# React Tutorials - Quotes App - 101b --- > Setting up the Navigation

## Add Bootstrap

### Adding bootstrap using CDN
In this project we will add bootstrap CSS framework to the project using CDN
Navigate to the site [Bootstrap Getting Started](https://getbootstrap.com/docs/5.1/getting-started/introduction/)

- Copy-Paste the CSS CDN link in the **Head** section of the HTML file `public/index.html`
- Copy-Paste the JS CDN link in the **BODY** section of the HTML file `public/index.html`
- The html file code should look like the one shown below

``` html
<!DOCTYPE html>
<html lang="en">
  <head>
    <title>Quotes App</title>
    <link href="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/css/bootstrap.min.css" rel="stylesheet" integrity="sha384-1BmE4kWBq78iYhFldvKuhfTAU6auU8tT94WrHftjDbrCEXSU1oBoqyl2QvZ6jIW3" crossorigin="anonymous">

  </head>
  <body>
    <div id="root"></div>
    <script src="https://cdn.jsdelivr.net/npm/bootstrap@5.1.3/dist/js/bootstrap.bundle.min.js" integrity="sha384-ka7Sk0Gln4gmtz2MlQnikT1wXgYsOg+OMhuP+IlRH9sENBO0LRn5q+8nbTov4+1p" crossorigin="anonymous"></script>
  </body>
</html>
```

- test if boostrap components are rendering properly by adding a button in the `App.js` file

``` typescript
 function App() {
  return (
   <div>
     <h1>Quotes App</h1>
      <button type="button" class="btn btn-primary">Primary</button>
   </div>
  );
}
 ```
 - Run the project, open the browser and validate if you see the bootstrap button is rendered 

 - On the browser, open the developers tools and click on the **Console** tab. Notice the error in the console. 

``` console
Warning: Invalid DOM property `class`. Did you mean `className`?
    at button
    at div
    at App
```
 - The above error occurs, since `class` name is a keyword in Javascript and JSX uses JavaScript, hence `class` word cannnot be used as an attribute in JSX HTML element definations. Instead you have to use `className`

 - Replace `class` with `className` and validate if the console error is gone

## Adding Navigation Menu 
We will now add the Navigation Menu to the site using bootstrap **NavBar**
- Copy the code snippet of the NavBar code example you prefer from the  [bootstrap Nav Examples](https://getbootstrap.com/docs/5.1/components/navbar/)

- Paste the code inside the Root div element of the `App.js` file and replace `class` with `className`

- Add/remove routes corressponding to the Quotes app
  - '/' --> Home
  - '/quote' --> Quote
  - '/author' --> Author


[:arrow_left: Previous](https://github.com/costaivo/tutorial-reactjs/blob/main/quotes-101b.md)  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[:1234: Index](https://github.com/costaivo/tutorial-reactjs) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[:arrow_right: Next](https://github.com/costaivo/tutorial-reactjs/blob/main/quotes-102.md) 
