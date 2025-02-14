# React Tutorials - Quotes App - 105 ---> Implementing CRUD operation 

## Implementing Add Quotes

### Add new component 

- Create a new component `AddQuote.jsx` under the `quote` folder
- Move the `Quote.jsx` file under the `quote` folder
- Add the below html code for generating the quote form


``` html
<>
      <form className="border border-dark border-3 rounded m-2 p-2">
        <div className="mb-3">
          <label for="inputQuote" className="form-label">
            Quote
          </label>
          <textarea
            className="form-control"
            id="inputQuote"
            rows="3"
          ></textarea>
        </div>
        <div className="mb-3">
          <label for="inputAuthorName" className="form-label">
            Author Name
          </label>
          <input
            type="text"
            className="form-control"
            id="inputAuthorName"
            placeholder="Author Name"
          />
        </div>
        <div className="mb-3">
          <label for="inputTags" className="form-label">
           Tags
          </label>
          <input
            type="text"
            className="form-control"
            id="inputTags"
            placeholder="Tags Seperated by semicolon"
          />
        </div>
        <div className="col-auto">
          <button type="submit" className="btn btn-primary mb-3">
           Add Quote
          </button>
        </div>
      </form>
    </>
```

- Enable the visibilty of the form by adding a new state in `QuotePage.jsx`

``` javascript
  const [showAddForm,setShowAddForm]=useState(false)
```

- Add the button `Add new Quote` to the side of the Search button

``` html
     <button
            type="button"
            className="btn btn-success border border-dark border-3 rounded"
            onClick={toggleAddQuote}
          >
            Add New Quote
          </button>
```

- Toggle the value of `showAddForm` once the form is clicked

``` javascript
  const toggleAddQuote=(e)=>{
    setShowAddForm(!showAddForm)
  }
```

### Add Quote Component

Create a function `handleChange` and link it to quote,author and tags field.

``` javascript
 const handleChange = (e) => {
    const { name, value } = e.target;
    switch (name) {
      case 'quote':
        setQuoteItem({ ...quoteItem, quote: value });
        if (value.length < 50) {
          setErrorMessage('Quote must be minimum 50 characters in length.');
        } else setErrorMessage(null);
        break;
      case 'author':
        setQuoteItem({ ...quoteItem, author: value });
        break;
      case 'tags':
        setQuoteItem({ ...quoteItem, tags: value });
        break;
      default:
        break;
    }
  };
```

Create a function `handleSubmit` which will be linked to the form. 

``` javascript
  const handleSubmit = (e) => {
    e.preventDefault();
    onAddQuote(quoteItem);
  };
```

The function `onAddQuote` is a prop that is passed to the **AddQuote** component from the **QuotePage** component

``` javascript
function AddQuote({ onAddQuote }) {
}
```

add function addQuote `Quote.service.js`

``` javascript
export async function addQuote(newQuote){
    const response = await quotesApi.post('/quote',newQuote);
    return response.data;
}
```
