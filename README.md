# Ian's RN Starter Template

This is my personal React Native starting template. So far my only additions are TypeScript and Prettier. Soon this will be a script.

## React Native CLI

### Init Project

`yarn global add react-native-cli`

https://facebook.github.io/react-native/docs/getting-started.html

`react-native init SampleProject`

\*Note: React Native 0.56 is broken on windows machines. You must downgrade to 0.55.4.

### Add TypeScript

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

## Expo CLI

### Init Project

`yarn global add expo-cli`

`expo init sample-expo`

### Add Typescript

`yarn add --dev typescript tslint react-native-typescript-transformer react-native-scripts-ts`

`yarn add --dev @types/react @types/react-native`

replace scripts with:

```
"scripts": {
    "start": "react-native-scripts-ts start",
    "eject": "react-native-scripts-ts eject",
    "android": "react-native-scripts-ts android",
    "ios": "react-native-scripts-ts ios"
  },
```

replace main with: `"main": "./node_modules/react-native-scripts-ts/build/bin/crna-entry.js"`

add tsconfig:

```
{
  "compilerOptions": {
    "target": "es5",
    "module": "es2015",
    "outDir": "build/dist",
    "sourceMap": true,
    "experimentalDecorators": true,
    "jsx": "react-native",
    "lib": ["dom", "es2015", "es2016"],
    "allowSyntheticDefaultImports": true,
    "moduleResolution": "node",
    "noEmitHelpers": true,
    "importHelpers": true,
    "strict": true,
    "noImplicitReturns": true
  }
}
```

add packager info to app.json :

```
"packagerOpts": {
  "sourceExts": ["ts", "tsx"],
  "transformer": "node_modules/react-native-typescript-transformer/index.js"
},
```

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
  "printWidth": 160,
  "semi": false,
  "singleQuote": true
}
```
