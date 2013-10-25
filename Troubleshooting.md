#### Some icons don't show up
1. You don't have an old version of Font Awesome installed on your system (it has priority);
2. Both your `font-awesome.css` file and your `/font`/`/fonts` folder are up to date (if you are serving Font Awesome from your own server);
3. Your css link is up to date (if you are serving Font Awesome from a CDN) (Refers to [#1490](https://github.com/FortAwesome/Font-Awesome/issues/1490));
4. You are not using plugins that load an older/modified version of Font Awesome (Refers to [1546]( https://github.com/FortAwesome/Font-Awesome/issues/1546));
5. You are using valid [HTML5](http://www.w3.org/TR/html5/introduction.html#a-quick-introduction-to-html) templates.


#### Phonegap / Android (icons in Heading tags)
Icons doesn't show up in tags with `text-rendering: optimizeLegibility`. This is the fix:
```css
[class^="icon-"],
[class*=" icon-"]  {
  text-rendering: auto;
}
```

(more info on [#862](https://github.com/FortAwesome/Font-Awesome/pull/862))


#### Small caps
If you are using `font-variant: small-caps;` in your project, please add:
```css
[class^="icon-"],
[class*=" icon-"]  {
  font-variant: normal;
}
```

(more info on [#2171](https://github.com/FortAwesome/Font-Awesome/issues/2171))


#### Reveal.js
If you are using FontAwesome < 4.0.0, add the following style:

```css
.reveal [class^="icon-"],
.reveal [class*=" icon-"]  {
  font-family: 'FontAwesome';
}
```

If you are using FontAwesome >= 4.0.0, add the following style:
```css
.reveal .fa-icon {
  font-family: 'FontAwesome';
}
```

(more info on [#2131](https://github.com/FortAwesome/Font-Awesome/pull/2131))