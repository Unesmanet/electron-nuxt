# {{ name }}

> {{ description }}

#### Build Setup

``` bash
# install dependencies
yarn

# serve app with hot reload
yarn dev

# build electron application for production
yarn build

{{#or unit e2e}}
# yarn tests
yarn test

{{/or}}

{{#if eslint}}
# lint all JS/Vue component files in `src/`
yarn lint

{{/if}}
```

---

This project was generated with [electron-nuxt](https://github.com/Unesmanet/electron-nuxt) v{{templateVersion}} based in [michalzaq12 template](https://github.com/michalzaq12/electron-nuxt) using [vue-cli](https://github.com/vuejs/vue-cli). Documentation about the original structure can be found [here](https://github.com/michalzaq12/electron-nuxt/blob/master/README.md).
