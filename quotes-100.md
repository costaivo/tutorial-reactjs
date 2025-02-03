# React Tutorials - Quotes App - 101 ---> Getting Started

## Creating the Project Structure

### Create react app using `vite`

[Vite](https://vitejs.dev/) is a modern build tool that provides a faster and leaner development experience for modern web projects. It leverages native ES modules and provides a lightning-fast development server with Hot Module Replacement (HMR).

### Using npm, pnpm, or yarn for building the project

You can use different package managers to create and manage your project. Here are the commands for each:

#### npm

``` bash
npm create vite@latest quotes-app --template react-ts
cd quotes-app
npm install
npm install bootstrap axios
```

**Advantage**: npm is the default package manager for Node.js and has a large ecosystem of packages.

#### pnpm

``` cmd
pnpm create vite@latest quotes-app --template react-ts
cd quotes-app
pnpm install
pnpm add bootstrap axios @types/bootstrap
```

**Advantage**: pnpm uses a unique symlink approach to save disk space and boost installation speed.

#### yarn

``` bash
yarn create vite@latest quotes-app --template react-ts
cd quotes-app
yarn
yarn add bootstrap axios
```

**Advantage**: yarn is known for its fast performance and reliability due to its efficient caching mechanism.

### Run the project

#### run using npm

``` bash
npm run dev
```

#### run using pnpm

``` bash
pnpm dev
```

#### run using yarn

``` bash
yarn dev
```

### Clean up the project

Clear the contents of the following files

- App.css
- index.css
- App.tsx
- main.tsx

### Modify code and test bootstrap installation

Open the `App.tsx` file

``` typescript
function App() {
  return (
    <div className="container mt-5">
      <button className="btn btn-primary">Hello World</button>
    </div>
  );
}

export default App;
```

- Open `main.tsx` file

``` typescript
import React from 'react';
import ReactDOM from 'react-dom/client';
import App from './App';
import 'bootstrap/dist/css/bootstrap.min.css';

ReactDOM.createRoot(document.getElementById('root')!).render(
  <React.StrictMode>
    <App />
  </React.StrictMode>
);
```

- Open `public\index.html`  file and replace its content with below code

``` html
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

- open `vite.config.ts` file and add the below code

``` typescript
import { defineConfig } from 'vite';
import react from '@vitejs/plugin-react';

export default defineConfig({
  plugins: [react()],
  server: {
    port: 3000,
    host: '0.0.0.0'
  }
});
```

---

### Run the application

start the react application and validate if the project is running properly on the default port 3000

``` cmd
   pnpm dev
```

---

## Setting  Dev Environment Right

Install the below extensions in VS Code to speed up your development time

- [Auto Import](https://marketplace.visualstudio.com/items?itemName=NuclleaR.vscode-extension-auto-import)
- [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [HTML Format](https://marketplace.visualstudio.com/items?itemName=mohd-akram.vscode-html-format)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

---

  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-101)
