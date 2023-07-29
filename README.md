# vue-test5
***
## 概要
1. vue-cliでインストール（reqular）
```
vue create projectName
vue add quasar 
```
2. ファイル名変更：quasar-user-options.js　→　quasar-user-options.ts
3. styleの指定変更：quasar.scss, quasar.variables.scss
```javascript:
@import './quasar.variables.scss';
// @import '~quasar-styl';
// @import '~quasar-addon-styl';
```

```ts:
// It's highly recommended to change the default colors
// to match your app's branding.

$primary   : #027BE3;
$secondary : #26A69A;
$accent    : #9C27B0;

$dark      : #1D1D1D;

$positive  : #21BA45;
$negative  : #C10015;
$info      : #31CCEC;
$warning   : #F2C037;

// @import '~quasar-variables-styl'
```
4. storybookのinstall  
* webPack5を選択
* eslintのエラー修正
```
npx storybook@latest init
```
***

## Project setup
```
yarn install
```

### Compiles and hot-reloads for development
```
yarn serve
```

### Compiles and minifies for production
```
yarn build
```

### Run your unit tests
```
yarn test:unit
```

### Lints and fixes files
```
yarn lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
