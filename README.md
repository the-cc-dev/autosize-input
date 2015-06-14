# autosize-input.js [![npm Version](http://img.shields.io/npm/v/autosize-input.svg?style=flat)](https://www.npmjs.org/package/autosize-input) [![Build Status](https://img.shields.io/travis/yuanqing/autosize-input.svg?branch=master&style=flat)](https://travis-ci.org/yuanqing/autosize-input)

> Effortless, dynamic-width `input` elements in vanilla JavaScript.

## Features

- Dynamically adjusts the width of the text `input` element to fit its current contents
- Can be initialised to fit the element&rsquo;s `placeholder` attribute
- Optionally set a `min-width` based on the element&rsquo;s initial content
- Super lightweight; just 1.0 KB [minified](autosize-input.min.js), or 0.6 KB minified and gzipped

## Usage

> [**Editable demo**](http://jsfiddle.net/5u4o001z/)

```html
<body>
  <input type="text" id="foo" value="Nice">
  <input type="text" id="bar" placeholder="People">
  <input type="text" id="baz" placeholder="Matter">
  <script src="../autosize-input.min.js"></script>
  <script>
    autosizeInput(document.querySelector('#foo'));
    autosizeInput(document.querySelector('#bar'));
    autosizeInput(document.querySelector('#baz'), { minWidth: true });
  </script>
</body>
```

## Implementation details

The [`box-sizing`](https://developer.mozilla.org/en-US/docs/Web/CSS/box-sizing) property of the given `input` element is set, inline, to `content-box`.

Under the hood, `autosize-input` uses a hidden &ldquo;ghost&rdquo; `div` (with the same `font-size` and `font-family` as the original `input` element) to determine the correct width to assign to the `input` element.

## API

In the browser, `autosizeInput` is a global variable. In Node, do:

```js
var autosizeInput = require('autosize-input');
```

### autosizeInput(elem [, opts])

`elem` is a text `input` element, and `opts` is an object literal.

If we do not want the text box to &ldquo;contract&rdquo; as the user starts to type, set `opts.minWidth` to `true`. This will give the `elem` a `min-width` that fits it initial contents (ie. either the element&rsquo;s intial `value`, or its `placeholder`).

See [Usage](#usage).

## Installation

Install via [npm](https://npmjs.com):

```
$ npm i --save autosize-input
```

Install via [bower](http://bower.io):

```
$ bower i --save yuanqing/autosize-input
```

## Prior art

- [jQuery.Autosize.Input](https://github.com/MartinF/jQuery.Autosize.Input)
- [React-Input-Autosize](https://github.com/JedWatson/react-input-autosize)

This module was written because I needed a standalone, lightweight solution to this rather common UI problem.

## License

[MIT](LICENSE)