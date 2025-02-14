# React Tutorials - Quotes App -105- Search and Filter

## Introduction

In this section, we'll enhance our Quotes application by adding search and filter functionality. We'll follow the DRY (Don't Repeat Yourself) principle to create reusable components and implement a search feature that allows users to filter quotes by author.

## Prerequisites

- Completed [Quotes-104](/tutorial-reactjs/quotes-104)
- Understanding of React hooks (useState, useEffect)
- Familiarity with TypeScript and React Router

## What We'll Build

1. A reusable search form component
2. Author-based quote filtering
3. Loading states and error handling
4. URL parameter integration

## Step 1: Creating the Search Form Component

First, let's create a reusable search form component that we can use across our application.

### Create src/components/SearchForm.tsx

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

  const handleChange = (e: ChangeEvent<HTMLInputElement>) => {
    setSearchTerm(e.target.value);
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
          onChange={handleChange}
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

## Step 2: Implementing the Quotes Page

Update the Quotes page to include search functionality and handle loading states.

### Update src/pages/QuotesPage.tsx

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

  const handleSearch = async (searchAuthor: string) => {
    setError(null);
    setIsLoading(true);
    
    try {
      // Update URL with search parameter
      setSearchParams(searchAuthor ? { author: searchAuthor } : {});
      
      // Filter quotes (will be replaced with API call later)
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
      console.error('Search error:', err);
    } finally {
      setIsLoading(false);
    }
  };

  // Initial load of quotes
  useEffect(() => {
    if (authorParam) {
      handleSearch(authorParam);
    }
  }, []);

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

## Step 3: Adding a Loading Spinner Component

Create a reusable loading spinner component.

### Create src/components/LoadingSpinner.tsx

```tsx
interface LoadingSpinnerProps {
  size?: 'sm' | 'md' | 'lg';
  color?: string;
}

export default function LoadingSpinner({ 
  size = 'md',
  color = 'primary'
}: LoadingSpinnerProps) {
  const sizeClass = {
    sm: '',
    md: 'spinner-border-md',
    lg: 'spinner-border-lg'
  }[size];

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

## Key Features Implemented

1. **Reusable Search Form**
   - Accepts initial value and custom placeholder
   - Handles form submission and input changes
   - Provides clean interface through props
   - Supports loading state with disabled inputs

2. **URL Parameter Integration**
   - Search terms are reflected in URL
   - Enables bookmarking and sharing of search results
   - Maintains search state on page refresh

3. **Loading and Error States**
   - Shows loading spinner during filtering
   - Displays user-friendly error messages
   - Handles edge cases gracefully
   - Includes error logging

4. **Responsive Design**
   - Works well on all screen sizes
   - Uses Bootstrap classes for consistent styling
   - Maintains accessibility
   - Provides visual feedback during loading

## Common Issues and Solutions

1. **Search Not Updating URL**
   - Make sure to use `setSearchParams` correctly
   - Check that the router is properly configured

2. **Loading State Issues**
   - Verify `isLoading` state is being passed to components
   - Ensure proper error handling in async functions

3. **Type Errors**
   - Import and use proper TypeScript interfaces
   - Use specific event types for handlers

## What's Next

In the next tutorial, we'll:

- Connect the search functionality to a real API
- Implement debounced search for better performance
- Add pagination for large result sets
- Enhance error handling with retry mechanisms
- Add search history functionality

---

[<< Previous](/tutorial-reactjs/quotes-104) | [Index](/tutorial-reactjs/) | [Next >>](/tutorial-reactjs/quotes-106)
