Checks if all of the characters in the string are for alphanumeric character(s). 
Returns `true` if every character is a letter or a digit, `false` otherwise. Empty string are always `false`.

```PHP
$strings = array('AbCd1zyZ9', 'foo!#$bar');
foreach ($strings as $testcase) {
    if (ctype_alnum($testcase)) {
        echo "The string $testcase consists of all letters or digits.\n";
    } else {
        echo "The string $testcase does not consist of all letters or digits.\n";
    }
}
```