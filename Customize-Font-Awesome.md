Font Awesome receives dozens of new requests every day. Some of them will eventually be included, others will not. [Popularity](https://fontawesome.com/community/leaderboard/new) is one of the factors taken into account, but it is not the only one.

So, if you need a new icon in a short while, or you need a comprehensive set of icons (e.g., a set of weather icons to build a forecast application) our suggestion is to customize Font Awesome.

## The Easy Way

There are some wonderful online services which allows you to customize Font Awesome, like:

- **Fort Awesome**: https://fortawesome.com/ (by **@davegandy**, creator of Font Awesome)
- Fontello: http://fontello.com/
- IcoMoon: https://icomoon.io/app/#/select ([How To](https://dyscribe.com/en/webdesign/create-your-own-custom-iconfont.html))
- Fontastic: http://fontastic.me/

Pick up the one which better fits your needs.

### SVG Framework

⚠️ SVG customization is on the To-Do list, meanwhile please use this approach

Prerequisites:
1. [Webpack](https://webpack.js.org/)
2. Single-path SVG

*Instructions are different for TypeScript*

JavaScript:
```js
import { library, dom } from '@fortawesome/fontawesome-svg-core'

// replace 'M241 241 H 351 V 351 H 241 L 241 241' with your single-path SVG
var faMyCustomIcon = {
  prefix: 'fac',
  iconName: 'my-custom-icon',
  icon: [512, 512, [], 'e001', 'M241 241 H 351 V 351 H 241 L 241 241']
}

library.add(
  faMyCustomIcon
)

dom.watch()
```

HTML:
```html
<span class="fac fa-my-custom-icon"></span>
```

Docs: https://fontawesome.com/how-to-use/with-the-api/setup/getting-started

Ref: [#13079](https://github.com/FortAwesome/Font-Awesome/issues/13079)

Blog Post on this approach - https://medium.com/@nsisodiya/hacking-font-awesome-for-custom-svg-icons-ea762118fa7b

## The Hard Way

⚠️ Outdated information. Please wait for the main repository to reflect FA5 changes

*Note that you may need commercial software*

1. [Fork](https://github.com/FortAwesome/Font-Awesome/fork) the repository. You need a [properly configured development environment](https://github.com/FortAwesome/Font-Awesome#hacking-on-font-awesome)
2. Hack with the `.otf` file. Here it is a guide you can follow: [The making of Octicons](https://github.com/blog/1135-the-making-of-octicons)
3. Share your fork with the Font Awesome community. Check for [open issues](https://github.com/FortAwesome/Font-Awesome/issues) that are related to your fork and share your repository

# New styles

If you don't need new icons but have special needs for your stylesheet, please consider a custom build based on `.less` or `.scss` versions.