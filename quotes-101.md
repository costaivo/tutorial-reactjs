# React Tutorials - Quotes App  -- Setting up the Navigation using Routes

## Add Routes

To set up navigation in your React application, you need to install `react-router-dom` which provides the necessary components and hooks for routing. The `@types/react-router-dom` package provides TypeScript definitions for `react-router-dom`.

``` bash
pnpm add react-router-dom @types/react-router-dom
```

Now create the page components:
Add three page components:

- HomePage,
- QuotePage,
- and AuthorPage.

### Use Snippets to Generate Components

For each file:

- Create a new file in the `src/pages` directory
- Open the new file
- Type the snippet command (**rafce** or **rfe**)
- Press Tab or Enter to generate the boilerplate
- Customize the component name and content

Example: HomePage.tsx

``` tsx
// Type 'rafce' and press Enter
const HomePage = () => {
  return (
    <div>
      <h1>Home Page</h1>
      <p>Welcome to the Quotes App!</p>
    </div>
  )
}

export default HomePage
```

## Change Default Generated code file

- Open the file
- Change the code to match as shown below

### Create src/pages/HomePage.tsx

``` tsx

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

### Add Routing Logic

To add routing logic to your application, you need to set up a router in your `src/App.tsx` file. Import the necessary components from `react-router-dom` and define the routes for your pages.

### Update src/App.tsx

``` tsx
import { BrowserRouter as Router, Route, Routes } from 'react-router-dom';
import HomePage from './pages/HomePage';
import QuotePage from './pages/QuotePage';
import AuthorPage from './pages/AuthorPage';

function App() {
  return (
    <Router>
      <div className="App">
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

This code sets up a router with three routes:

- `/` for the `HomePage` component
- `/quote` for the `QuotePage` component
- `/authors` for the `AuthorPage` component

Now, when you navigate to these paths in your browser, the corresponding components will be rendered.

### Add Navigation Menu

To add a navigation menu to your application.

``` tsx
    <div className='"navbar navbar-expand-lg navbar-light bg-light'>
        <Link className="nav-link" to="/">Home</Link>
        <Link className="nav-link" to="/quotes">Quotes</Link>
        <Link className="nav-link" to="/authors">Author</Link>
      </div>
      <Routes>
        <!--- existing routes -->
        </Routes>
```

---

[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-100) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-102)
