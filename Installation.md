# Installation #
You will need to install WWW SQL Designer if you want to:
  * Use custom locale
  * Use custom CSS file
  * Use custom DB definition
  * Use custom server backend

Just [download](http://code.google.com/p/wwwsqldesigner/downloads/list) and unpack latest application archive. There are generally no requirements, but to use server-side storage, one should have a working webserver.

## To enable the Load and Save features using a database ##

Ensure that you have a working webserver (Such as WAMP for Windows, MAMP on
Mac etc) enabled on your desktop or the PC you will be working off.

You will then need to create a database and enable a user on it:

For PHP-MySQL:

Once logged into the console, create a database that the application will
use:
```
mysql> create database sqlDesignerExample;
Query OK, 1 row affected (0.03 sec)
```
Ensure that you switch to the database you just created:
```
mysql> use sqlDesignerExample;
Database changed
mysql> DROP TABLE IF EXISTS `wwwsqldesigner`;
Query OK, 0 rows affected, 1 warning (0.03 sec)
```
Run the SQL in the sqlDesigner\backend\php-mysql folder:
```
mysql> CREATE TABLE `wwwsqldesigner` (
    ->   `keyword` varchar(30) NOT NULL default '',
    ->   `data` mediumtext,
    ->   `dt` timestamp,
    ->   PRIMARY KEY  (`keyword`)
    -> );
Query OK, 0 rows affected (0.03 sec)
```
Now, create a user with the permissions as needed:
```
mysql> create user 'sqlExample'@'localhost' identified by
'someSuperSecretPassword';
Query OK, 0 rows affected (0.38 sec)

mysql> grant all privileges on sqlDesignerExample.* to
'sqlExample'@'localhost'
with grant option;
Query OK, 0 rows affected (0.03 sec)
```
Finally, update the PHP file in the same folder. You will need to make
changes to the first function as follows:
```
function setup_saveloadlist() {
    define("SERVER", "localhost");
    define("USER", "sqlExample");
    define("PASSWORD", "someSuperSecretPassword");
    define("DB", "sqlDesignerExample");
    define("TABLE", "wwwsqldesigner");
}
```
Save the file after you make the changes and you will now be able to load
and save using Server Backend: php-mysql