## Frappe Search

Frappe Search enables powerful, global search functionality across your custom Frappe apps.

It utilises full-text search capabilities (MariaDB Match) along with Fuzzy Search to provide fast and relevant search results.

The core search functionality is inspired from Frappe's built in search but rebuilds the JS side logic in Python for quick use with any app just by calling the search endpoint and also allows per app basis allowed DocTypes list change.

### Features

- Fast, full-text search across multiple DocTypes
- Seamless integration with Frappe's permission system
- Easy setup and usage
- Match terms highlighting in results
- Supports pagination and result limits
- Uses Redis for caching search results

### Getting Started

1. Install the app in your Frappe site:
  ```bash
  bench get-app https://github.com/rtCamp/frappe-search
  bench --site your-site install-app frappe_search
  ```
2. Call the search endpoint:
  ```
  frappe_search.api.search.get_global_search_results
  ```
3. Get the search results in an array of dictionaries format alongside a boolean indicating if further results are possible.

### Parameters

1. `search_text` (str): The text to search for.
2. `doctype` (str, optional): Doctype to search within.
3. `limit` (int, optional): Maximum number of results to return. Default is 20.
4. `start` (int, optional): The starting index for pagination. Default is 0.
5. `allowed_doctypes` (list, optional): List of doctypes to search within.