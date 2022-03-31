# React Tutorials - Quotes App - 102 --- > Adding Routes

## Adding Routes

### Adding the required packages

React does not come with a built in routing mechanism like Angular. we need to install and additional npm package to enable routing.
Install the `react-router-dom` package using command

``` bash
  npm install react-router-dom
```

### Add pages

create a folder **pages** and add create the following files 
- AuthorPage.jsx
- QuotePage.jsx
- HomePage.jsx

In each of the Page component file, create a functional component. 
**Tip:** Type **rfce** inside the empty file and press tab, for ES6/Javascript snippet extension to generate the code for a functional component.

``` javascript
function HomePage() {
  return (
    <div>HomePage</div>
  )
}

export default HomePage
```

### Add Routes

To start writing the routes, first import the following modules from the `react-router-dom` package

``` javascript
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
```

**Tip:** Type **imb** below the existing imports to generate the snippet to import the **BrowserRouter**.

Add the below code to add the routing logic for the application

``` javascript
   <Router>
        <Routes>
          <Route path="/author" element={<AuthorPage />} />
          <Route path="/quote" element={<QuotePage />} />
          <Route path="/" element={<HomePage />} />
        </Routes>
  </Router>
```

Click on the Navigation routes and check if the route paths work


[Previous](https://costaivo.com/tutorial-reactjs/quotes-102)  &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[Index](https://costaivo.com/tutorial-reactjs) &nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;
[Next](https://costaivo.com/tutorial-reactjs/quotes-102b) 
