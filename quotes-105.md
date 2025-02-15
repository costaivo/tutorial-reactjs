# React Tutorials - Quotes App -105- Search and Filter

## Introduction

In this section, we'll add search functionality to filter quotes by author. We'll create reusable components and follow best practices for state management and error handling.

## Prerequisites

- Completed [Quotes-104](/tutorial-reactjs/quotes-104)
- Understanding of React hooks (useState, useEffect)
- Familiarity with TypeScript and React Router

## Step-by-Step Instructions

### 1. Create the Search Form Component

Create a new file `src/components/SearchForm.tsx`. This component will handle the search input and form submission:

```tsx
import { useState, ChangeEvent, FormEvent } from 'react';

interface SearchFormProps {
  onSearch: (author: string) => void;
  initialValue?: string;
  placeholder?: string;
  isLoading?: boolean;
}

export default function SearchForm({ 
  onSearch, 
  initialValue = '', 
  placeholder = 'Author Name',
  isLoading = false
}: SearchFormProps) {
  const [searchTerm, setSearchTerm] = useState<string>(initialValue);

  const handleSubmit = (e: FormEvent<HTMLFormElement>) => {
    e.preventDefault();
    onSearch(searchTerm);
  };

  return (
    <form onSubmit={handleSubmit} className="row m-3">
      <div className="input-group">
        <span className="input-group-text">Search by Author</span>
        <input 
          type="text" 
          className="form-control" 
          placeholder={placeholder}
          value={searchTerm}
          onChange={(e) => setSearchTerm(e.target.value)}
          disabled={isLoading}
        />
        <button 
          type="submit" 
          className="btn btn-primary"
          disabled={isLoading}
        >
          {isLoading ? 'Searching...' : 'Search'}
        </button>
      </div>
    </form>
  );
}
```

### 2. Create a Loading Spinner Component

Create `src/components/LoadingSpinner.tsx` for showing loading states:

```tsx
interface LoadingSpinnerProps {
  size?: 'sm' | 'md' | 'lg';
  color?: string;
}

export default function LoadingSpinner({ 
  size = 'md',
  color = 'primary'
}: LoadingSpinnerProps) {
  const sizeClass = size === 'lg' ? 'spinner-border-lg' : 
                    size === 'sm' ? '' : 'spinner-border-md';

  return (
    <div className="text-center mt-4">
      <div 
        className={`spinner-border text-${color} ${sizeClass}`} 
        role="status"
      >
        <span className="visually-hidden">Loading...</span>
      </div>
    </div>
  );
}
```

### 3. Update the Quotes Page

Update `src/pages/QuotesPage.tsx` to implement the search functionality:

```tsx
import { useState, useEffect } from 'react';
import { useSearchParams } from 'react-router-dom';
import Quote from '../components/Quote';
import SearchForm from '../components/SearchForm';
import LoadingSpinner from '../components/LoadingSpinner';
import { Quote as QuoteType } from '../types';

export default function QuotesPage() {
  const [searchParams, setSearchParams] = useSearchParams();
  const [quotes, setQuotes] = useState<QuoteType[]>([]);
  const [isLoading, setIsLoading] = useState(false);
  const [error, setError] = useState<string | null>(null);
  
  const authorParam = searchParams.get('author') || '';

  // Add initial quotes loading
  useEffect(() => {
    const loadQuotes = async () => {
      setIsLoading(true);
      try {
        // This would typically be an API call
        const initialQuotes: QuoteType[] = [
          { _id: '1', text: 'Be yourself; everyone else is already taken.', author: 'Oscar Wilde' },
          { _id: '2', text: 'Two things are infinite: the universe and human stupidity; and I\'m not sure about the universe.', author: 'Albert Einstein' },
          { _id: '3', text: 'So many books, so little time.', author: 'Frank Zappa' },
          { _id: '4', text: 'Be the change that you wish to see in the world.', author: 'Mahatma Gandhi' },
        ];
        setQuotes(initialQuotes);
        
        // If there's an initial author parameter, filter immediately
        if (authorParam) {
          handleSearch(authorParam);
        }
      } catch (err) {
        setError('Failed to load quotes. Please try again.');
      } finally {
        setIsLoading(false);
      }
    };

    loadQuotes();
  }, []); // Run once on component mount

  const handleSearch = async (searchAuthor: string) => {
    setError(null);
    setIsLoading(true);
    
    try {
      // Update URL parameters
      setSearchParams(searchAuthor ? { author: searchAuthor } : {});
      
      // Filter quotes (we'll replace this with an API call later)
      const filtered = searchAuthor.trim()
        ? quotes.filter(quote => 
            quote.author.toLowerCase().includes(searchAuthor.toLowerCase())
          )
        : quotes;
      
      if (filtered.length === 0) {
        setError('No quotes found for this author.');
      }
      
      setQuotes(filtered);
    } catch (err) {
      setError('Failed to filter quotes. Please try again.');
    } finally {
      setIsLoading(false);
    }
  };

  return (
    <div className="container mt-4">
      <h1>All Quotes</h1>
      
      <SearchForm 
        onSearch={handleSearch} 
        initialValue={authorParam}
        isLoading={isLoading}
      />
      
      {error && (
        <div className="alert alert-danger mt-3" role="alert">
          {error}
        </div>
      )}
      
      {isLoading ? (
        <LoadingSpinner />
      ) : (
        <div className="quotes-container mt-3">
          {quotes.map((quote) => (
            <Quote key={quote._id} quote={quote} />
          ))}
        </div>
      )}
    </div>
  );
}
```

## Testing Your Implementation

1. Start your development server
2. Navigate to the Quotes page
3. Try searching for an author:
   - Enter a name in the search box
   - Verify the URL updates with the search parameter
   - Check that the loading spinner appears
   - Confirm filtered results are displayed
4. Test error cases:
   - Search for a non-existent author
   - Verify error message appears
   - Clear the search and confirm all quotes return

## Next Steps

In the next tutorial, we'll:
- Connect to a real API for searching
- Add pagination
- Implement search history

[<< Previous](/tutorial-reactjs/quotes-104) | [Index](/tutorial-reactjs/) | [Next >>](/tutorial-reactjs/quotes-106)
