# React Tutorials - Quotes App -103- Wiring Pages to work

## Author Page

### Listing the Authors

``` typescript

export default function AuthorPage() {
  const authors = [
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
    "Lao-Tze",
    "Steve Jobs",
  ];

  return (
    <div className="container mt-4">
      <h1>Authors</h1>
      <ul className="list-group mt-3">
        {authors.map((author) => (
          <li className="list-group-item">{author}</li>
        ))}
      </ul>
    </div>
  );
}
```

## Quotes Page

### Listing Quotes

- Assign the values to a const variable **quotes** in the `QuotePage.jsx`
- Write a map function in the return statement to render the author names as a list

``` typescript
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
            {quotes.map((quote) => (
                <div className="card mt-3">
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

### Quote of the day

- create a variable **quoteOfDay** and set it to a quote value
- write code to rendre the quote

``` typescript

export default function HomePage() {
  const quoteOfDay = {
    quote: 'If you want to shine like a sun, first burn like a sun.',
    author: 'A. P. J. Abdul Kalam',
  };
  return (
      <div className="container mt-4">
        <h1>Quotes App</h1>
        <p><strong>Explore inspiring quotes from famous authors</strong></p>
        <hr></hr>
        <p> <h3 className="text-primary"> Quote of the Day </h3></p>
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

## Revisit  -> Quotes page & Author page

### Add the form to search for quote based on Author

Add a form to the QuotesPage to implement the search by Author functionality

``` typescript
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
```

### Add link from Author to Quotes Page

Modify the code in the Author page to include a hyperlink to take the user to the Quotes page on clicking on the Author
For this we need to use the **Link** element from `react-router-dom`
Modify the code to look as shown below

``` typescript
authors.map(author=>(<p>
              <Link to='/quote'>{author}</Link>
              </p>))
```

## Testing the application

- Run the application using `pnpm run dev`
- Open the application in the browser using `http://localhost:3000`
- Test the application by clicking on the links to navigate to the different pages
- On the browser console check for any errors
- On the browser console, check the network calls to ensure that the application is working as expected

```diff
- Fix the issues in the code to ensure no errors are shown in the browser console
```

---

[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-102) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next >>](https://costaivo.com/tutorial-reactjs/quotes-104)
