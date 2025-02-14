# React Tutorials - Quotes App -103- Wiring Pages to Work

## Introduction

In this section, we'll implement the core functionality of our pages by adding real data and interactive features. We'll populate our pages with actual quotes and authors, and add search functionality to help users find specific content.

## What We'll Build

In this section, we'll:

1. Implement the Authors page with:
   - List of unique authors
   - Clickable author names linking to quotes
2. Create the Quotes page featuring:
   - Display of quote cards with text and author
   - Search functionality by author name
3. Set up the Home page with:
   - Quote of the day feature
   - Welcome message and app description

## Author Page

### Listing the Authors

```typescript
export default function AuthorPage() {
  // Remove duplicate authors using Set
  const authors = [...new Set([
    "A. P. J. Abdul Kalam",
    "Gandhi",
    "Ivo Costa",
    "Jakob",
    "John Lennon",
    "Ivo Costa",
    "Lao-Tze",
    "Larry Niven",
    "Linnie",
    "Martin Fowler",
    "Michael Feathers",
    "Michael Jordan",
    "Nelson Mandela",
    "Steve Jobs",
  ])];

  return (
    <div className="container mt-4">
      <h1>Authors</h1>
      <ul className="list-group mt-3">
        {authors.map((author, index) => (
          <li key={index} className="list-group-item">
            <Link to={`/quotes?author=${encodeURIComponent(author)}`}>
              {author}
            </Link>
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
            text: "Be the change you wish to see in the world.",
            author: "Mahatma Gandhi"
        },
        {
            text: "Two things are infinite: the universe and human stupidity; and I'm not sure about the universe.",
            author: "Albert Einstein"
        },
        {
            text: "In three words I can sum up everything I've learned about life: it goes on.",
            author: "Robert Frost"
        },
        {
            text: "To be yourself in a world that is constantly trying to make you something else is the greatest accomplishment.",
            author: "Ralph Waldo Emerson"
        },
        {
            text: "The only way to do great work is to love what you do.",
            author: "Steve Jobs"
        }
    ];

    return (
        <div className="container mt-4">
            <h1>All Quotes</h1>
            <form className="row m-3">
                <div className="input-group">
                    <span className="input-group-text" id="basic-addon1">
                        Search by Author
                    </span>
                    <input type="text" className="form-control" placeholder="Author Name" />
                    <button type="submit" className="btn btn-primary">
                        Search
                    </button>
                </div>
            </form>
            {quotes.map((quote, index) => (
                <div key={index} className="card mt-3">
                    <div className="card-body">
                        <blockquote className="blockquote mb-0">
                            <p>{quote.text}</p>
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
    quote: 'If you want to shine like a sun, first burn like a sun.',
    author: 'A. P. J. Abdul Kalam',
  };
  
  return (
    <div className="container mt-4">
      <h1>Quotes App</h1>
      <p><strong>Explore inspiring quotes from famous authors</strong></p>
      <hr />
      <h3 className="text-primary">Quote of the Day</h3>
      <div className="card">
        <div className="card-body">
          <h5 className="card-title">{quoteOfDay.quote}</h5>
          <p className="card-text">Author: {quoteOfDay.author}</p>
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

- Add state management for the search functionality
- Implement filtering quotes by author
- Add error handling and loading states
- Enhance the user experience with feedback messages

This will make our application fully interactive and user-friendly.

---

[<< Previous](/tutorial-reactjs/quotes-102) | [Index](/tutorial-reactjs/) | [Next >>](/tutorial-reactjs/quotes-104)
