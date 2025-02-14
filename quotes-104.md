# React Tutorials - Quotes App -104- DRY Principle

## What is DRY?

DRY (Don't Repeat Yourself) is a fundamental principle of software development that aims to reduce code duplication by extracting repeated code into reusable components.

## Implementing DRY in our Quotes App

We noticed that both the Home Page and Quotes Page use identical code to render quotes. Let's refactor this duplicate code into a reusable `Quote` component.

### Creating the Quote Component

1. Create a new file `Quote.jsx` in the `components` folder
1. Add the following code:

```tsx
interface QuoteType {
  _id: string;
  text: string;
  author: string;
}

interface QuoteProps {
  quote: QuoteType;
}

function Quote({ quote }: QuoteProps) {
  return (
    <div className="card mt-3">
      <div className="card-body">
        <blockquote className="blockquote mb-0">
          <p>{quote.text}</p>
          <footer className="blockquote-footer mt-2">{quote.author}</footer>
        </blockquote>
      </div>
    </div>
  )
}

export default Quote
```

1. Update `QuotePage.jsx` to use the new component:

```tsx
{quotes.map((quote) => (
  <Quote quote={quote} key={quote._id} />
))}
```

1. Update `HomePage.jsx` to use the same component:

```tsx
<Quote quote={quoteOfDay} />
```

## Adding Author Links

### Configure Route Parameters

1. Update `App.tsx` to handle author-specific routes:

```tsx
<Route path="/quotes" element={<QuotePage />} />
<Route path="/quotes/:author" element={<QuotePage />} />
```

1. Modify `AuthorPage.tsx` to create author links:

```tsx
<Link to={`/quotes?author=${encodeURIComponent(author)}`}>
```

1. Update `QuotePage.tsx` to handle author-specific quotes:

```tsx
import { useSearchParams } from 'react-router-dom';

export default function QuotePage() {
    const [searchParams] = useSearchParams();
    const author = searchParams.get('author');
  // Filter quotes if author parameter exists
  const displayedQuotes = author 
    ? quotes.filter(q => q.author === decodeURIComponent(author))
    : quotes;
  
  return (
    // ... existing JSX using displayedQuotes
  );
}
```

## Project Structure After Changes

```bash
src/
├── components/
│   └── Quote.tsx       # New reusable quote component
├── pages/
│   ├── HomePage.tsx    # Updated to use Quote component
│   ├── QuotePage.tsx   # Updated to use Quote component
│   └── AuthorPage.tsx  # Updated with author links
└── App.tsx            # Updated with new routes
```

---

[<< Previous](/tutorial-reactjs/quotes-103) | [Index](/tutorial-reactjs/) | [Next >>](../tutorial-reactjs/quotes-105)
