![Color Claim](http://www.vanschneider.com/wp-content/uploads/2016/02/cc_title_vector.svg)  

[![Latest version](https://img.shields.io/npm/v/color-claim-sass.svg)](https://www.npmjs.com/package/color-claim-sass) [![Build Status](https://travis-ci.org/jeroenptrs/color-claim-sass.svg?branch=master)](https://travis-ci.org/jeroenptrs/color-claim-sass) [![Dependency Status](https://www.versioneye.com/user/projects/59411a306725bd0030ec5006/badge.svg?style=flat-square)](https://www.versioneye.com/user/projects/59411a306725bd0030ec5006)

color-claim-sass is a Sass color library, with a set of accompanying functions, classes and mixins.
They are based on Tobias van Schneider's Color Claim. See all the color swatches over at http://www.vanschneider.com/colors/

## Installation
### NPM
`npm install --save color-claim-sass` installs color-claim-sass. Copy the scss or css files to your assets. 
Alternatively, use `@import "path/to/node_modules/color-claim-sass/color-claim";` in your Sass project.

### CDN
Download the latest version through via [RawGit](https://cdn.rawgit.com/jeroenptrs/color-claim-sass/archive/v1.1.0.zip).

Import all CSS classes in your website using `<link rel="stylesheet" href="https://cdn.rawgit.com/jeroenptrs/color-claim-sass/1d7af7f2/css/color-claim.min.css">`

## Usage
### Function
```sass
color-claim($color, $claim[, $percentage])
```
`$color` selects the corresponding Color Claim swatch and accepts a number from 1 to 102.
`$claim` accepts "bg", "text" or "mix" as value. This respectfully returns the background and text Color Claim colors that are stored in `$color-claim`, or mixes them together.

If you mix the colors together, you can add an extra parameter `$percentage` to set the weight of the mix.
This percentage is 50% by default, i.e. "bg" and "text" have equal weight in the mix.
Setting percentage to 0% equals to `color-claim($color)`, 100% equals to `color-claim($color, "text")`.

You should use this if you want to set something else than `background-color` or `color`.
In case of setting `background-color` and/or `color` to their respective Color Claim values, use the mixin instead.

### Mixin
```sass
@include color-claim($color[, $claim])
```
This mixin sets your element's background and/or text colors to the corresponding Color Claim values.
`$color` selects the corresponding Color Claim swatch.

Not passing a value for `$claim` automatically sets both, passing "bg" or "text" as value respectfully only sets `background-color` and `color`.

Passing "inv" as a value sets the inverse: `background-color` to the corresponding "text" color and `color` to the "bg" color.

### Classes
```sass
.color-claim-#{$color}
.color-claim-bg-#{$color}
.color-claim-text-#{$color}
.color-claim-inv-#{$color}
```
You can use the following classes if you really need to use it as a class (f.e. in HTML, jQuery, ...). In any other cases - like the ones addressed above - just use the mixin or the function. 

`$color` can be any Color Claim swatch (1-102). 
Use `.color-claim-#{$color}` to set both the `background-color` and `color` attributes.

`.color-claim-bg-#{$color}` only sets `background-color` attribute,
`.color-claim-text-#{$color}` only sets `color`.

If you want to set the inverse: 
`.color-claim-inv-#{$color}` sets background-color attribute to the color value (and vice versa). 

### Silent Classes
```sass
$_silent: true
```
You can also set all classes as silent, so they won't compile to your css.
Before importing color-claim-sass in your project, create a variable `$_silent` and set it to `true`.

All classes will still be available in Sass, just use `@extend %color-claim[-bg/-text/-inv]-#{$color}`.

<a href="https://www.buymeacoffee.com/6QmhM2xDG" target="_blank"><img src="https://www.buymeacoffee.com/assets/img/custom_images/black_img.png" alt="Buy Me A Coffee" style="height: auto !important;width: auto !important;" ></a>
