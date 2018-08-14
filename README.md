# Ian's RN Starter Template

This is my personal React Native starting template. So far my only additions are TypeScript and Prettier. Soon this will be a script.

## Init React Native

https://facebook.github.io/react-native/docs/getting-started.html

`react-native init SampleProject`

\*Note: React Native 0.56 is broken on windows machines. You must downgrade to 0.55.4.

## Add TypeScript

https://github.com/Microsoft/TypeScript-React-Native-Starter

```
yarn add --dev typescript
yarn add --dev react-native-typescript-transformer
yarn add --dev tslint
yarn tsc --init --pretty --jsx react
touch rn-cli.config.js
yarn add --dev @types/react @types/react-native
```

Uncomment `allowSyntheticDefaultImports: true` in `tsconfig.json`

Add the following to `rn-cli.js`:

```javascript
module.exports = {
  getTransformModulePath() {
    return require.resolve("react-native-typescript-transformer");
  },
  getSourceExts() {
    return ["ts", "tsx"];
  }
};
```

Rename `App.js` to `App.tsx`

## Add Prettier

```
yarn add --dev prettier
touch .prettierrc
```

Open VS Code workspace settings and add:

```
"editor.formatOnSave": true,
"javascript.format.enable": false
```

Update prettier rules:

```
{
    "semi": false,
    "singleQuote": true
}
```
