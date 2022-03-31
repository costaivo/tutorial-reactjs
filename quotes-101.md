# React Tutorials - Quotes App - 101 ---> Getting Started

## Creating the Project Structure

### Create react app using `create-react-app`
 
 create the react application using the command
 
 ``` cmd
    npx create-react-app quotes-app
 ```


### Clean up

Remove all the files that are not required 
- logo.svg
- reportWebVitals.js
- App.test.js
- setupTests.js
- public/logo*.png
- public/manifest.json
- public/robots.txt

Clear the contents of the following files
- App.css
- index.css

Open the `App.js` file 
- remove all the unused imports of the delete files
- replace the return statement as shown below


``` typescript

function App() {
  return (
   <div>Quotes App</div>
  );
}

export default App;
```

- Open `index.js` file and remove unused imports
- Open `public\index.html`  file and replace its content with below code

``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Quotes App</title>
  </head>
  <body>
    <div id="root"></div>
  </body>
</html>

```

### Run the application 

start the react application and validate if the project is running properly on the default port 3000

``` cmd
    npm start
```

## Setting our Dev Enviornment Right

Install the below extenstions in VS Code to speed up your developement time

- [Auto Import ](https://marketplace.visualstudio.com/items?itemName=NuclleaR.vscode-extension-auto-import)
- [ES7+ React/Redux/React-Native snippets](https://marketplace.visualstudio.com/items?itemName=dsznajder.es7-react-js-snippets)
- [HTML Format](https://marketplace.visualstudio.com/items?itemName=mohd-akram.vscode-html-format)
- [Prettier - Code formatter](https://marketplace.visualstudio.com/items?itemName=esbenp.prettier-vscode)

<hr/>
[Previous](https://costaivo.com/tutorial-reactjs)  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[Index](https://costaivo.com/tutorial-reactjs) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[Next](https://costaivo.com/tutorial-reactjs/quotes-101b) 
