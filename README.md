# Prettier-Linting-Husky-Setup-Guide

This readme File will be a step-by-step setup guide for ESLint with Pettier and Husky for Typescript React

# Step 1 Setting Up ESLint

1. Open the terminal in vscode and cd into the folder of your react-app
   `cd my-app`
2. Enter the below command in ther termianal to initalize eslint
   `npm init @eslint/config`
   `
   When asked How would you like to use ESLint Select

- To chek syntax and find problems
  ![HowWouldYouliketoSetupESLlint](my-app/SetupPhotos/How_would_you_like_to_use_ESLint.png)
  Next Select "JavaScript modules (import/export)"
  When asked What type of modules does your project use?
  You can select "CommonJS" if you are creating a node project.
  ![WhatTypeofmodulesDoesyourProjectUse](my-app/SetupPhotos/WhatTypeofmodulesDoesyourProjectUse.png)

For The following prompt Select React
![SelectReact](my-app/SetupPhotos/SelectReact.png)
For the rest of the questions pick the answers show in the photo below
![WhatTypeofmodulesDoesyourProjectUse](my-app/SetupPhotos/Final.png)

# Setting up Airbnb styleGudie for Eslinting

1. Setup regular Airbnb config
   `npm info "eslint-config-airbnb@latest" peerDependencies`

   `npx install-peerdeps --dev eslint-config-airbnb`
2. Install dependencies (and peer dependencies)
   `npm install eslint-config-airbnb-typescript \
            @typescript-eslint/eslint-plugin@^5.13.0 \
            @typescript-eslint/parser@^5.0.0 \
            --save-dev`
3. Configure ESLlint, Within your ESLint config file(.eslintrc.json):
   eslint-config-airbnb/hooks for react
   `{
    "env": {
        "browser": true,
        "es2021": true,
        "jest":true
    },
    "extends": [
        "react-app",
        "react-app/jest",
        "airbnb",
        "airbnb-typescript",
        "airbnb/hooks",
        "plugin:import/typescript"
    ],
    "overrides": [
    ],
    "parser": "@typescript-eslint/parser",
    "parserOptions": {
        "ecmaVersion": "latest",
        "sourceType": "module",
        "project": "./tsconfig.json"
    },
    "plugins": [
        "react",
        "@typescript-eslint"
    ],
    "rules": {
    }
}
`
4. With in your package.json 
`
scripts": {
    "start": "react-scripts start",
    "build": "react-scripts build",
    "test": "react-scripts test",
    "eject": "react-scripts eject",
    "lint": "eslint .",
    "lint:fix": "eslint --fix ."
  },
`


# Acknowledges

This setup uses the Airbnb code style guide
This setup guide follows and documments the steps of setting ESLint with Pettier and Husky for Typescript React from Youtuber CoderOne's video [ESLint with VSCode, Prettier, Husky and React For Beginners](https://www.youtube.com/watch?v=ZXW6Jn6or1w)
