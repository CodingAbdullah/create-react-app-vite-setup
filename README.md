# React, TypeScript, and Vite Setup

This template provides a minimal setup to get React working with Vite with HMR and some ESLint rules.

Note that <code>create-react-app</code> is now deprecated and so you will need to use a framework or another setup in order to effectively use React.js as a client UI library. 

This setup allows you to work with React.js using Vite.

## Setup Command
To set this up on your own in a separate directory, dependencies can be installed and updated using a specified command for working with React.js and Typescript. 

The following command will create a directory named <code>my-react-app</code>. It will contain a template for working with React.js and Typescript:

<code>npm create vite@latest my-react-app -- --template react-ts</code>

Ensure you install all the required dependencies using <code>npm install</code> in the root of this project.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react/README.md) uses [Babel](https://babeljs.io/) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type aware lint rules:

- Configure the top-level `parserOptions` property like this:

```js
export default tseslint.config({
  languageOptions: {
    // other options...
    parserOptions: {
      project: ['./tsconfig.node.json', './tsconfig.app.json'],
      tsconfigRootDir: import.meta.dirname,
    },
  },
})
```

- Replace `tseslint.configs.recommended` to `tseslint.configs.recommendedTypeChecked` or `tseslint.configs.strictTypeChecked`
- Optionally add `...tseslint.configs.stylisticTypeChecked`
- Install [eslint-plugin-react](https://github.com/jsx-eslint/eslint-plugin-react) and update the config:

```js
// eslint.config.js
import react from 'eslint-plugin-react'

export default tseslint.config({
  // Set the react version
  settings: { react: { version: '18.3' } },
  plugins: {
    // Add the react plugin
    react,
  },
  rules: {
    // other rules...
    // Enable its recommended rules
    ...react.configs.recommended.rules,
    ...react.configs['jsx-runtime'].rules,
  },
})
```
