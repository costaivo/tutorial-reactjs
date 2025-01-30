# React Tutorials - Quotes App - 102 --- > Adding Routes

## Add Navigation Menu compoonent

### Create src/components/Navbar.tsx

``` tsx
import { Link } from 'react-router-dom';

export default function Navbar() {
    return (
        <nav className="navbar navbar-expand-lg navbar-light bg-light">
            <div className="container-fluid">
                <Link className="navbar-brand" to="/">Quotes App</Link>
                <button 
                    className="navbar-toggler" 
                    type="button" 
                    data-bs-toggle="collapse" 
                    data-bs-target="#navbarNav" 
                    aria-controls="navbarNav" 
                    aria-expanded="false" 
                    aria-label="Toggle navigation"
                >
                    <span className="navbar-toggler-icon"></span>
                </button>
                <div className="collapse navbar-collapse" id="navbarNav">
                    <ul className="navbar-nav me-auto mb-2 mb-lg-0">
                        <li className="nav-item">
                            <Link className="nav-link" to="/">Home</Link>
                        </li>
                        <li className="nav-item">
                            <Link className="nav-link" to="/quote">Quotes</Link>
                        </li>
                        <li className="nav-item">
                            <Link className="nav-link" to="/authors">Authors</Link>
                        </li>
                    </ul>
                </div>
            </div>
        </nav>
    );
}
```

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

### Move Navbar to its own component with dark theme

To move the `Navbar` to its own component and apply a dark theme, follow these steps:

1. Create a new file `src/components/NavbarDark.tsx`.

2. Update the `Navbar` component to use a dark theme:

``` tsx
import { Link } from 'react-router-dom';

export default function NavbarDark() {
  return (
    <nav className="navbar navbar-expand-lg navbar-dark bg-dark">
      <div className="container-fluid">
        <Link className="navbar-brand" to="/">Quotes App</Link>
        <button 
          className="navbar-toggler" 
          type="button" 
          data-bs-toggle="collapse" 
          data-bs-target="#navbarNav" 
          aria-controls="navbarNav" 
          aria-expanded="false" 
          aria-label="Toggle navigation"
        >
          <span className="navbar-toggler-icon"></span>
        </button>
        <div className="collapse navbar-collapse" id="navbarNav">
          <ul className="navbar-nav me-auto mb-2 mb-lg-0">
            <li className="nav-item">
              <Link className="nav-link" to="/">Home</Link>
            </li>
            <li className="nav-item">
              <Link className="nav-link" to="/quotes">Quotes</Link>
            </li>
            <li className="nav-item">
              <Link className="nav-link" to="/authors">Authors</Link>
            </li>
          </ul>
        </div>
      </div>
    </nav>
  );
}
```

---

[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-101b) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-102)
