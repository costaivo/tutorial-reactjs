# React Tutorials - Quotes App - 102b --- > Wiring all the pages to work

## Author Page

### Listing the Authors 

Initially we will implement all the functionality without actually connecting with the API. So that we can focus on building the application structure first. 

- Navigate to the api endpoint and copy the response from the endpoint returned by the [Author API](https://quote-api-app.herokuapp.com/author)

- Assign the values to a const variable **authors** in the `AuthorPage.jsx`
- Write a map function in the return statement to render the author names as a list


``` typescript

function AuthorPage() {
    const authors =[
        "A. P. J. Abdul Kalam",
        "Gandhi",
        "Ivo Costa",
        "Jakob",
        "John Lennon",
        "Lao-Tze",
        "Larry Niven",
        "Linnie",
        "Martin Fowler",
        "Michael Feathers",
        "Michael Jordan",
        "Nelson Mandela",
        "Steve Jobs",
      ]
  return (
    <div>
        {
            authors.map(author=>(<p>{author}</p>))
        }
    </div>
  )
}

export default AuthorPage
```

## Quotes Page

### Listing Quotes 

- Navigate to the api endpoint and copy the response from the endpoint returned by the [Quote API](https://quote-api-app.herokuapp.com/quote)

- Assign the values to a const variable **quotes** in the `QuotePage.jsx`
- Write a map function in the return statement to render the author names as a list

``` javascript
function QuotePage() {

    const quotes = [
        {
          "likes": 1,
          "dislikes": 0,
          "isActive": true,
          "_id": "611ba4f0bf79660015b222fc",
          "quote": "If you want to shine like a sun, first burn like a sun.",
          "author": "A. P. J. Abdul Kalam",
          "__v": 0
        },
      ]
  return (
    <div>
    {quotes.map((quote)=>(
        <div>
            <h5>{quote.quote}</h5>  
            <h6>{quote.author}</h6> 
            <hr/>
        </div>
    ))}</div>
  )
}

export default QuotePage
```


## Home Page

### Quote of the day

- create a variable **quoteOfDay** and set it to a quote value
- write code to rendre the quote


``` javascript
function HomePage() {
  const quoteOfDay = {
    likes: 1,
    dislikes: 0,
    isActive: true,
    _id: '611ba4f0bf79660015b222fc',
    quote: 'If you want to shine like a sun, first burn like a sun.',
    author: 'A. P. J. Abdul Kalam',
    __v: 0,
  };
  return (
    <div>
      <h1> Quote of the Day</h1>
      <div>
        <h5>{quoteOfDay.quote}</h5>
        <h6>{quoteOfDay.author}</h6>
        <hr />
      </div>
    </div>
  );
}

export default HomePage;

```

##  Revisit  -> Quotes page & Author page

### Add the form to search for quote based on Author

Add a form to the QuotesPage to implement the search by Author functionality


``` javascript
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

``` javascript 
authors.map(author=>(<p>
              <Link to='/quote'>{author}</Link>
              </p>))
```

<hr/>
[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-102) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-102b) 
