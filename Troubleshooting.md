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