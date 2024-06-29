# TaintedSql

Emitted when user-controlled input can be passed into a SQL command.

```php
<?php

class A {
    public function deleteUser(PDO $pdo) : void {
        $userId = self::getUserId();
        $pdo->exec("delete from users where user_id = " . $userId);
    }

    public static function getUserId() : string {
        return (string) $_GET["user_id"];
    }
}
```

N.B. In order for the PDO sink to be enabled you will need to have the PDO extension enabled either via the pslam.xml config or having the PHP PDO extension in you composer.json.
