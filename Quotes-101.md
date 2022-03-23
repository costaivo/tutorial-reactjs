# React Tutorials - Quotes App - 01

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
``` Javascript

function App() {
  return (
   <div>Quotes App</div>
  );
}

export default App;

```

Open `index.js` file and remove unused imports


### Run the application 

start the react application and validate if the project is running properly on the default port 3000

``` cmd
    npm start
```

