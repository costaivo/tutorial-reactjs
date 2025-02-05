# React Tutorials - Quotes App - 100 ---> Getting Started

## Introduction

This tutorial series will guide you through building a Quotes Application using React with TypeScript. We'll use modern development tools and best practices to create a responsive, user-friendly application.

## Creating the Project Structure

### Create react app using `vite`

[Vite](https://vitejs.dev/) is a modern build tool that provides a faster and leaner development experience for modern web projects. It leverages native ES modules and provides a lightning-fast development server with Hot Module Replacement (HMR).

#### Why Vite?

- **Speed**: Vite is significantly faster than Create React App (CRA)
- **Modern Architecture**: Uses native ES modules for better performance
- **Optimized Build**: Produces highly optimized production builds
- **TypeScript Support**: Built-in TypeScript support without additional configuration
- **Hot Module Replacement**: Instant feedback during development

### Using npm, pnpm, or yarn for building the project

You can use different package managers to create and manage your project. Choose the one that best fits your needs:

#### npm

```bash
npm create vite@latest quotes-app --template react-ts
cd quotes-app
npm install
npm install bootstrap 
```

**Advantage**: npm is the default package manager for Node.js and has a large ecosystem of packages.
**Best for**: Beginners and teams that want maximum compatibility

#### pnpm

```cmd
pnpm create vite@latest quotes-app --template react-ts
cd quotes-app
pnpm install
pnpm add bootstrap  @types/bootstrap
```

**Advantage**: pnpm uses a unique symlink approach to save disk space and boost installation speed.
**Best for**: Large projects and teams concerned about disk space efficiency

#### yarn

```bash
yarn create vite@latest quotes-app --template react-ts
cd quotes-app
yarn
yarn add bootstrap 
```

**Advantage**: yarn is known for its fast performance and reliability due to its efficient caching mechanism.
**Best for**: Teams that need deterministic installations and enhanced security

### Project Dependencies Explained

- **bootstrap**: UI framework for responsive design
- **@types/bootstrap**: TypeScript type definitions for Bootstrap
- **react-ts template**: Includes TypeScript configuration and React setup

### Run the project

Choose the command based on your package manager:

#### run using npm

```bash
npm run dev
```

#### run using pnpm

```bash
pnpm dev
```

#### run using yarn

```bash
yarn dev
```

After running these commands, your application will be available at `http://localhost:3000`

### Clean up the project

To start with a clean slate, we'll remove the default boilerplate code:

Clear the contents of the following files:

- `App.css`: Remove default styles. Empty the contents of the file.
- `index.css`: Remove default styles. Empty the contents of the file.
- `App.tsx`: Remove demo content. Empty the contents of the file
- `main.tsx`: add the import statement to include bootstrap at the end of existing imports

  ```tsx
  import 'bootstrap/dist/css/bootstrap.min.css';
  ```

### Modify code and test bootstrap installation

#### Open the `App.tsx` file

```typescript
function App() {
  return (
    <div className="container mt-5">
      <button className="btn btn-primary">Hello World</button>
    </div>
  );
}

export default App;
```

This simple component tests that both React and Bootstrap are working correctly.

#### The `main.tsx` file

The contents of  `main.tsx` file should like the one shown below.

```typescript
import { StrictMode } from 'react'
import { createRoot } from 'react-dom/client'
import './index.css'
import App from './App.tsx'
import 'bootstrap/dist/css/bootstrap.min.css';

createRoot(document.getElementById('root')!).render(
  <StrictMode>
    <App />
  </StrictMode>,
);
```

The main file imports Bootstrap CSS and sets up the React application root.

#### Open `public\index.html` file

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <link rel="icon" type="image/svg+xml" href="/quotes.png" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>Quotes App</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
```

This HTML file serves as the application shell and includes necessary meta tags for responsive design.

#### Configure Vite - `vite.config.ts`

Change the port to run on 3000 instead of the default port.

```typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000,
    host: '0.0.0.0'  // Allows access from other devices on the network
  }
});
```

This configuration sets up Vite with React plugin and configures the development server.

### Verify Installation

Start the application and check for:

1. The application runs without errors
2. You see a blue "Hello World" button (confirms Bootstrap is working)
3. The button is centered on the page (confirms container class is working)

```cmd
pnpm dev
```

## Setting Dev Environment Right

To enhance your development experience, install these recommended VS Code extensions:

- [Auto Import](https://marketplace.visualstudio.com/items?itemName=NuclleaR.vscode-extension-auto-import)
  - Automatically finds, parses and provides code actions for all available imports
  - Speeds up development by reducing manual import typing

- [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
  - Provides shortcuts for common React patterns
  - Includes TypeScript snippets

- [HTML Format](https://marketplace.visualstudio.com/items?itemName=mohd-akram.vscode-html-format)
  - Formats HTML code for better readability
  - Supports JSX/TSX formatting

- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)
  - Ensures consistent code formatting
  - Can be configured to format on save

### Recommended VS Code Settings

Create or update `.vscode/settings.json` in your project:

```json
{
  "editor.formatOnSave": true,
  "editor.defaultFormatter": "esbenp.prettier-vscode",
  "editor.tabSize": 2,
  "files.eol": "\n"
}
```

---

[Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-101)
