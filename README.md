# PostCSS HTML Syntax

[![NPM license](https://img.shields.io/npm/l/postcss-html.svg)](https://www.npmjs.com/package/postcss-html)
[![NPM version](https://img.shields.io/npm/v/postcss-html/next.svg?style=flat-square)](https://www.npmjs.com/package/postcss-html/v/next)
[![NPM downloads](https://img.shields.io/npm/dw/postcss-html.svg)](http://www.npmtrends.com/postcss-html)
[![NPM downloads](https://img.shields.io/npm/dm/postcss-html.svg)](http://www.npmtrends.com/postcss-html)
[![NPM downloads](https://img.shields.io/npm/dy/postcss-html.svg)](http://www.npmtrends.com/postcss-html)
[![Build Status](https://github.com/ota-meshi/postcss-html/workflows/CI/badge.svg?branch=master)](https://github.com/ota-meshi/postcss-html/actions?query=workflow%3ACI)

<img align="right" width="95" height="95"
 title="Philosopher’s stone, logo of PostCSS"
 src="http://postcss.github.io/postcss/logo.svg">

[PostCSS](https://github.com/postcss/postcss) syntax for parsing HTML (and HTML-like)

- [PHP](http://php.net)
- [Vue Single-File Component](https://vue-loader.vuejs.org/spec.html)
- [Quick App](https://doc.quickapp.cn/framework/source-file.html)
- [XSLT](https://www.w3.org/TR/xslt-30/)

## Getting Started

First thing's first, install the module:

```bash
npm install postcss-html@next --save-dev
```

If you want support SCSS/SASS/LESS/SugarSS syntax, you need to install the corresponding module.

- SCSS: [postcss-scss](https://github.com/postcss/postcss-scss)
- SASS: [postcss-sass](https://github.com/aleshaoleg/postcss-sass)
- LESS: [postcss-less](https://github.com/shellscape/postcss-less)
- SugarSS: [sugarss](https://github.com/postcss/sugarss)

## Use Cases

```js
const postcss = require('postcss');
const syntax = require('postcss-html')({
    // syntax for parse scss (non-required options)
    scss: require('postcss-scss'),
    // syntax for parse less (non-required options)
    less: require('postcss-less'),
    // syntax for parse css blocks (non-required options)
    css: require('postcss-safe-parser'),
});
postcss(plugins).process(source, { syntax: syntax }).then(function (result) {
    // An alias for the result.css property. Use it with syntaxes that generate non-CSS output.
    result.content
});
```

If you want support SCSS/SASS/LESS/SugarSS syntax, you need to install these module:

- SCSS: [postcss-scss](https://github.com/postcss/postcss-scss)
- SASS: [postcss-sass](https://github.com/aleshaoleg/postcss-sass)
- LESS: [postcss-less](https://github.com/shellscape/postcss-less)
- SugarSS: [sugarss](https://github.com/postcss/sugarss)

## Advanced Use Cases

### Options

```js
const options = {
    rules: [
        {
            // custom language for file extension
            test: /\.postcss$/i,
            lang: 'scss'
        },
        {
            // custom language for file extension
            test: /\.customcss$/i,
            lang: 'custom'
        },
    ],

    // custom parser for CSS (using `postcss-safe-parser`)
    css: 'postcss-safe-parser',
    // custom parser for SASS (PostCSS-compatible syntax.)
    sass: require('postcss-sass'),
    // custom parser for SCSS (by module name)
    scss: 'postcss-scss',
    // custom parser for LESS (by module path)
    less: require.resolve('./node_modules/postcss-less'),
    // custom parser for SugarSS
    sugarss: require('sugarss'),
    // custom parser for custom language
    custom: require('postcss-custom-syntax'),
}
const syntax = require('postcss-html')(options);
```

## Turning PostCSS off from within your HTML

PostCSS can be temporarily turned off by using special comments in your HTML. For example:

```html
<html>
<body>
<!-- postcss-disable -->
<a style="color: red;"></a>
<!-- postcss-enable -->
```

## Linting with Stylelint

The main use case of this plugin is to apply linting with [Stylelint] to `<style>` tags and `<div style="*">` property in HTML (and HTML-like).

[Stylelint]: https://stylelint.io/
