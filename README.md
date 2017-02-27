# Vue Date Range Picker Component

[![npm version][npm-v-img]][npm-url]
[![npm download][npm-dl-img]][npm-url]

> Intellectual property of [Oneway.mobi](http://www.oneway.mobi/)

#### Notice
This component is not meant to meet all the business requirements  
so diving into `src/` to make it fits your needs is highly recommended

#### Example
See [here](https://kenberkeley.github.io/vue-daterangepicker-component/example.html), source in [`example.html`](./example.html)
> Suggest inspecting it with [devtools](https://github.com/vuejs/vue-devtools)

#### Requirement
* Vue 1.x
* Vue Router 0.7.x
* [vue-update-query-mixin](https://github.com/kenberkeley/vue-update-query-mixin)
* Moment.js (available globally)
* jQuery + BootStrap 3.x (available globally)
* [`bootstrap-daterangepicker`](http://www.daterangepicker.com/)

#### Installation
`npm i vue-daterangepicker-component -S`

> alternatively: `<script src="dist/vue-daterangepicker-component.min.js"></script>`  
> which exposes **`VueDateRangePicker`** as a global variable

#### Usage
```
<date-range-picker :config></date-range-picker>

props: {
  // more options see http://www.daterangepicker.com/#options
  config: { type: Object, default: () => ({}) }
}
```

#### Build

`npm run build`

#### LICENSE

MIT

[npm-url]: https://www.npmjs.com/package/vue-daterangepicker-component
[npm-v-img]: http://img.shields.io/npm/v/vue-daterangepicker-component.svg
[npm-dl-img]: http://img.shields.io/npm/dm/vue-daterangepicker-component.svg
