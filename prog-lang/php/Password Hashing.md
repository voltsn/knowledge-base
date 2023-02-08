- [Password Hashing Functions](#password-hashing-functions)
	- [`password_algos`](#password_algos)
	- [`password_get_info`](#password_get_info)
	- [`password_hash`](#password_hash)
	- [`password_needs_rehash`](#password_needs_rehash)
	- [`password_verify`](#password_verify)

[Documentation](https://www.php.net/manual/en/book.password.php)

The password hashing api provides an easy to use wrapper around [`crypt()`](https://www.php.net/manual/en/function.crypt.php) and some other password hashing algorithms, that make it easy to create and manage passwords securely.

# Password Hashing Functions

## `password_algos`
Returns a complete list of all available password hashing algorithms IDs as an array of strings.

```PHP
print_r(password_algos());
```

## `password_get_info`
Returns information about a given hash in the form of an associative array with three elements:
- _algo_, will match a password algorithm constant
- _algoName_, has the human readable name of the algorithm
- _options_, contains the options provided when calling `password_hash`

```PHP
 password_get_info(string $hash): array
```

## `password_hash` 
Creates a password hash using a strong one-way hashing algorithm, the supported algoriths are: 
- **PASSWORD_DEFAULT**, uses the _brypt_ algorithm as of PHP 5.5.0
- **PASSWORD_BRCRYPT**, uses the **CRYPT_BLOWFISH** algorithm
- **PASSWORD_ARGON2i**, uses the _Argon2i_ hashing algorithm, ==only available when PHP has been compiled with Argon2 support==
- **PASSWORD_ARGON2ID**, uses the _Argon2id_ hashing algorithm, ==only available when PHP has been compiled with Argon2 support== 
Returns the hashed password aswell as the algorithm, cost and the salt.

```PHP
echo password_hash("rasmuslerdorf", PASSWORD_DEFAULT);
```

## `pasword_needs_rehash`
Checks to see if the supplied hash implements the algorithm and options provided, if not, it is assumend that the hash needs to be rehashed. It returns `TRUE` if the hash should be reshashed to match the given `algo` and `options` parameters or `FALSE` otherwise.

```PHP
$password = 'rasmuslerdorf';
$hash = '$2y$10$YCFsG6elYca568hBi2pZ0.3LDL5wjgxct1N8w/oLR/jfHsiQwCqTS';

// The cost parameter can change over time as hardware improves
$options = array('cost' => 11);

// Verify stored hash against plain-text password
if (password_verify($password, $hash)) {
    // Check if a newer hashing algorithm is available
    // or the cost has changed
    if (password_needs_rehash($hash, PASSWORD_DEFAULT, $options)) {
        // If so, create a new hash, and replace the old one
        $newHash = password_hash($password, PASSWORD_DEFAULT, $options);
    }

    // Log user in
}
```

## `password_verify`
Verifies that the given hash matches the given password. This function is compatible with `crypt()` meaning that password hashes created by `crypt()` can be used with it. Returns `TRUE` if the password and hash match, `FALSE` otherwise.

```PHP
$hash = '$2y$07$BCryptRequires22Chrcte/VlQH0piJtjXl.0t1XkA8pw9dMXTpOq';

if (password_verify('rasmuslerdorf', $hash)) {
    echo 'Password is valid!';
} else {
    echo 'Invalid password.';
}
```