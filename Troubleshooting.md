#### Some icons don't show up
Check the following:

1. You don't have an old version of Font Awesome installed on your system (it may have priority) and you didn't restart your machine;
2. **If you are serving Font Awesome from your own server**: both `font-awesome.css` file and `/fonts` folders are up to date;
3. **If you are serving Font Awesome from a CDN**: Font Awesome's css link is up to date (ref: [#1490](https://github.com/FortAwesome/Font-Awesome/issues/1490));
4. You are not using plugins/extensions which are loading older/modified versions of Font Awesome (ref: [#1546]( https://github.com/FortAwesome/Font-Awesome/issues/1546));
5. You are using valid [HTML5](http://www.w3.org/TR/html5/introduction.html#a-quick-introduction-to-html) templates;
6. Your browser's development console shows that you are loading the proper font files;
7. Your browser's extensions are not blocking webfonts (noscript, adblockplus, etc.);
8. Your operating system is not blocking webfonts (Microsoft Group Policy).

#### I'm developing my web app locally (file://) and icons from CDN don't show up
Please check that you are not using [protocol relative urls](http://www.paulirish.com/2010/the-protocol-relative-url/). In that case, you should add `https:` in front of the CDN link.

#### I'm hosting fonts on my server and icons don't show up
Check the following:

1. You properly configured server's [MIME types](https://github.com/EnlightenAgency/Server-Setup-MIME-Types-Headers/blob/master/font-mimetypes.txt);
2. You properly configured [Cross-origin Resource Sharing (CORS)](https://github.com/FortAwesome/Font-Awesome/issues/4675#issuecomment-58192275);
3. **For Internet Explorer**: you don't serve files with `no-store` option in Cache-control header (Ref: [#6454](https://github.com/FortAwesome/Font-Awesome/issues/6454));
4. **For Internet Explorer and HTTPS**: you don't serve files with `no-cache` option in Pragma header.

#### Some brand icons are missing
You (or your costumers) are probably using Adblock Plus. If the "Remove Social Media Buttons" option is enabled, you will miss some brand icons.

Ref: [#1799]( https://github.com/FortAwesome/Font-Awesome/issues/1799) for more information.

#### Internet Explorer Compatibility Mode
This feature will cause some random issues with IE, so please disable it by adding the meta tag as the **FIRST** tag in your `<head>`:
```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

Refs: [#4144](https://github.com/FortAwesome/Font-Awesome/issues/4144) and [stackoverflow](https://stackoverflow.com/questions/27913012/font-awesome-4-2-0-not-rendering-in-ie11-with-compatibility-mode-turned-on/28490514#28490514)

#### Internet Explorer 8 caveats
If you are using IE8, it's necessary to add the html5.js script like:
```css
<!--[if lt IE 9]>
  <script src="http://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.2/html5shiv.min.js"></script>
<![endif]-->
```
Note that you may still have random issues with this browser.

Refs: [#954](https://github.com/FortAwesome/Font-Awesome/issues/954), workaround available at [#954-comment](https://github.com/FortAwesome/Font-Awesome/issues/954#issuecomment-65414146)

#### Need a blank/empty icon?
Icons do not have the same width by design choice, so a blank icon is pretty useless. You should use `fa-fw` if you need a placeholder. If you perform database validation, allow the blank value.

Please take a look at this fiddle: http://jsfiddle.net/tagliala/7z9b557v/

Ref: [#1606](https://github.com/FortAwesome/Font-Awesome/issues/1606)

#### Reveal.js
According to your Font Awesome version, please add this to your stylesheets:

```css
.reveal .fa {
  font-family: 'FontAwesome';
  font-style: normal;
}
```

Ref: [#2131](https://github.com/FortAwesome/Font-Awesome/pull/2131)

### ie7-js
FontAwesome is not compatible with [ie7-js](https://code.google.com/p/ie7-js/).

(more info on [#2171](https://github.com/FortAwesome/Font-Awesome/issues/2821))

#### Stack icons inside Wordpress posts

Wordpress automatically adds a `<br>` tag at the end of the line and this will break icon stacks. Please put your html in one line or add this to your stylesheet:

```css
.fa-stack br { display: none }
```
(more info on [#4212](https://github.com/FortAwesome/Font-Awesome/issues/4212))

#### Get TTF/OTF fonts working in IE9+

While [some browsers](http://caniuse.com/ttf) support the TTF/OTF formats as webfonts, Internet Explorer generates an error unless the font is set to Installable Embedding mode. This behavior is reproduced when neither `.woff` nor `.eot` variants are served to IE.

This can be remedied by setting the ``fsType`` flag in the font file to ``0000``, representing Installable Embedding mode, using one of the following utilities:

##### Using the ttembed-js npm module
```
npm install -g ttembed-js
ttembed-js path/to/fontawesome-webfont.ttf
ttembed-js path/to/FontAwesome.otf
```
or, within node.js:
```js
var callback = function(error, oldFsType) {
    if (error) {
        console.error('Something went wrong.', error);
        return;
    }
    if (oldFsType === '0000') {
        console.log('fsType is already 0000; no action taken.');
    } else {
        console.log('fsType successfully changed from ' + oldFsType + ' to 0000.');
    }
}
var ttembed = require('ttembed-js');
ttembed({filename: './path/to/fontawesome-webfont.ttf'}, callback);
ttembed({filename: './path/to/FontAwesome.otf'}, callback);
```

##### Using the original ttembed
```
git clone https://github.com/hisdeedsaredust/ttembed.git
cd ttembed
make
./ttembed path/to/fontawesome-webfont.ttf path/to/FontAwesome.otf
```

Ref: [#2517](https://github.com/FortAwesome/Font-Awesome/issues/2517)

#### Adobe Flash Builder

Just include this in your css:
```
@font-face {
	fontFamily: 			FontAwesome;
	embed-as-cff:			true;
	src: 					url("/assets/font/font-awesome-4.0.3/fonts/FontAwesome.otf");
	fontStyle: 				normal;
}
@font-face {
	fontFamily: 			FontAwesomeNonCff;
	embed-as-cff:			false;
	src: 					url("/assets/font/font-awesome-4.0.3/fonts/FontAwesome.otf");
	fontStyle: 				normal;
}
```
And add the contents of FontAwesome in your assets folder (or somewhere else).

Then use this syntax to show icons as a label:
```
<s:Label id="icon" text="&#xf011;" color="#000000" fontFamily="FontAwesome"/>
```
Use the link http://fontawesome.io/cheatsheet/ to find the right code for your icon (or write a function to nick-name it).

Ref: [#1154](https://github.com/FortAwesome/Font-Awesome/issues/1154#issuecomment-41045407)

#### Fonts not showing up in Phonegap application (iOs)
In Xcode select the main project file in the sidebar (at the top, blue icon) and for each item under "TARGETS" go to the "Info" tab.

Under there you should find a "Fonts provided by application" key. If it's not there it needs to be added by control-clicking (or "right-clicking") any of the existing keys and selecting "Add row". In the drop down find "Fonts provided by application" and use that. It should have the "Array" type by default, if it does not, add it.

Expand the key by clicking the arrow to the left of it.

Under you should at least see an "Item 0" key. If it doesn't have a value, double-click its "value" field and enter the name of your first font.

For every additional font you can click the "+" button next to any of the items (visible when the item is selected) to add a new row.

You also need to be sure that the font files are in your project's "Resources" folder. I believe support is limited to .otf and .ttf.

#### Fonts not showing up in Phonegap application (Android and Windows Phone)

https://github.com/FortAwesome/Font-Awesome/issues/3632#issuecomment-72075216

Try to remove all occurrences of `?v=4.2.0` from the `@font-face` property in the `font-awesome.css` file.

#### .fa-ul problem

If a general css specified `list-style-image` that this image is superimposed on the marker. I propose to add to the definition `.fa-ul` property `list-style-image: none`.

#### Fonts not rendering properly running Windows 10
Windows 10 can be configured via its registry to block untrusted fonts.

Ref: [Turn on and use the Blocking Untrusted Fonts feature](https://technet.microsoft.com/en-us/library/dn985836%28v=vs.85%29.aspx#Turn_on_and_use_the_Blocking_untrusted_fonts_feature)