#### Some icons don't show up
Check the following:

1. You don't have an old version of Font Awesome installed on your system (it may have priority);
2. If you are serving Font Awesome from your own server: both your `font-awesome.css` file and your `/fonts` folders are up to date;
3. If you are serving Font Awesome from a CDN: Your css link is up to date (Refers to [#1490](https://github.com/FortAwesome/Font-Awesome/issues/1490));
4. You are not using plugins/extensions loading older/modified versions of Font Awesome (Refers to [#1546]( https://github.com/FortAwesome/Font-Awesome/issues/1546));
5. You are using valid [HTML5](http://www.w3.org/TR/html5/introduction.html#a-quick-introduction-to-html) templates.

#### I'm hosting fonts on my server and icons don't show up
Please check server's [MIME types](https://github.com/EnlightenAgency/Server-Setup-MIME-Types-Headers/blob/master/font-mimetypes.txt)

#### Are you/your customers using Adblock Plus?
If "Remove Social Media Buttons" option is enabled, you will miss some brand icons. Refer to [#1799]( https://github.com/FortAwesome/Font-Awesome/issues/1799) for more information.

#### Internet Explorer compatibility mode
This feature will cause some random issues with IE, so please disable it by adding to your `head`:
```html
<meta http-equiv="X-UA-Compatible" content="IE=edge">
```

(more info on [#4144](https://github.com/FortAwesome/Font-Awesome/issues/4144))

#### Internet Explorer 8 caveats
If you are using IE8, it's necessary to add the html5.js script like:
```css
<!--[if lt IE 9]>
  <script src="http://cdnjs.cloudflare.com/ajax/libs/html5shiv/3.7.2/html5shiv.min.js"></script>
<![endif]-->
```
Note that you may still have random issues with this browser.

(more info on [#954](https://github.com/FortAwesome/Font-Awesome/issues/954))

#### Need a blank/empty icon?
By design, icons have not the same width, so a blank icon is pretty useless. You should use `fa-fw` if you need a placeholder. If you also need to validate a database, allow the blank value.

Please take a look at this fiddle: http://jsfiddle.net/tagliala/7z9b557v/

(more info on [#1606](https://github.com/FortAwesome/Font-Awesome/issues/1606))

#### Reveal.js
According to your Font Awesome version, please add to your stylesheets:

```css
.reveal .fa {
  font-family: 'FontAwesome';
  font-style: normal;
}
```

(more info on [#2131](https://github.com/FortAwesome/Font-Awesome/pull/2131))

### ie7-js
FontAwesome is not compatible with [ie7-js](https://code.google.com/p/ie7-js/).

(more info on [#2171](https://github.com/FortAwesome/Font-Awesome/issues/2821))

#### Stack icons inside Wordpress posts

Wordpress automatically adds a `<br>` tag at the end of the line and this will break icon stacks. Please put your html in one line or add to your stylesheet:

```css
.fa-stack br { display: none }
```
(more info on [#4212](https://github.com/FortAwesome/Font-Awesome/issues/4212))

#### Get TTF/OTF fonts working in IE9+

While [some browsers](http://caniuse.com/ttf) support the TTF/OTF formats as webfonts, Internet Explorer generates an error unless the font is set to Installable Embedding mode. This behavior is reproduced when neither `.woff` nor `.eot` variants are served to IE.

(more info on [#2517](https://github.com/FortAwesome/Font-Awesome/issues/2517))

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