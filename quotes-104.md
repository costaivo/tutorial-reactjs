# React Tutorials - Quotes App -104- DRY Principle

## What is DRY?

DRY (Don't Repeat Yourself) is a fundamental principle of software development that aims to reduce code duplication by extracting repeated code into reusable components.

## Implementing DRY in our Quotes App

We noticed that both the Home Page and Quotes Page use identical code to render quotes. Let's refactor this duplicate code into a reusable `Quote` component.

### Creating the Quote Component

1. Create a new file `Quote.jsx` in the `components` folder
1. Add the following code:

```javascript
function Quote(props) {
  const { quote } = props;
  return (
    <div className="m-2">
      <h5>{quote.quote}</h5>
      <h6>{quote.author}</h6>
      <hr />
    </div>
  );
}

export default Quote;
```

1. Update `QuotePage.jsx` to use the new component:

```javascript
{quotes.map((quote) => (
  <Quote quote={quote} key={quote._id} />
))}
```

1. Update `HomePage.jsx` to use the same component:

```javascript
<Quote quote={quoteOfDay} />
```

## Adding Author Links

### Configure Route Parameters

1. Update `App.js` to handle author-specific routes:

```javascript
<Route path="/quote/:author" element={<QuotePage />} />
```

1. Modify `AuthorPage.jsx` to create author links:

```javascript
<Link to={`/quote/${author}`}>{author}</Link>
```

### Implementing Quote Filtering

Use the `useParams` hook to filter quotes by author:

```javascript
const params = useParams();

const getFilteredQuotes = (author) => {
  if (author && author !== '') {
    quotes = quotes.filter((x) => x.author === author);
  }
};
```

## Adding Search Functionality

### Setting up State Management

1. Initialize state using the `useState` hook:

```javascript
const [searchAuthor, setSearchAuthor] = useState('');
```

1. Create the search input:

```javascript
<input
  type="text"
  className="form-control"
  placeholder="Author Name"
  value={searchAuthor}
  onChange={handleOnChange}
/>
```

1. Implement the change handler:

```javascript
const handleOnChange = (e) => {
  e.preventDefault();
  setSearchAuthor(e.target.value);
};
```

### Managing Quote Loading

1. Create helper functions:

```javascript
const loadQuotes = () => {
  getFilteredQuotes(params.author);
};

const handleSubmit = (e) => {
  e.preventDefault();
  getFilteredQuotes(searchAuthor);
};
```

1. Use `useEffect` for initial loading:

```javascript
useEffect(() => {
  loadQuotes();
}, []);
```

## Next Steps

In the next tutorial, we'll connect our application to API endpoints to fetch real data.

---

[<< Previous](/tutorial-reactjs/quotes-103) | [IIIIndex](/tutorial-reactjs/) | [Next >>](../tutorial-reactjs/quotes-105)
