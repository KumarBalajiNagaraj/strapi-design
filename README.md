<p align="center">
  <a href="https://strapi.io">
    <img src="./assets/logo.svg" width="318px" alt="Strapi logo" />
  </a>
</p>
<p align="center">
<a style='margin-right:10px' href="https://design-system.strapi.io/">Documentation</a>|<a style='margin-left:10px' href="https://design-system-git-main-strapijs.vercel.app/">Try components</a></p>
<br />

<p align="center">
  <a href="https://www.npmjs.org/package/@strapi/design-system">
    <img src="https://img.shields.io/npm/v/@strapi/design-system/latest.svg" alt="NPM Version" />
  </a>
    <img alt="Bundle Size" src="https://badgen.net/bundlephobia/minzip/@strapi/design-system"/>
  <a href="https://github.com/strapi/design-system/actions/workflows/playwright-ci.yml">
    <img src="https://github.com/strapi/design-system/actions/workflows/playwright-ci.yml/badge.svg" alt="Playwright tests" />
  </a>
  <a href="https://discord.strapi.io">
    <img src="https://img.shields.io/discord/811989166782021633?label=Discord" alt="Strapi on Discord" />
  </a>
</p>

# Welcome! 👋👋👋

Strapi Design System provides guidelines and tools to help anyone make Strapi's contributions more cohesive and to build
plugins more efficiently.

## Installation

Install Strapi Design System and its peer dependencies:

```sh
$ yarn add react react-dom @strapi/design-system @strapi/icons styled-components react-router-dom

# or

$ npm i react react-dom @strapi/design-system @strapi/icons styled-components react-router-dom
```

## Usage

Wrap your application with the `ThemeProvider` and pass the default `lightTheme` provided by `@strapi/design-system`.

```jsx
import { ThemeProvider, lightTheme } from '@strapi/design-system';

function App({ children }) {
  return <ThemeProvider theme={lightTheme}>{children}</ThemeProvider>;
}

export default App;
```

## Testing a specific branch

Make sure to have the project already cloned (see previous point). Then, run the following commands:

```sh
# Inside the folder
$ git checkout BRANCH_NAME # BRANCH_NAME concerns the modifications to tests
$ yarn setup # reinstall dependencies & prepare lerna packages
```

If you encounter problems doing so, run the following command and retry the previous one:

```sh
$ git reset --hard
```

## Linking the design system

If you want to analyze the admin bundle and the impact each library has on the over all application, link this repo to your copy of the strapi monorepo or your own strapi application or plugin

### Application or Plugin

First, run `yarn build` in `strapi-design-system/packages/strapi-design-system` to generate the bundle.

You can link the design system using either a [relative path](#relative-path) or [yarn link](#yarn-link).

### Strapi monorepo

To link the design system to the Strapi monorepo follow the steps outlined in the [contributor documentation](https://contributor.strapi.io/core/admin/link-strapi-design-system)

### Relative path

Replace the version number with the relative path to your copy of the design system:

```
"@strapi/design-system": "link:../../../../strapi-design-system/packages/strapi-design-system"
```

### Yarn link

[`yarn link`](https://classic.yarnpkg.com/lang/en/docs/cli/link/) allows you to link the design system without any changes to the `package.json`. First run `yarn link` in `strapi-design-system/packages/design-system` and then `yarn link @strapi/design-system` in your Strapi project.

### Development

Once the link is setup, reinstall dependencies before rebuilding the admin and starting the server

```
yarn install -f && yarn build && yarn develop
```
