# React Tutorials - Quotes App - 102 --- > Adding Routes

## Add Navigation Menu compoonent

### Create src/components/Navbar.tsx

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

#### Code Explanation

- This line imports the Link component from react-router-dom, which is used for navigation within the application without reloading the page.

- The NavbarDark function is a React functional component.
- It returns a JSX structure that represents a navigation bar (<nav> element) with Bootstrap classes for styling.
- The navbar-expand-lg class makes the navbar responsive, expanding on large screens.
- The navbar-dark bg-dark classes apply a dark theme to the navbar.
- Inside the navbar, there is a container (<div className="container-fluid">) that holds the content.
- The Link component is used to create a brand link that navigates to the home page ("/").
- A button is included to toggle the navigation menu on smaller screens. This button uses Bootstrap's - - - - - collapse functionality with appropriate data-bs-* attributes and ARIA attributes for accessibility.
- This component sets up a responsive, dark-themed navigation bar that can be used across the application.

Modify the `src/App.tsx` file to include the Navbar component:

``` tsx
 <div className="App">
        <NavbarDark />
        <Routes>
          <!--- existing routes -->
        </Routes>
    </div>
```

---

[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-101b) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-102b)
