# Postcss-position-alt

<img align="right" width="135" height="95"
  title="Philosopher’s stone, logo of PostCSS"
  src="http://postcss.github.io/postcss/logo-leftp.png">

[![NPM version][npm-image]][npm-url] [![Build Status][ci-img]][ci] [![Dependency Status][daviddm-image]][daviddm-url]

[![npm](https://nodei.co/npm/postcss-position-alt.svg?)](https://nodei.co/npm/postcss-position-alt/)

[PostCSS] plugin that adds shorthand to position declarations.

[PostCSS]: https://github.com/postcss/postcss
[ci-img]:  https://travis-ci.org/sylvainbaronnet/postcss-position-alt.svg
[ci]:      https://travis-ci.org/sylvainbaronnet/postcss-position-alt
[npm-url]: https://www.npmjs.com/package/postcss-position-alt
[npm-image]: https://badge.fury.io/js/postcss-position.svg
[daviddm-image]: https://david-dm.org/sylvainbaronnet/postcss-position-alt.svg
[daviddm-url]: https://david-dm.org/sylvainbaronnet/postcss-position-alt



```css

/* Input example */
.alpha {
  absolute: top left;
}
.beta {
  absolute: bottom 10px right z-index 1;
}
.gamma {
  fixed: top left 10px;
}
.delta {
  fixed: bottom auto left 10%;
}
.epsilon {
  fixed: top left bottom right z-index 9999;
}
.zeta {
  relative: top var(--some-var) left initial bottom revert;
}
```

```css
/* Output example */
.alpha {
  position: absolute;
  top: 0;
  left: 0;
}
.beta {
  position: absolute;
  bottom: 10px;
  right: 0;
  z-index: 1;
}
.gamma {
  position: fixed;
  top: 0;
  left: 10px;
}
.delta {
  position: fixed;
  bottom: auto;
  left: 10%;
}
.epsilon {
  position: fixed;
  top: 0;
  left: 0;
  bottom: 0;
  right: 0;
  z-index: 9999;
}
.zeta {
  position: relative;
  top: var(--some-var);
  left: initial;
  bottom: revert;
}
```

It's also possible to use directly position without position type : 

```css

/* Input example */
.toto {
  top: 10px left z-index 100;
}
.titi {
  right: left 10px z-index bottom 1px;
}
```

```css
/* Output example */
.toto {
  top: 10px;
  left: 0;
  z-index: 100;
}
.titi {
  right: 0;
  left: 10px;
  bottom: 1px;
  z-index: 0;
}
```

It support those properties aliases :

```css
.aliases {
  absolute t 1px l 2px b 3px r 4px z 5 /* or zi */
}

/* Output */
.aliases {
  position: absolute;
  top: 1px;
  left: 2px;
  bottom: 3px;
  right: 4px;
  z-index: 5;
}
```

It works with [postcss-center](https://github.com/jedmao/postcss-center) :

```css
.center {
  absolute left center top center
}

```

postcss-center must be applied _after_ postcss-position-alt


## Usage

```js
postcss([ require('postcss-position-alt') ])
```

See [PostCSS] docs for examples for your environment.


## Alternative 

*See [postcss-position](https://github.com/seaneking/postcss-position) for an alternative shorthand syntax.*