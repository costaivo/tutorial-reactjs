# React Tutorials - Quotes App  --101- Setting up the Navigation using Routes

## Introduction

In this section, we'll add navigation to our Quotes App using React Router. We'll create multiple pages and implement a navigation menu to move between them. This will give our application a proper multi-page structure. Navigation is a fundamental part of web applications, allowing users to move between different sections smoothly without page reloads.

## What We'll Build

In this section, we'll:

1. Set up React Router for navigation
2. Create three main pages:
   - Home: Welcome page
   - Quotes: Display quotes list
   - Authors: Show authors list
3. Implement a navigation menu
4. Test the routing functionality

This will form the foundation for adding more features in upcoming sections.

## Installing Required Dependencies

First, install the routing dependencies:

```bash
pnpm add react-router-dom @types/react-router-dom
```

## Creating Page Components

We'll create three main pages for our application. You can use VS Code snippets to quickly generate React functional components. Here are some useful snippets:

- `rafce` - React Arrow Function Component with Export
- `rfc` - React Function Component
- `rfce` - React Function Component with Export

To use these snippets:

1. Create a new file with `.tsx` extension
1. Type the snippet shortcut (e.g., `rafce`)
1. Press Tab or Enter
1. The snippet will expand into a full component template

For example, typing `rafce` will generate:

```tsx
const ComponentName = () => {
  return (
    <div>ComponentName</div>
  )
}

export default ComponentName
```

First, create a new `pages` directory in your `src` folder:

```bash
mkdir src/pages
```

### Create src/pages/HomePage.tsx

This will be our landing page, welcoming users to the application.

```tsx
export default function HomePage() {
  return (
    <div className="container mt-4">
      <h1>Welcome to Quotes App</h1>
      <p>Explore inspiring quotes from famous authors</p>
    </div>
  );
}
```

### Create src/pages/QuotePage.tsx

This page will display our collection of quotes. For now, we'll use placeholder content.

``` tsx
export default function QuotePage() {
  return (
    <div className="container mt-4">
      <h1>Quotes</h1>
      <div className="card mt-3">
        <div className="card-body">
          <blockquote className="blockquote mb-0">
            <p>Quote content will appear here...</p>
            <footer className="blockquote-footer mt-2">Author name</footer>
          </blockquote>
        </div>
      </div>
      <div className="card mt-3">
        <div className="card-body">
          <blockquote className="blockquote mb-0">
            <p>Quote content will appear here...</p>
            <footer className="blockquote-footer mt-2">Author name</footer>
          </blockquote>
        </div>
      </div>
        <div className="card mt-3">
        <div className="card-body">
          <blockquote className="blockquote mb-0">
            <p>Quote content will appear here...</p>
            <footer className="blockquote-footer mt-2">Author name</footer>
          </blockquote>
        </div>
      </div>
    </div>
  );
}
```

### Create src/pages/AuthorPage.tsx

This page will show a list of quote authors. We'll populate it with real data later.

```tsx
export default function AuthorPage() {
  return (
    <div className="container mt-4">
      <h1>Authors</h1>
      <ul className="list-group mt-3">
        <li className="list-group-item">Author 1</li>
        <li className="list-group-item">Author 2</li>
        <li className="list-group-item">Author 3</li>
      </ul>
    </div>
  );
}
```

After creating all pages, your project structure should look like this:

```bash
src/
├── pages/
│   ├── HomePage.tsx
│   ├── QuotePage.tsx
│   └── AuthorPage.tsx
├── App.tsx
└── main.tsx
```

## Setting up the Router

React Router allows us to create a single-page application with multiple views. The `BrowserRouter` component enables client-side routing, while `Routes` and `Route` components define our application's routing structure.

### Update src/App.tsx

```tsx
import { BrowserRouter as Router, Route, Routes, Link } from 'react-router-dom';
import HomePage from './pages/HomePage';
import QuotePage from './pages/QuotePage';
import AuthorPage from './pages/AuthorPage';

function App() {
  return (
    <Router>
      <div className="App">
        <nav className="navbar navbar-expand-lg navbar-light bg-light">
          <div className="container">
            <div className="navbar-nav">
              <Link className="nav-link" to="/">Home</Link>
              <Link className="nav-link" to="/quotes">Quotes</Link>
              <Link className="nav-link" to="/authors">Authors</Link>
            </div>
          </div>
        </nav>

        <Routes>
          <Route path="/" element={<HomePage />} />
          <Route path="/quotes" element={<QuotePage />} />
          <Route path="/authors" element={<AuthorPage />} />
        </Routes>
      </div>
    </Router>
  );
}

export default App;
```

## Testing the Navigation

1. Start your development server:

```bash
pnpm dev
```

1. Open your browser to [http://localhost:3000](http://localhost:3000)

1. Verify that:
   - The navigation menu appears at the top
   - Clicking each link loads the corresponding page
   - The URL changes appropriately for each page
   - Each page displays its content correctly

## Troubleshooting

If you encounter issues:

1. **Navigation links not working:**
   - Ensure `BrowserRouter` wraps your entire application
   - Check that all import paths are correct
   - Verify route paths match exactly with your Link components

2. **Pages not displaying:**
   - Check the browser console for errors
   - Verify all page components are properly exported
   - Ensure route paths are correctly defined

## What's Next

With our navigation structure in place, in quotes-102 we'll:

- Add real quote data to our application
- Create reusable components for displaying quotes
- Implement quote filtering and searching functionality

This will transform our basic structure into a dynamic quotes application.

---

[<< Previous](/tutorial-reactjs/quotes-100) | [Index](/tutorial-reactjs/) | [Next >>](/tutorial-reactjs/quotes-102)
