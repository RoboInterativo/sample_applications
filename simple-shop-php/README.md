#Ссылки

```php

<?php
$result = $pdo->query("SELECT id, name FROM employees");
while (list($id, $name) = $result->fetch(PDO::FETCH_NUM)) {
    echo "id: $id, name: $name\n";
}
?>

```

https://www.php.net/manual/en/function.list.php
