
# React Tutorials - Quotes App - 104 --- > Fetching Data from API
===old
## Installing Axios

to call external api's we will be using axios, to install axios use the below command

``` cmd
  npm i axios
```


## Creating a service

create a new file `quotes.service.js` under the **services** folder
Add methods to call the API endpoints
- **getAuthors** --> Get the list of Authors
- **getQuotes** --> Get the list of Quotes
- **getQuotesByAuthor** --> Get Quotes filtered by Author Name


``` javascript
import axios from 'axios'


export async function getAuthors(){
    const quotesApi = axios.create({
        baseURL:'https://quote-api-app.herokuapp.com'
    })
    const response = await quotesApi.get('/author');
    return response.data;
}

export async function getQuotes(){
    const quotesApi = axios.create({
        baseURL:'https://quote-api-app.herokuapp.com'
    })
    const response = await quotesApi.get('/quote');
    return response.data;
}

export async function getQuotesByAuthor(authorName){
    const quotesApi = axios.create({
        baseURL:'https://quote-api-app.herokuapp.com'
    })
    const response = await quotesApi.get(`/quote/search?author=${authorName}`);
    return response.data;
}
```



The AuthorPage.jsx code should look 
``` javascript
  const [authors, setAuthors] = useState([]);

  const loadData = async () => {
    const data = await getAuthors();
    setAuthors(data);
  };

  useEffect(() => {
    loadData();
  }, []);
```

**TODO : Assignment**
In the **QuotesPage** remove the reference to the `all_quotes` variable and add call to the service methods at appropriate places. **Note:** API functions are **async** in nature, so make the necessary changes at time of invocation. 

## Fixing the Nav Links

Currently whenever we click on the navigation, the selected menu item is not shown as selected.
To fix this we have to we can use custom logic or use **NavLink** component available in reactjs

In the `App.js` file replace the **Link** element with **NavLink** and set the attribute *activeClassName** to the value of the class. that will keep the nav item active

``` html
 <NavLink className="nav-link"  to='/'>Home</NavLink>
```

## Implementing the logic to generate Random Quote of the Day

First let's implement the logic to get a random quote for the day. Later we will add the logic to make sure that the same random quote is shown throughout the day. 


``` javascript
 const [quoteOfDay,setQuoteOfDay] = useState({}) 

 const getRandomQuote = async()=>{
  const allQuotes = await  getQuotes()
  const randomNumer = Math.floor(Math.random(allQuotes.length)*10)
  setQuoteOfDay(allQuotes[randomNumer])
 }
 useEffect(() => {
  getRandomQuote()
 }, [])

```

To implement the logic for the quote to be same for the day, we will have to use local storage. 
Below is the complete code snippet of the QuoteOfTheDay logic

``` javascript

const LocalStorageKeys = {
  QUOTE_OF_D_DAY:'QuoteOfTheDay',
  QUOTE_DATE:'QUOTE_DATE',
  PAST_10_QUOTES:'PAST_10_QUOTES'
} 
function HomePage() {
    const [quoteOfDay, setQuoteOfDay] = useState({});

    const getRandomQuote = async () => {
    const current = new Date()
    const todayDate =`${current.getFullYear()}-${current.getMonth()}-${current.getDate()}`
    const storedDate = localStorage.getItem(LocalStorageKeys.QUOTE_DATE)

    if(storedDate && storedDate !== todayDate)
    {
      console.log('clearing localStorage')
      localStorage.removeItem(LocalStorageKeys.QUOTE_OF_D_DAY)
      localStorage.removeItem(LocalStorageKeys.QUOTE_DATE)
    }

    if (localStorage.getItem(LocalStorageKeys.QUOTE_OF_D_DAY)) {
      const quote = JSON.parse(localStorage.getItem(LocalStorageKeys.QUOTE_OF_D_DAY));
      setQuoteOfDay(quote);
      return;
    }

    const allQuotes = await getQuotes();
    const randomNumer = Math.floor(Math.random(allQuotes.length) * 10);
    localStorage.setItem(LocalStorageKeys.QUOTE_OF_D_DAY, JSON.stringify(allQuotes[randomNumer]));
    localStorage.setItem(LocalStorageKeys.QUOTE_DATE,todayDate)
    
    setQuoteOfDay(allQuotes[randomNumer]);
    
  };

  useEffect(() => {
    getRandomQuote();
  }, []);
```

## Service Refactoring

The `Quote.service.js` file is refering to the external API URL at multiple times, lets refactor the code to fix this. 

``` javascript
import axios from 'axios'

const quotesApi = axios.create({
    baseURL:'https://quote-api-app.herokuapp.com'
})

export async function getAuthors(){
    const response = await quotesApi.get('/author');
    return response.data;
}

export async function getQuotes(){
    const response = await quotesApi.get('/quote');
    return response.data;
}

export async function getQuotesByAuthor(authorName){
    const response = await quotesApi.get(`/quote/search?author=${authorName}`);
    return response.data;
}
```

## Breaking into smaller components

### Creating the Navigation Component

- Create a new component `Header.jsx` `under components\layouts folder`
- Move the code from `App.js` related to the navigation menu into the new component


### Creating the Footer Component
- Create a new component `Footer.jsx` `under components\layouts folder`
- Add the below code for the footer

``` javascript
function Footer() {
  return (
    <footer className="footer mt-auto py-3 bg-light">
      <div className="container">
      <span class="text-muted">Quotes App © 2022</span>
      </div>
    </footer>
  );
}

export default Footer;
```

<hr/>

[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-103) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-104b) 
