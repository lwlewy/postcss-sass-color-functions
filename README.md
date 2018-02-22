[PostCSS](https://github.com/postcss/postcss) plugin to transform SASS/compass color functions to more compatible CSS.

>This fork is using a [forked version](https://github.com/ivansky/color) of [color](https://github.com/Qix-/color) to replicate correctly SASS's lighten function ([color/#91](https://github.com/Qix-/color/issues/91), [color/#92](https://github.com/Qix-/color/issues/92)). There is still a negligible difference in the result compared to SASS due to rounding.

Inspired, and modified from, [postcss-color-function](https://github.com/postcss/postcss-color-function).

## Installation

```console
$ npm install git://github.com/lwlewy/postcss-sass-color-functions.git
```

## Usage

```js
// dependencies
var fs = require("fs")
var postcss = require("postcss")
var sassColorFunctions = require("postcss-sass-color-functions")

// css to be processed
var css = fs.readFileSync("input.css", "utf8")

// process css
var output = postcss()
  .use(sassColorFunctions())
  .process(css)
  .css
```

Using this `input.css`:

```css
body {
  background-color: mix(#255073, #3c749e, 25%);
}

```

you will get:

```css
body {
  background-color: rgb(54, 107, 147);
}
```

Checkout [tests.js](tests.js) for examples.


### Currently Supported functions

 - `mix(one, two, weight)`
 - `rgba(color, alpha)`
 - `darken(color, amount)`
 - `lighten(color, amount)`
 - `tint(color, amount)`
 - `shade(color, amount)`
