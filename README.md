```
yarn add react-native-reanimated react-native-splash-screen react-native-gesture-handler react-hook-form @react-navigation/bottom-tabs @react-navigation/native @react-navigation/native-stack react-native-orientation-locker react-native-safe-area-context react-native-screens react-native-vector-icons @react-native-async-storage/async-storage react-native-svg
```

```
yarn add -D babel-plugin-module-resolver eslint-plugin-import eslint-plugin-react eslint-plugin-react-hooks prettier eslint react-native-dotenv @typescript-eslint/eslint-plugin @typescript-eslint/parser eslint-plugin-react eslint-plugin-react-hooks @types/react-native-vector-icons
```

### EsLint config

```json
{
  "root": true,
  "extends": ["@react-native-community", "prettier"],
  "plugins": ["react", "react-hooks", "import"],
  "overrides": [
    {
      "files": ["*.ts", "*.tsx", "*.js", "*.jsx"],
      "rules": {
        "no-param-reassign": 0,
        "import/order": [
          "error",
          {
            "groups": ["builtin", "external", "internal", "sibling"],
            "pathGroups": [
              {
                "pattern": "react",
                "group": "builtin",
                "position": "before"
              },
              {
                "pattern": "src/**",
                "group": "external",
                "position": "after"
              }
            ],
            "pathGroupsExcludedImportTypes": ["react"],
            "newlines-between": "always",
            "alphabetize": {
              "order": "asc",
              "caseInsensitive": true
            }
          }
        ],
        "sort-imports": [
          "error",
          {
            "ignoreDeclarationSort": true
          }
        ],
        "import/no-default-export": 0,
        "react-native/no-unused-styles": 0,
        "react-native/no-inline-styles": 2,
        "react-native/no-color-literals": 2,
        "import/prefer-default-export": 0
      }
    }
  ],
  "rules": {
    "global-require": 0,
    "no-param-reassign": [
      2,
      {"props": true, "ignorePropertyModificationsForRegex": ["^acc"]}
    ],
    "react-hooks/rules-of-hooks": 1,
    "react-hooks/exhaustive-deps": 0,
    "react/function-component-definition": [
      1,
      {"namedComponents": "function-declaration"}
    ],
    "@typescript-eslint/no-unused-vars": "error",
    "import/prefer-default-export": 1
  }
}
```

### Prettier config

```json
{
  "arrowParens": "avoid",
  "bracketSameLine": true,
  "bracketSpacing": false,
  "singleQuote": true,
  "trailingComma": "all",
}
```

### TS config

```js
{
  <...>,
  "compilerOptions": {
    "baseUrl": ".",
    "paths" : {
      "src/*": ["src/*"]
    },
    /* Completeness */
    "skipLibCheck": true
  }
}
```

### react-native.config.js

```js
module.exports = {
  ...,
  assets: ['./assets/fonts/'],
};
```

### babel.config.js

```js
module.exports = {
  presets: [
    'module:metro-react-native-babel-preset',
    '@babel/preset-typescript',
  ],
  plugins: [
    [
      'module-resolver',
      {
        alias: {
          src: './src',
        },
      },
    ],
    [
      'module:react-native-dotenv',
      {
        envName: 'APP_ENV',
        moduleName: '@env',
        path: '.env',
        safe: false,
        allowUndefined: true,
        verbose: false,
      },
    ],
    'react-native-reanimated/plugin',
  ],
};
```

### package.json

```
{
  "scripts": {
    ...,
    "link-asset": "npx react-native-asset"
  }
}
```

### Create src folder and replace App.tsx

```jsx
import {AppRegistry} from 'react-native';

import {AppWithProviders} from 'src/app-with-providers';

import {name as appName} from './app.json';

AppRegistry.registerComponent(appName, () => AppWithProviders);
```

### [Setup splash](https://github.com/crazycodeboy/react-native-splash-screen#third-stepplugin-configuration)
### [Setup orientation-locker](https://github.com/wonday/react-native-orientation-locker#configuration)
### [Delete console logs in production](https://reactnative.dev/docs/performance#using-consolelog-statements)
### [react-native-flipper-performance-monitor setup](https://github.com/bamlab/react-native-flipper-performance-monitor#install-for-non-expo-projects)
