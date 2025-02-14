# React Tutorials - Quotes App -102- Adding Navigation and Footer Components

## Introduction

In this section, we'll enhance our Quotes application by adding a proper navigation menu and footer. These components will improve the user experience and give our application a more professional look. We'll use Bootstrap classes for styling and ensure our layout works well across different screen sizes.

## What We'll Build

In this section, we'll:

1. Create a responsive navigation component with:
   - Brand logo/text
   - Collapsible menu for mobile devices
   - Navigation links using React Router
2. Add a sticky footer that:
   - Stays at the bottom of the viewport
   - Shows copyright information
3. Implement proper layout structure to:
   - Handle content of varying lengths
   - Prevent footer overlap
   - Maintain responsive design

## Step 1: Adding the Navigation Menu

First, we'll create a navigation menu that allows users to move between different sections of our application. The navigation will include links to Home, Quotes, and Authors pages.

### Create src/components/Navbar.tsx

Create a new file called `Navbar.tsx` in the components directory and add the following code:

```tsx
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

### Understanding the Navbar Component

The Navbar component is built using Bootstrap's navigation classes and React Router's Link component. Here's what each part does:

1. **Link Component**: We use React Router's `Link` component instead of regular `<a>` tags to prevent page reloads during navigation.

2. **Bootstrap Classes**:
   - `navbar-expand-lg`: Makes the navbar responsive, expanding on larger screens
   - `navbar-dark bg-dark`: Applies a dark theme with white text
   - `container-fluid`: Provides full-width container behavior

3. **Responsive Design**:
   - The navbar includes a hamburger menu button that appears on mobile devices
   - The menu collapses on smaller screens and expands on larger ones

### Integrating the Navbar

Update your `App.tsx` to include the new Navbar component:

```tsx
import NavbarDark from './components/Navbar';

function App() {
  return (
    <div className="App">
      <NavbarDark />
      <Routes>
        {/* existing routes */}
      </Routes>
    </div>
  );
}
```

## Step 2: Adding the Footer

Next, we'll add a footer component to display copyright information and provide a professional finish to our application.

### Create src/components/Footer.tsx

Create a new file called `Footer.tsx` and add this code:

```tsx
export default function Footer() {
  return (
    <footer className="footer mt-auto py-3 bg-dark text-white fixed-bottom">
      <div className="container text-center">
        <span>&copy; {new Date().getFullYear()} Quotes App. All rights reserved.</span>
      </div>
    </footer>
  );
}
```

### Understanding the Footer Component

The Footer component uses several Bootstrap utilities to achieve its styling:

1. **Positioning**:
   - `fixed-bottom`: Keeps the footer at the bottom of the viewport
   - `mt-auto`: Automatically adjusts top margin to push footer down

2. **Styling**:
   - `py-3`: Adds padding on top and bottom
   - `bg-dark text-white`: Creates a dark background with white text
   - `text-center`: Centers the content

### Integrating the Footer

Update your `App.tsx` to include the Footer component with proper layout structure:

```tsx
import NavbarDark from './components/Navbar';
import Footer from './components/Footer';

function App() {
  return (
    <Router>
      <div className="App">
      <NavbarDark />
        <Routes>
        {/* existing routes */}
        </Routes>
        <Footer />
      </div>
    </Router>
  );
}
```

### Understanding the Layout Structure

The updated App component uses Flexbox to create a sticky footer layout:

1. **Container Setup**:
   - `d-flex flex-column`: Creates a vertical flex container
   - `min-vh-100`: Ensures minimum height of 100% viewport height

2. **Content Area**:
   - `flex-shrink-0`: Prevents the main content from shrinking
   - Wrapped in `main` tag for semantic HTML

This structure ensures that:

- The footer stays at the bottom even when content is short
- Content can push the footer down when it exceeds the viewport height
- The layout remains responsive across different screen sizes

## Summary

In this tutorial, we:

- Created a responsive navigation bar using Bootstrap and React Router
- Added a sticky footer component
- Implemented proper layout structure to handle content and footer positioning
- Enhanced the overall user experience with proper navigation

Now our application has a professional look with consistent navigation and footer across all pages.

## What's Next

In quotes-103, we'll:

- Add a quotes data source
- Implement quote listing functionality
- Create a quote card component
- Display real quotes instead of placeholder content

This will transform our application from a static shell into a dynamic quotes display system.

---

[<< Previous](/tutorial-reactjs/quotes-101) | [Index](/tutorial-reactjs/) | [Next >>](/tutorial-reactjs/quotes-103)
