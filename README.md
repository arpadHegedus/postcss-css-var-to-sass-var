# PostCSS CSS var to Sass var [<img src="https://postcss.github.io/postcss/logo.svg" alt="PostCSS Logo" width="90" height="90" align="right">](https://github.com/postcss/postcss)
[![NPM Version](https://img.shields.io/npm/v/postcss-css-var-to-sass-var.svg)](https://www.npmjs.com/package/postcss-css-var-to-sass-var)
[![Build Status](https://travis-ci.org/arpadHegedus/postcss-css-var-to-sass-var.svg?branch=master)](https://travis-ci.org/arpadHegedus/postcss-css-var-to-sass-var)
[![BGitter Chat](https://img.shields.io/badge/chat-gitter-blue.svg)](https://gitter.im/postcss/postcss)

A [PostCSS](https://github.com/postcss/postcss) plugin to convert CSS variables to Sass variables


## Installation

```
npm install postcss-css-var-to-sass-var
```

## Examples

```css
/* input */
:root {
  --color: black;
  --size: 15px;
}
div {
  --size: 20px;
  background: var(--color);
  font-size: var(--size);
}
p {
  font-size: var(--size);
}
```
```scss
/* output */
$color: black;
$size: 15px;
div {
  $size: 20px;
  background: $color;
  font-size: $size; // 20px
}
p {
  font-size: $size; // 15px
}
```

## Usage

### [Postcss JS API](https://github.com/postcss/postcss#js-api)

```js
postcss([require('postcss-css-var-to-sass-var')]).process(yourCSS);
```

### [Gulp](https://github.com/gulpjs/gulp)

```js
const gulp = require('gulp');
const postcss = require('gulp-postcss');
const varConvert = require('postcss-css-var-to-sass-var');
gulp.task('css', () => {
    gulp.src('path/to/dev/css')
        .pipe(postcss([
            varConvert()
        ]))
        .pipe(gulp.dest('path/to/build/css'));
});
```

## Tests

```
npm test
```

## License
This project is licensed under the [MIT License](./LICENSE).
