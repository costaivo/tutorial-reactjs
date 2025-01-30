# React Tutorials - Quotes App - 104b --- > Custom Hook
===old
## Creating a Custom Hook

Let's create a custom hook to save data to the localstorage, since we would be using this very often.

- Create a folder `hooks` under `src` folder
- Create a new file `useLocalStorage.js` under `hooks` folder.
- Create a customHook using the **rfce** code snippet generator
- The custom Hook won't be returning an HTML, instead we will return the **value** and the **setValue** function

``` javascript
function useLocalStorage() {
  const [value,setValue] = useState() 

  const setValue()=>{

  }
  return [value,setValue]
}

export default useLocalStorage
```

- Rename the variable **value --> storeValue** and function name **setValue --> setStoreValue**
- We need to pass two parameters to the hook
  - key --> the key of the localstorage
  - initialValue --> the initial value for the key
- Let's write the logic to pull data from the localstorage if it already exists

``` javascript
import  { useState } from 'react';

function useLocalStorage(key, initialValue) {
  const [storeValue, setStoreValue] = useState(() =>
    getValueFromLocalStorage(key, initialValue));

  const setValue=(data) =>{
  }

  return [storeValue,setValue]
}

function getValueFromLocalStorage(key, inititalValue) {
  const valueFromStore = localStorage.getItem(key);
  // Return value if found in localstore else return the initial value
  return valueFromStore ? JSON.parse(valueFromStore) : inititalValue;
}

export default useLocalStorage;
```

Add the logic to update the localStorage

``` javascript
  const setValue=(data) =>{
      const valueToStore = data instanceof Function ? data(storeValue):data
      setStoreValue(data)
      localStorage.setItem(key,JSON.stringify(valueToStore))
  }
```

### Updating code to use the hook

A custom hook can be invoked, just like how inbuilt hooks are used. 
Below is the complete code after using the hook instead of localstorage

``` javascript
import Quote from '../components/Quote';
import { useState, useEffect } from 'react';
import { getQuotes } from '../services/Quote.service';
import useLocalStorage from '../hooks/useLocalStorage';

const LocalStorageKeys = {
  QUOTE_OF_D_DAY: 'QuoteOfTheDay',
  QUOTE_DATE: 'QUOTE_DATE',
};
function HomePage() {
  const [quoteOfDay, setQuoteOfDay] = useState({});
  const [storeQuoteDate, setStoreQuoteDate] = useLocalStorage(
    LocalStorageKeys.QUOTE_DATE,
    ''
  );
  const [storeQuote, setStoreQuote] = useLocalStorage(
    LocalStorageKeys.QUOTE_OF_D_DAY,
    null
  );

  const setRandomQuote = async (date) => {
    const allQuotes = await getQuotes();
    const randomNumer = Math.floor(Math.random(allQuotes.length) * 10);
    setStoreQuote(allQuotes[randomNumer]);
    setStoreQuoteDate(date);
    setQuoteOfDay(allQuotes[randomNumer]);
  };

  const getRandomQuote = async () => {
    const current = new Date();
    const todayDate = `${current.getFullYear()}-${current.getMonth()+1}-${current.getDate()}`;
    if (storeQuoteDate && storeQuoteDate !== todayDate) {
      setStoreQuoteDate(null);
      setStoreQuote(null);
    }

    storeQuote ? setQuoteOfDay(storeQuote) : setRandomQuote(todayDate);
  };

  useEffect(() => {
    getRandomQuote();
  }, []);

  return (
    <div className="container">
      <h1 className="m-3"> Quote of the Day</h1>
      <Quote quote={quoteOfDay} />
    </div>
  );
}

export default HomePage;

```
<hr/>

[<< Previous](https://costaivo.com/tutorial-reactjs/quotes-104) |  [Index](https://costaivo.com/tutorial-reactjs) |  [Next>>](https://costaivo.com/tutorial-reactjs/quotes-105) 
