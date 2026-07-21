# postman-tests

Postman collection tests for API testing.

## Structure

```
collections/    # Postman collection JSON files
```

## Running Tests

Import the collection files from the `collections/` folder into Postman, or run them via [Newman](https://github.com/postmanlabs/newman):

```bash
newman run collections/<collection-name>.json
```
