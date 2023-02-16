# `Database`

## how to use

```php

//open config file and setup database
define("host", "localhost"); //host
define("dbname", "test"); // database name
define("username", "root"); // database user(root)
define("password", ""); // database password default empty

```

### method one

```php


// simple statement
$getallname = DB::db()->query("select * from users")->getAllRow();
// insert data
$insert = DB::db();
$insert->query("insert into users (name,pass) values (?,?)");
$data = ['ahmed', '12345678'];
$insert->setValueList($data);
$insert->exec();

//update
$update = DB::db();
$update->query("update users set name=?,pass=? where id=5");
$data = ['ahmedabdo', 'password'];
$update->setValueList($data);
$update->exec();

//delete 
$delete = DB::db()->query("delete from users where id=5")->exec();
```

### ***method two***

```php
// table, columns, where, orderby, limit &&-> join, jointype(inner, left,cross)
$select = DB::crud()->select("users", 'name', "name like '%ab%'", "name desc", '10');
$curd->print($select);
// table, data
$insert = DB::crud()->insert('users', ['fname' => 'ali', 'lnsame' => 'abdo']);
echo $insert . br;
// table, data, where
$update = DB::crud()->update("users", ['lname' => 'abdo ali'], 'fname="ali"');
echo $update . br;
//table, data &&-> where
$delete = DB::crud()->delete("users", 'fname="ahmedali"');
echo $delete . br;
```

