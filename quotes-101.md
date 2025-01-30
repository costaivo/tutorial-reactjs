# React Tutorials - Quotes App - 101 ---> Getting Started

## Creating the Project Structure

### Create react app using `vite`

 ``` cmd
npm create vite@latest quotes-app --template react-ts
cd quotes-app
npm install
npm install bootstrap axios
 ```

**or**

``` cmd
pnpm create vite@latest quotes-app --template react-ts
cd quotes-app
pnpm install
pnpm add bootstrap axios @types/bootstrap
```

**or**

``` bash
yarn create vite quotes-app --template react-ts
cd quotes-app
yarn
yarn add bootstrap axios
```

### Run the project

``` bash
npm run dev
  ```

**or**

  ``` basg
pnpm dev
```

**or**

``` bash
yarn dev
```

### Clean up

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

### Run the application

start the react application and validate if the project is running properly on the default port 3000

``` cmd
   pnpm dev
```

## Setting  Dev Environment Right

Install the below extensions in VS Code to speed up your development time

- [Auto Import](https://marketplace.visualstudio.com/items?itemName=NuclleaR.vscode-extension-auto-import)
- [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [HTML Format](https://marketplace.visualstudio.com/items?itemName=mohd-akram.vscode-html-format)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

---

[<< Previous](https://costaivo.com/tutorial-reactjs) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-101b)
