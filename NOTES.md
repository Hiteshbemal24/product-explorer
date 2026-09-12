# Notes

> Fill this in as you work. This document is assessed alongside your code.

## Bugs I found

1. Products were being fetched multiple times
The products state was included in the useEffect dependency array, while the same effect was also updating that state. This caused the API request to run again whenever the products changed. I removed products from the dependency array so the products are fetched only when the component mounts.

2. any was being used for the product data
The product state and API response were using any. Since the project already had a Product interface, I used that instead to keep the types consistent.

3. Array index was used as the React key
The product list was using the array index as the key. Since the list can change when filtering, the index isn't a reliable identifier. I changed it to use the product id.

4. Search and category filters weren't working together
When a category was selected, the search filter was effectively ignored. I updated the filtering logic so that the product has to match both the selected category and the search text.

5. Search was case-sensitive
Searching only worked when the casing matched the product title. I normalized both the search value and product title before comparing them, so searches now work regardless of capitalization.

## Features I completed

- Added an API error state so users can see when loading products fails.
- Added an open/close animation for the product details modal.

## Decisions

- I kept the existing component structure because the project was already split into reasonable components. I didn't feel a restructure was necessary for these changes.
- I used the existing Product interface instead of adding another library or introducing separate validation just for this task.

## With more time

- Add a retry button when the API request fails.
- Improve the modal's accessibility, especially keyboard support and focus handling.
- Add tests covering different search and category filter combinations.
