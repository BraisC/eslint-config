# Eslint and Prettier Custom Config

![](https://img.shields.io/npm/v/@braisc/eslint-config?logo=npm&style=flat-square)
![](https://img.shields.io/npm/dependency-version/@braisc/eslint-config/peer/eslint?style=flat-square)
![](https://img.shields.io/bundlephobia/min/@braisc/eslint-config?label=size&logo=npm&style=flat-square)
![](https://img.shields.io/npm/dw/@braisc/eslint-config?logo=npm&style=flat-square)
![](https://img.shields.io/github/last-commit/braisc/eslint-config?logo=github&style=flat-square)

These are my settings for ESLint and Prettier with some minor modifications over the ones from [Wes Bos](https://github.com/wesbos/eslint-config-wesbos)

## Installing (in your project folder)

1. You need a `package.json` file, so run this command if you dont have it:

```
npm init
```

2. Install everything needed for it to run:

```
npx install-peerdeps --dev @braisc/eslint-config
```

3. Create an `.eslintrc.json` file in the root of your project's directory with this content:

```json
{
  "extends": ["@braisc"]
}
```

4. Create a `.babelrc.json` file in the root of your project's directory with this two presets, the second one only if you are using React:

```json
{
  "presets": ["@babel/preset-env", "@babel/preset-react"]
}
```

5. You can add two scripts to your `package.json` to lint and/or fix:

```json
"scripts": {
  "lint": "eslint .",
  "lint:fix": "eslint . --fix"
},
```

6. Now you can manually lint your code by running `npm run lint` and fix all fixable issues with `npm run lint:fix`. You probably want your editor to do this though.

## With VS Code

You need eslint installed globally to make it work nice with VSCode

```
npm install --global eslint
```

1. Install the [ESLint package](https://marketplace.visualstudio.com/items?itemName=dbaeumer.vscode-eslint)
2. Now we need to setup some VS Code settings via `Code/File` → `Preferences` → `Settings`. It's easier to enter these settings while editing the `settings.json` file, so click the `{}` icon in the top right corner:

```js
  // These are all my auto-save configs
"editor.formatOnSave": true,
// turn it off for JS/JSX/TS, we will do this via eslint
"[javascript]": {
  "editor.formatOnSave": false
},
"[javascriptreact]": {
  "editor.formatOnSave": false
},
"[typescript]": {
  "editor.formatOnSave": false
},
// tell VSCode to autofix also TypeScript and html
"eslint.validate": [
  "javascript",
  "javascriptreact",
  "typescript",
  "typescriptreact",
  "html"
],
// tess ESlint to fix on filesave
"editor.codeActionsOnSave": {
  "source.fixAll.eslint": true
},
// Optional BUT IMPORTANT: If you have the prettier extension enabled for other languages like CSS and HTML, turn it off for JS/JSX/TS since we are doing it through Eslint already
"prettier.disableLanguages": ["javascript", "typescript", "javascriptreact"],
```
