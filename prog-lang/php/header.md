`header()` is used to send a raw HTTP header, it must be called before any output is sent such as HTML tags, blank lines in a file or from PHP. There are two special case header calls for the _header_ string:
- `HTTP/` (case is not significant) will be used to determine the HTTP status code to send.
- `Location` in addition to sending a header back to the browser is also reutrns a _REDIRECT_ (302) status code to the browser unless the 201 or 3xx code has already been set.

[Official documentation](https://www.php.net/manual/en/function.header.php)

```PHP
// We'll be outputting a PDF
header('Content-Type: application/pdf');

// It will be called downloaded.pdf
header('Content-Disposition: attachment; filename="downloaded.pdf"');

// The PDF source is in original.pdf
readfile('original.pdf');
```