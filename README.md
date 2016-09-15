# moneytransapp

> A Vue.js project

**Main Components:**

- The app is basically a bunch of `page-components` found in `src/`
- Each file component contains HTML temlate, JS code (VueJS), and CSS (optional)
- `App.vue`: main component, wraps other components and passes props to them (child-components)
    + Each component expects some props that it receives from its parent   
- ConfirmationPage, InfoPage, MainPage, SummaryPage (names are self explanatory)

## Build Setup

``` bash
# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# build for production with minification
npm run build
```

For detailed explanation on how things work, consult the [docs for vue-loader](http://vuejs.github.io/vue-loader).
