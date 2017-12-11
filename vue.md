# Happy Path to Developing Vue Apps

## Tooling

We’ve agreed on using the following toolstack:

* [`yarn`](https://yarnpkg.com/en/docs) for JavaScript package management
* [`webpack`](https://webpack.js.org/concepts/)
* [`babel`](https://babeljs.io/) for transpiling
  [ES2015](https://babeljs.io/learn-es2015/)
* [`eslint`](https://eslint.org/docs/user-guide/)
* [`node-sass` with `sassc`/`libsass`](http://sass-lang.com/libsass)

## Syntax

* 2 spaces indentation
  - for JavaScript, HTML, CSS/SCSS
  - also for indentation of attributes in Vue components
* use spaces inside `import { stuff } from 'module'`
* use single quotes for strings `'`
* prefer `Promise`s over `async`/`await` (we are more familiar with `Promise`)
* use SCSS style (not SASS)

### import ordering

* (roughly) from unspecific to most specific:
  - 3rd party libs (lodash, object-path, qs)
  - Vue, Vue plugins
  - own modules/components
* each group in ascending alphabetical order

## Vue

Parts we use:

* [`Vue` 2.4 or 2.5](https://vuejs.org/v2/guide/)
* [`Vuex`](https://vuex.vuejs.org/en/)
  - use modules for the store, if the app is big enough
  - no need for mutation types as constants
* [`vue-i18n`](http://kazupon.github.io/vue-i18n/en/)
* [`vue-router`](https://router.vuejs.org/en/)
* [`axios`](https://github.com/axios/axios)

No need to use `nuxt`, as we do not use SSR.

## Vue style guide

All the rules in the [Vue style guide](https://vuejs.org/v2/style-guide/) apply.

Some rules are further narrowed down by us:

* do not use `<style scoped>`
  - prefer class names prefixed with the component name
* prefer single component files
* component file names are `CamelCase.vue`, other files are `kebab-case.js`
* component tag names are cased consistently throughout the same app
  - prefer `<PascalCase/>`, but `<kebab-case/>` is fine as well in single
    component files
* attributes should span multiple lines
  - indent with 2 spaces
* always use the shorthand syntax for `v-bind`/`v-on`: `:` and `@`
* adhere to this order in `.vue` files: `<template>` --> `<script>` -->
  `<style>`
* prefer Vuex for global state

## Reusable components

* as Vue plugin
* provide a `package.json` for use with `yarn`
* provide documentation
  - how to use the component
  - properties, events
  - optional dependencies
* inject data via prop
* bubble up via events
* API calls return `Promise`s

## Component libraries

Currenty we choose between Element and Bootstrap-Vue.

### Bootstrap

https://bootstrap-vue.js.org/

`bootstrap-vue` (1.2)

* layout, styling, ... is better then Element’s
* BootstrapVue comes without dependency on jQuery
* try being agnostic to bootstrap "goodies" (like `<b-form-checkbox/>`
  behaviour for Array references in `v-model`) or at least document the
  commitment to specific component behaviours

### Element

http://element.eleme.io/#/en-US

`element-ui` (1.4)

* best used when working on components only, i.e. you do not need a full
  framework
* or if embedded in a 3rd party site (i.e. not used in an SPA)
* multilang/localization out of box with components
* only import the components you need

## Translations

Use [`vue-i18n`](https://kazupon.github.io/vue-i18n/en/).

Translation strings are static configuration, so no need to put them in the
store.

Structure translated data like `vue-i18n`:

    {
      en: {
        key: {
          subkey: translation
        }
      }
    }

## Documentation

* document the intention of methods if they are not trivial or the name itself
  is not telling enough
* document like
  https://github.com/vuejs/vuejs.org/blob/master/src/v2/api/index.md
