# vue-test5
***
## 概要
1. vue-cliでインストール（regular）
```
vue create projectName
vue add quasar 
```
2. ファイル名変更：quasar-user-options.js　→　quasar-user-options.ts
3. styleの指定変更：quasar.scss, quasar.variables.scss   
`quasar.scss`の修正
```javascript:
@import './quasar.variables.scss';
// @import '~quasar-styl';
// @import '~quasar-addon-styl';
```
`quasar.variables.scss`の修正
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

`main.ts`の修正
```javascript:main.ts
import { createApp } from "vue";
import App from "./App.vue";
import "./registerServiceWorker";
import router from "./router";
import store from "./store";
import { Quasar } from "quasar";
import quasarUserOptions from "./quasar-user-options";
import "quasar/dist/quasar.sass";

createApp(App)
  .use(Quasar, quasarUserOptions)
  .use(store)
  .use(router)
  .mount("#app");

```
5. storybookのinstall  
* webPack5を選択
* eslintのエラー修正
```
npx storybook@latest init
```
***

6. storybookでquasar使用可能にする
* .storybook/preview.ts の修正
```
import type { Preview } from "@storybook/vue3";
import "@quasar/extras/mdi-v7/mdi-v7.css";
import "quasar/dist/quasar.css";
import { setup } from "@storybook/vue3";
import { Quasar } from "quasar";

setup((app) => {
  app.use(Quasar, {});
});

import "@quasar/extras/material-icons/material-icons.css";
import '@quasar/extras/roboto-font/roboto-font.css'

const preview: Preview = {
  parameters: {
    actions: { argTypesRegex: "^on[A-Z].*" },
    controls: {
      matchers: {
        color: /(background|color)$/i,
        date: /Date$/,
      },
    },
  },
};

export default preview;

```
7. StoryBookでactionを使用可能にする
```typescript
// addonのインストール
$ yarn add -D @storybook/addon-actions

// .storybook/main.tsの編集
import { StorybookConfig } from "@storybook/vue3-vite";

const config: StorybookConfig = {
  framework: "@storybook/vue3-vite",
  stories: ["../src/**/*.stories.@(js|ts)"],
  addons: ["@storybook/addon-controls", "@storybook/addon-actions"], // 追加
};

export default config;

// Storybook における action は、コンポーネントに対するイベントハンドラーで、argTypes に定義することで、
// Action タブにイベントのログを表示します。アクション名は onXXX という命名にすることで、
// 自動的に XXX に対応するイベントのハンドラとして定義されます。

// src/stories/MyHeader.stories.ts
argTypes: {
  onLogin: { action: "onLogin" },
  onLogout: { action: "onLogout" },
  onSignUp: { action: "onSignUp" },
},


```

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
