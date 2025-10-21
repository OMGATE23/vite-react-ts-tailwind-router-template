# React + TypeScript + Vite Template

A modern, production-ready React template with TypeScript, TailwindCSS, and React Router DOM. This template provides a scalable foundation for building single-page applications with file-based routing support through the `/pages` folder structure.

## App Structure

This template implements a clean, organized architecture that supports:

- **File-based routing** through the `/pages` folder for easy navigation management
- **TypeScript** for type safety and better developer experience
- **TailwindCSS** for utility-first styling with Vite integration
- **React Router DOM** for client-side routing and navigation
- **ESLint** configuration for code quality and consistency

## File Structure

```
vite-react-ts-tailwind-router-template/
├── public/
│   └── vite.svg                 # Vite logo asset
├── src/
│   ├── assets/
│   │   └── react.svg           # React logo asset
│   ├── pages/
│   │   └── home/
│   │       └── index.tsx       # Home page component
│   ├── App.tsx                 # Main app component with router setup
│   ├── App.css                 # App-specific styles
│   ├── index.css               # Global styles with TailwindCSS import
│   └── main.tsx                # Application entry point
├── eslint.config.js            # ESLint configuration
├── index.html                  # HTML template
├── package.json                # Dependencies and scripts
├── tsconfig.json               # TypeScript configuration
├── tsconfig.app.json           # App-specific TypeScript config
├── tsconfig.node.json          # Node-specific TypeScript config
└── vite.config.ts              # Vite configuration with TailwindCSS plugin
```

The template uses a pages-based routing system where each folder in `/src/pages` represents a route, making it easy to add new pages and maintain a clear project structure.

Currently, two official plugins are available:

- [@vitejs/plugin-react](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react) uses [Babel](https://babeljs.io/) (or [oxc](https://oxc.rs) when used in [rolldown-vite](https://vite.dev/guide/rolldown)) for Fast Refresh
- [@vitejs/plugin-react-swc](https://github.com/vitejs/vite-plugin-react/blob/main/packages/plugin-react-swc) uses [SWC](https://swc.rs/) for Fast Refresh

## React Compiler

The React Compiler is not enabled on this template because of its impact on dev & build performances. To add it, see [this documentation](https://react.dev/learn/react-compiler/installation).

## Expanding the ESLint configuration

If you are developing a production application, we recommend updating the configuration to enable type-aware lint rules:

```js
export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // Other configs...

      // Remove tseslint.configs.recommended and replace with this
      tseslint.configs.recommendedTypeChecked,
      // Alternatively, use this for stricter rules
      tseslint.configs.strictTypeChecked,
      // Optionally, add this for stylistic rules
      tseslint.configs.stylisticTypeChecked,

      // Other configs...
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```

You can also install [eslint-plugin-react-x](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-x) and [eslint-plugin-react-dom](https://github.com/Rel1cx/eslint-react/tree/main/packages/plugins/eslint-plugin-react-dom) for React-specific lint rules:

```js
// eslint.config.js
import reactX from "eslint-plugin-react-x";
import reactDom from "eslint-plugin-react-dom";

export default defineConfig([
  globalIgnores(["dist"]),
  {
    files: ["**/*.{ts,tsx}"],
    extends: [
      // Other configs...
      // Enable lint rules for React
      reactX.configs["recommended-typescript"],
      // Enable lint rules for React DOM
      reactDom.configs.recommended,
    ],
    languageOptions: {
      parserOptions: {
        project: ["./tsconfig.node.json", "./tsconfig.app.json"],
        tsconfigRootDir: import.meta.dirname,
      },
      // other options...
    },
  },
]);
```
