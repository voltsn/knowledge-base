`intval` returns the int value of __argument__, using the specified __base__ for the conversion by default its base 10 or 0 on failure, Empty arrays return 0 and non empty arrays return 1.


> `intval` should not be used on objects.

```PHP
 intval(mixed $value, int $base = 10): int
```