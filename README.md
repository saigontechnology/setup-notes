# Setup Flow and ESlint for React Native Project

## Setup Flow
At root project folder, do below:
* Make sure the `.flowconfig` file is already in the project, open it and scroll to the bottom to see flow version.
For example:
````
[version]
^0.38.0
````
* Install flow by running `npm install --save-dev flow-bin@^0.38.0` (replace ^0.38.0 with version in your `.flowconfig` file).
* Open `package.json` file and add `"flow": "flow"` into "scripts"
For example:
````json
  "scripts":{
    "flow": "flow"
  }
````
* Open any `.js` file in the project which you want Flow to type check it, add `// @flow` anotation in the beginning of the file.
* Run `npm run flow`, Flow should be running now, and show some type check in the console.

## Setup ESlint
* Install eslint and plugins: 
`npm install --save-dev eslint babel-eslint eslint-config-standard eslint-plugin-import eslint-plugin-promise eslint-plugin-react eslint-plugin-standard`
* Create `.eslintrc.js` in project root folder with below content:
````js
module.exports = {
    "env": {
        "browser": true,
        "commonjs": true,
        "es6": true
    },
    "extends": [
        "eslint:recommended",
        "plugin:react/recommended",
        "plugin:import/errors",
        "plugin:import/warnings"
    ],
    "parserOptions": {
        "ecmaVersion": 6,
        "ecmaFeatures": {
            "experimentalObjectRestSpread": true,
            "jsx": true
        },
        "sourceType": "module"
    },
    "parser": "babel-eslint",
    "plugins": [
        "react",
        "import"
    ],
    "globals": {
        "__DEV__": false,
        "jest": false,
        "describe": false,
        "it": false,
        "expect": false
    },
    "rules": {
        "indent": [
            "error",
            4,
            {"SwitchCase": 1}
        ],
        "no-warning-comments": [
            "warn"
         ],
        "react/prop-types": [
            0
        ],
        "import/no-unresolved": [2, {commonjs: true, amd: true}],
        "import/named": [2],
        "import/namespace": [2],
        "import/default": [2],
        "import/export": [2]
    }
}

````
* Open `package.json` file and add `"eslint": "eslint src/**/*.js"` into "scripts"
For example
````json
  "scripts":{
    "flow": "flow",
    "eslint": "eslint src/**/*.js"
  }
````
* Run `npm run eslint`, eslint should be running now and show linting warnings/errors in the console.

## Setup for IDE
* Depend on your favourite IDE (Sublime, Nuclide, Visual Code), choose appropriate extensions, if above steps are finished, the extensions should be running after install successfully.
* For Nuclide, the extension is only linter-eslint and flow extension is already built-in.
