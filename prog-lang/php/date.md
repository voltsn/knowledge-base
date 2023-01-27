The  `date` function returns a string formatted according to the specified format string of the provided timestamp. By default the timestamp is set to the value of `time()`. 

> Unix timestamps do not handle timezones. [DateTimeImmutable](https://www.php.net/manual/en/class.datetimeimmutable.php) is more appropriate for this task.

```PHP
$today = date("m.d.y"); // 03.10.01
```