# MoneyTransApp

> A Vue.js project


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


## Main Components:

- The app is basically a bunch of `page-components` found in `src/`
- Each page-component contains its HTML template, JS code (VueJS), and CSS (optional)
- `App.vue`: main component, wraps other components and passes props to them (child-components)
    - Sub-components: ConfirmationPage, InfoPage, MainPage, SummaryPage (names are self explanatory)

### Steps:

**MainPage :house: :**
- **Click** on Login with Facebook image (_just an image, no real OAuth_)
- **Select** dest. currency
- **Enter** either
    - The amount you want to send (AUD) OR
    - The amount to be received

**InfoPage :information_source: :**
- **View** calculation in details

**ConfirmationPage:**
- **Choose** method (bank/cash)
- **Enter** recipient's details
- **Send**

**SummaryPage:**
- **View** summary of transaction
