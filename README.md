# JavaScript Style Guide

The previous version is available at [old](https://github.com/mercadolibre/javascript-style-guide/tree/old).

# ES5 

The rules for linting JavaScript es5 are based on those from [AirBnB (for the deprecated version es5)](https://github.com/airbnb/javascript/tree/es5-deprecated/es5). From there, we’ve made some modifications to add our own custom set of rules, which are listed below.

Our final [`.eslintrc`](https://github.com/mercadolibre/javascript-style-guide/blob/master/es5/.eslintrc) reflect this.

## Table of Contents

  1. [Indent](#indent)
  1. [Line max length](#line-max-length)
  1. [Function names](#function-names)
  1. [Parameters reassignment](#parameters-reassignment)

## Indent
 
 - We use an indentation of 4 spaces, instead of 2 as AirBnB.

**[⬆ back to top](#table-of-contents)**

## Line max length

 - The limit for each line of code is set at 120 characters. It will produce an error if the limit is surpassed.

**[⬆ back to top](#table-of-contents)**

## Function names

 - We have disabled the [`func-names`](http://eslint.org/docs/rules/func-names) rule from AirBnB.
 - We **allow** anonymous functions.

**[⬆ back to top](#table-of-contents)**

## Parameters reassignment

 - We have disabled the [`no-param-reassign`](http://eslint.org/docs/rules/no-param-reassign) rule from AirBnB.
 - We **allow** the reassignment of parameters.

**[⬆ back to top](#table-of-contents)**

## Contribute

### References

 - [Release notes](https://github.com/mercadolibre/javascript-style-guide/releases)
 - [Issue tracker](https://github.com/mercadolibre/javascript-style-guide/issues)
 - Contributors: Leandro Linares, Cristian Escudero, Hernán Colmeiro, Guillermo Paz, [and all these people](https://github.com/mercadolibre/javascript-style-guide/graphs/contributors).



