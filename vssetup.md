# visual code setup

###### Created 22 April 2020, Updated 1 May 2020

I got this from other sources: Alex Gog's article [How to properly setup Nuxt with ESLint and Prettier](https://medium.com/@gogl.alex/how-to-properly-set-up-eslint-with-prettier-for-vue-or-nuxt-in-vscode-e42532099a9c)

The official Nuxt guide has setup notes for EsLint and Prettier: [Nuxt EsLint and Prettier](https://nuxtjs.org/guide/development-tools/#eslint-and-prettier)

**Note that the following needs to run after all the installations: `npm run lint -- --fix`**

## Install

In the project root:

```javascript
npm install eslint babel-eslint eslint-config-prettier eslint-plugin-prettier eslint-plugin-vue eslint-loader prettier -D
```

In workspace settings:

```javascript
{
  "editor.formatOnSave": true,
  "vetur.validation.template": false,
  "editor.codeActionsOnSave": {
    "source.fixAll.eslint": true
  }
}
```

Note that to avoid the end of line errors, the `.prettierrc` file must have `"endOfLine": "auto"` added:

```javascript
{
  "semi": false,
  "arrowParens": "always",
  "singleQuote": true,
  "endOfLine": "auto"
}
```

In `.eslintrc.js` file in the root directory:

```javascript
module.exports = {
  root: true,
  env: {
    node: true,
    browser: true,
  },
  extends: [
    'plugin:vue/recommended',
    'eslint:recommended',
    'prettier/vue',
    'plugin:prettier/recommended',
  ],
  rules: {
    'vue/component-name-in-template-casing': ['error', 'PascalCase'],
    'no-console': process.env.NODE_ENV === 'production' ? 'error' : 'off',
    'no-debugger': process.env.NODE_ENV === 'production' ? 'error' : 'off',
  },
  globals: {
    $nuxt: true,
  },
  parserOptions: {
    parser: 'babel-eslint',
  },
};
```
