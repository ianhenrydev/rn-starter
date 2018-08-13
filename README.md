# Ian's RN Starter Template

`react-native init SampleProject`

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