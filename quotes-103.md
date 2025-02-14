# React Tutorials - Quotes App -103-  Listing static data and Linking  pages

## Introduction

In this section, we'll implement the core functionality of our pages by adding real data and interactive features. We'll populate our pages with actual quotes and authors, and add search functionality to help users find specific content.

## What We'll Build

In this section, we'll:

1. Implement the Authors page with:
   - List of unique authors
2. Create the Quotes page featuring:
   - Display of quote cards with text and author
3. Set up the Home page with:
   - Quote of the day feature
   - Welcome message and app description

## Author Page

### Listing the Authors

```typescript
export default function AuthorPage() {
  const authors = [...new Set([
    "A. P. J. Abdul Kalam",
    "Albert Einstein",
    "Mahatma Gandhi",
    "Ralph Waldo Emerson",
    "Robert Frost",
    "Steve Jobs"
  ])].sort(); 

  return (
    <div className="container mt-4">
      <h1>Authors</h1>
      <ul className="list-group mt-3">
        {authors.map((author) => (
          <li key={author} className="list-group-item">
              {author}
          </li>
        ))}
      </ul>
    </div>
  );
}
```

## Quotes Page

### Listing Quotes

```typescript
export default function QuotePage() {
    const quotes = [
        {
            _id: "550e8400-e29b-41d4-a716-446655440000",
            quote: "Be the change you wish to see in the world.",
            author: "Mahatma Gandhi"
        },
        {
            _id: "6ba7b810-9dad-11d1-80b4-00c04fd430c8",
            quote: "Two things are infinite: the universe and human stupidity; and I'm not sure about the universe.",
            author: "Albert Einstein"
        },
        {
            _id: "6ba7b811-9dad-11d1-80b4-00c04fd430c8",
            quote: "In three words I can sum up everything I've learned about life: it goes on.",
            author: "Robert Frost"
        },
        {
            _id: "6ba7b812-9dad-11d1-80b4-00c04fd430c8",
            quote: "To be yourself in a world that is constantly trying to make you something else is the greatest accomplishment.",
            author: "Ralph Waldo Emerson"
        },
        {
            _id: "6ba7b813-9dad-11d1-80b4-00c04fd430c8",
            quote: "The only way to do great work is to love what you do.",
            author: "Steve Jobs"
        }
    ];

    return (
        <div className="container mt-4">
            <h1>All Quotes</h1>
            {quotes.map((quote, index) => (
                <div key={index} className="card mt-3">
                    <div className="card-body">
                        <blockquote className="blockquote mb-0">
                            <p>{quote.quote}</p>
                            <footer className="blockquote-footer mt-2">{quote.author}</footer>
                        </blockquote>
                    </div>
                </div>
            ))}
        </div>
    );
}
```

## Home Page

### Quote of the Day

```typescript
export default function HomePage() {
    const quoteOfDay = {
        _id: "9ba7b812-9dad-11d1-80b4-00c04fd430c8",
        quote: 'If you want to shine like a sun, first burn like a sun.',
        author: 'A. P. J. Abdul Kalam',
      };
    return (
        <div className="container mt-4">
        <h1>Quotes App</h1>
        <p><strong>Explore inspiring quotes from famous authors</strong></p>
        <hr />
        <div  className="card mt-3">
                    <div className="card-body">
                        <blockquote className="blockquote mb-0">
                            <p>{quoteOfDay.quote}</p>
                            <footer className="blockquote-footer mt-2">{quoteOfDay.author}</footer>
                        </blockquote>
                    </div>
        </div>
      </div>
    );
  }
```

## Testing the Application

1. Run the application:

```bash
pnpm run dev
```

1. Test the following functionality:
   - Navigation between pages
   - Author links leading to quotes page
   - Quote of the day display
   - Search form interaction
   - Responsive layout on different screen sizes

1. Check browser console for any errors or warnings

## What's Next

In quotes-104, we'll:

- Add Quote Card Component
- Add Search Form
- Link the Author Page to the Quotes Page

This will make our application fully interactive and user-friendly.

---

[<< Previous](/tutorial-reactjs/quotes-102) | [Index](/tutorial-reactjs/) | [Next >>](/tutorial-reactjs/quotes-104)
