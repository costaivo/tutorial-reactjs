# React Tutorials - Quotes App - 103 --- > Passing Data between Components

## Fixing the Errors in console

Open the **Quotes App** in the browser, and review all the error messages in the **Console** tab

<span style='color:red'>
 Warning: Each child in a list should have a unique <strong>key</strong> prop.<br/>
 
Check the render method of `AuthorPage`. See https://reactjs.org/link/warning-keys for more information.
</span>

The above error occurs, since each rendered element in a loop should have a unique value set to the **key** attribute

### Fixing Author Page
 - Set the **key** attribute on the  **p** tag to author name
 
 ``` javascript
   return (
    <div className='container m-5 p-5'>
        {
            authors.map(author=>(<p key={author}>
              <Link to='/quote'>{author}</Link>
              </p>))
        }
    </div>
  )
 ```

 ### Fixing the Quotes Page
 - set the **key** attritube on the parent **div** tag inside the map function to `quote._id` field

``` javascript
   {quotes.map((quote) => (
        <div className='m-2' key={quote._id}>
          <h5>{quote.quote}</h5>
          <h6>{quote.author}</h6>
          <hr />
        </div>
      ))}
```

## Fixing Duplicate Code. DRY - Don't Repeat yourself

The Home Page and the Quotes Page is using the same code to render the **Quote**, this duplicate code can be reduced by creating a seperate component for **Quote Item**

### Creating Quote Component

- Add a new file `Quote.jsx` under the folder **components**
- Remove the code rendering the quote and paste it in the `Quote.jsx` file
- add the props as input paramter to the `Quote.jsx` functional component

``` javascript
  function Quote(props) {
    const {quote} = props
      return (
        <div>
          <div className="m-2" >
            <h5>{quote.quote}</h5>
            <h6>{quote.author}</h6>
            <hr />
          </div>
        </div>
      );
}

export default Quote;

```

- remove the attribute `key={quote._id}` since it is not required in the Quote component 
- add the Quote component element in place of the original code `QuotePage.jsx`  

``` javascript
     {quotes.map((quote) => (
          <Quote quote={quote} key={quote._id}/>
      ))}
```
- add the Quote Component in the `HomePage.jsx`

``` html
    <Quote quote={quoteOfDay} />
```

## Linking Author to Quotes Page

## Add the route for capturing params in the url

- open the `App.js` file and add a new route that can accept the author name

``` javascript
  <Route path="/quote/:author" element={<QuotePage />} />
```

- edit the `AuthorPage.jsx` to send the author name when the user clicks on the link 

``` javascript
   <Link to={`/quote/${author}`}>{author}</Link>
```

## Read Route Params on Quotes Page

let's start using our first react hook. To get the request parameters, we have to use the `useParams` hook
using the below code snippet we can filter the quotes based on the author's name

``` javascript 
  const params = useParams()
  console.log(params)
  if(params.author && params.author!=='')
  {
    console.log(quotes)
    quotes =  quotes.filter((x)=>(x.author === params.author))
    console.log(quotes)
  }

```

## Implement Search functionality

In this section we will start using **useState** hook. In order to maintain the data in a react application we need to use a store, useState provides us that feature. Whenever the value of the state variable changes, React will automatically re-render the componet. 


``` javascript
 const [searchAuthor,SetSearchAuthor] = useState('')
```

Set the value of input field to **searchAuthor**

``` javascript
       <input
            type="text"
            className="form-control"
            placeholder="Author Name"
            value={searchAuthor}
          />
```

Add a function **handleOnChange** and link it to **onChange** event

``` javascript
 const handleOnChange=(e)=>{
    e.preventDefault()
    setSearchAuthor(e.target.value)
  }
```

Refactor the code, move all the code related to filtering in a function 

``` javascript
const getFilteredQuotes=(author)=>{
    if(author && author!=='')
    {
      quotes =  quotes.filter((x)=>(x.author === author))
      console.log('The filtered quote list',quotes)
    }
  }
```

Wrapper function to invoke getFilteredQuotes.
``` javascript
  const loadQuotes =()=>{
    getFilteredQuotes(params.author)
  }
```

``` javascript
  const handleSubmit=(e)=>{
    e.preventDefault()
    getFilteredQuotes(searchAuthor)
  }
```


### using `useEffect` hook

we need the **useEffect** hook to load the quotes on inital load of the QuotePage component.

``` javascript

  useEffect(() => {
    console.log('UseEffect Called')
    loadQuotes()
  },[])
```


now the entire application is funcitally working. But it still needs to be hooked to pull the data from the api endpoints. we will work on implementing it next. 

<hr/>

[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-102b) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-104) 
