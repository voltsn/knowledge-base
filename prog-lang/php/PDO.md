- [Database Connection](#database-connection)
- [Query](#query) 
- [Prepare](#prepare) 
- [Execute](#execute)

`PDO` or *PHP Data Objects* defines a lightweight, consistent interface for accessing databases in PHP.

>In order to perform actions on a database, we have to use a database-specific [PDO driver](https://www.php.net/manual/en/pdo.drivers.php). 

# Database connection

```PHP 
$dbhost = $_SERVER["SERVER_NAME"];
$dbname = "becode";
$dbuser = "segfault";
$dbpassword = "";

try {
	// Connect to the database
	$db_conn = new PDO("mysql:host=$dbhost; dbname=$dbname", $dbuser, $dbpassword);
	} catch (PDOException $e) {
	$db_conn = NULL;
}
```

# Query
With `PDO`, we can query a database by using the `query` function. It prepares and executes a SQL statement without placeholders, a `PDOStatement` object is returned or `FALSE` on failure.
```PHP
$sql = 'SELECT name, color, calories FROM fruit ORDER BY name';
foreach ($db_conn->query($sql) as $row) {   
	print $row['name'] . "\t";
	print $row['color'] . "\t";  
	print $row['calories'] . "\n";   
}
```

# Prepare
`PDO::prepare` prepares a SQL statement for execution and returns a statement object. The statement template can contain 0 or more named or question mark parameters which will be substitued with real values when the stament gets excuted.

> Named and question mark parameters cannot be used within the same statement template.

```PHP
/* Execute a prepared statement by passing an array of values */
$sql = 'SELECT name, colour, calories
    FROM fruit
    WHERE calories < :calories AND colour = :colour';
$sth = $dbh->prepare($sql, [PDO::ATTR_CURSOR => PDO::CURSOR_FWDONLY]);
$sth->execute(['calories' => 150, 'colour' => 'red']);
$red = $sth->fetchAll();
/* Array keys can be prefixed with colons ":" too (optional) */
$sth->execute([':calories' => 175, ':colour' => 'yellow']);
$yellow = $sth->fetchAll();
```

# Execute
`PDOStatment::execute` executes a prepared statement, it takes as a parameter an array of values with the same number of parameters in the SQL statement being executed. Returns `TRUE` or `FALSE`.

```PHP
$calories = 150;
$colour = 'red';
$sth = $dbh->prepare('SELECT name, colour, calories
    FROM fruit
    WHERE calories < ? AND colour = ?');
$sth->execute(array($calories, $colour));
```