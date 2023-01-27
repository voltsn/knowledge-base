User input is an important process of backend development
When dealing with external data, sanitizing and validating it is non-negociable for security purposes.

## Sanitze Filters
PHP puts to our disposal a number of [filters](https://www.php.net/manual/en/filter.filters.sanitize.php) that allows us to sanitize external data.

## filter_input
This function gets an external variable by name and optionally filters it.

On success the returned value is the value of the requested variable, `FALSE` is returned if variable is not set, or `NULL` if the filter fails 

```PHP
if (isset($_GET['term'])) {
    $term = filter_var($_GET['term'], FILTER_SANITIZE_SPECIAL_CHARS);
    var_dump($term);
}
```

## filter_var
`filter_var` filters a variable with a specified filter, it returns the filtered data or `FALSE` if the filter fails

```PHP
if (isset($_GET['term'])) {
    $term = filter_var($_GET['term'], FILTER_SANITIZE_SPECIAL_CHARS);
    var_dump($term);
}
```