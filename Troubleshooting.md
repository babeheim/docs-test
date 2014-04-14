#### After upgrading, some icons don't show up
1. You don't have an old version of Font Awesome installed on your system (it has priority);
2. Both your `font-awesome.css` file and your `/fonts` (`/font` in 3.2.1) folder are up to date (if you are serving Font Awesome from your own server);
3. Your css link is up to date (if you are serving Font Awesome from a CDN) (Refers to [#1490](https://github.com/FortAwesome/Font-Awesome/issues/1490));
4. You are not using plugins that load an older/modified version of Font Awesome (Refers to [#1546]( https://github.com/FortAwesome/Font-Awesome/issues/1546));
5. You are using valid [HTML5](http://www.w3.org/TR/html5/introduction.html#a-quick-introduction-to-html) templates.

#### Are you/your customers using Adblock Plus?
If "Remove Social Media Buttons" option is enabled, you will miss some brand icons. Refers to [#1799]( https://github.com/FortAwesome/Font-Awesome/issues/1799)

#### Phonegap / Android (icons in Heading tags)
Icons doesn't show up in tags with `text-rendering: optimizeLegibility`. According to your Font Awesome version, please add to your stylesheets:
```css
/* FA 4.0.0 and newer */
.fa {
  text-rendering: auto;
}

/* FA 3.2.1 and older */
[class^="icon-"],
[class*=" icon-"]  {
  text-rendering: auto;
}
```

(more info on [#862](https://github.com/FortAwesome/Font-Awesome/pull/862))


#### font-variant (Small caps)
If you are using `font-variant: small-caps;`, according to your Font Awesome version, please add to your stylesheets:

```css
/* FA 4.0.0 and newer */
.fa {
  font-variant: normal;
}

/* FA 3.2.1 and older */
[class^="icon-"],
[class*=" icon-"] {
  font-variant: normal;
}
```

(more info on [#2171](https://github.com/FortAwesome/Font-Awesome/issues/2171))


#### Reveal.js
According to your Font Awesome version, please add to your stylesheets:

```css
/* FA 4.0.0 and newer */
.reveal .fa {
  font-family: 'FontAwesome';
}

/* FA 3.2.1 and older */
.reveal [class^="icon-"],
.reveal [class*=" icon-"]  {
  font-family: 'FontAwesome';
}
```

(more info on [#2131](https://github.com/FortAwesome/Font-Awesome/pull/2131))


### ie7-js
FontAwesome is not compatible with [ie7-js](https://code.google.com/p/ie7-js/).

(more info on [#2171](https://github.com/FortAwesome/Font-Awesome/issues/2821))


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