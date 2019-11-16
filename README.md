# Eslint and Prettier Custom Config
These are my settings for ESLint and Prettier with some minor modifications over the ones from [Wes Bos](https://github.com/wesbos/eslint-config-wesbos) (like adding TypeScript support)

## Installing (in your project folder)

1. You need a package.json file.

2. Install everything needed for it to run:

```
npx install-peerdeps --dev eslint-config-brais
```

3. Create a `.eslintrc` file in the root of your project's directory with this content:

```json
{
  "extends": ["brais"]
}
```

4. You can add two scripts to your package.json to lint and/or fix:

```json
"scripts": {
  "lint": "eslint .",
  "lint:fix": "eslint . --fix"
},
```

5. Now you can manually lint your code by running `npm run lint` and fix all fixable issues with `npm run lint:fix`. You probably want your editor to do this though.


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
  // tell VSCode to autofix also TypeScript
  "eslint.validate": [
    "javascript",
    "javascriptreact",
    { "language": "typescript", "autoFix": true },
    { "language": "typescriptreact", "autoFix": true }
  ],
  // tell the ESLint plugin to run on save
  "eslint.autoFixOnSave": true,
  // Optional BUT IMPORTANT: If you have the prettier extension enabled for other languages like CSS and HTML, turn it off for JS/JSX/TS since we are doing it through Eslint already
  "prettier.disableLanguages": ["javascript", "typescript", "javascriptreact"],
  ```
