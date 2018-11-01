# Ian's RN Starter Template

My personal reference for starting a new React Native project from scratch. Open source to share a little insight about what I've learned putting it together.

Includes instructions for both the `react-native-cli` and `expo-cli`. Each have distinct pros and cons that I'll highlight in their respective sections.

## Expo CLI

https://docs.expo.io/versions/latest/workflow/expo-cli

Using the expo-cli is the best choice for beginners or those who don't want to touch native iOS/Android code. Expo boasts tons of great features, but some of those come at cost. You can read more at:

https://docs.expo.io/versions/v30.0.0/introduction/why-not-expo

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

## React Native CLI

https://facebook.github.io/react-native/docs/getting-started.html

This allows you to make React Native actually _Native_. Initialized a project with this cli will give you full Android Studio and Xcode projects that you can edit by hand. This allows you to do all kinds of cool stuff, but also adds extra complexity.

### Init Project

`yarn global add react-native-cli`

`react-native init SampleProject`

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

## Prettier

https://github.com/prettier/prettier

Prettier is a godsend for people like me that can't stand unformatted code. Combined with VS Code it can fix your ugly code every time you hit save.

### Add Prettier

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
