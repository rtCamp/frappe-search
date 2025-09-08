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

- Install the app in your Frappe site:
  ```bash
  bench get-app https://github.com/rtCamp/frappe-search
  bench --site your-site install-app frappe_search
  ```
- Call the search endpoint:
  ```
  frappe_search.api.search.get_global_search_results
  ```
  - Parameters:
      - `text` (str): The text to search for.
      - `doctype` (str, optional): Doctype to search within.
      - `limit` (int, optional): Maximum number of results to return. Default is 20.
      - `start` (int, optional): The starting index for pagination. Default is 0.
      - `allowed_doctypes` (list, optional): List of doctypes to search within.
- Get the search results in an array of dictionaries format alongside a boolean indicating if further results are possible.

### Demo response

### Demo response

```Python
[
  [
    {
      "name": "k5sm76en7o",
      "doctype": "ToDo",
      "content": "Name: k5sm76en7o <br> Allocated To : rtCamp.goodwork@rtcamp.com <br> Description : Some description here.",
      "rank": 1,
      "score": 350,
      "marked_string": "...<br> Allocated To : <mark>rtCamp</mark>.goodwork@rtcamp.com <br>...",
      "full_marked_string": "Name: k5sm76en7o <br> Status : Open <br> Allocated To : <mark>aryan</mark>.kaushik@rtcamp.com <br> Description : Some description here.:",
      "title": "Good Work. Good People",
    }
  ],
  true
]
```
