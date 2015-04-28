# Pantheon Tools
Basic shell scripts to make it easier to work with Pantheon.

## Configuration
Create a .cnf file for each environment
- test.cnf
- dev.cnf
- local.cnf
```
[client]
user='root'
password='root'
host='localhost'
port='3306'
verbose
```

## Usage
- for MAMP, add '/Applications/MAMP/bin/php/php5.6.2/bin' to your $PATH

### db-dump
**Usage**
```
db-dump $DATABASE
db-dump example.com
```
**Returns**
```
$DATABASE-$DATETIME.sql
example.com-YYYYMMDD-HHMMSS.sql
```

### db-replace
**Usage**
```
db-replace $FILENAME $ENVIRONMENT $SEARCH $REPLACE
db-replace example.com-YYYYMMDD-HHMMSS.sql dev example.com.local:8888 dev.example.com
```
**Returns**
```
$ENVIRONMENT-$DATABASE-$DATETIME.sql
dev-example.com-YYYYMMDD-HHMMSS.sql
```

### db-dump-replace
**Usage**
```
db-dump-replace $DATABASE $ENVIRONMENT $SEARCH $REPLACE
db-dump-replace example.com dev example.com.local:8888 dev.example.com
```
**Returns**
```
$DATABASE-$DATETIME.sql
example.com-YYYYMMDD-HHMMSS.sql

$ENVIRONMENT-$DATABASE-$DATETIME.sql
dev-example.com-YYYYMMDD-HHMMSS.sql
```

### db-push
**Usage**
```
db-push $ENVIRONMENT $FILE
db-push dev dev-example.com-YYYYMMDD-HHMMSS.sql
```

### db-pull
**Usage**
```
db-push $ENVIRONMENT $FILENAME
db-push dev dev-example.sql
```
**Returns**
```
$ENVIRONMENT-$FILENAME-$DATETIME.sql
dev-example.com-YYYYMMDD-HHMMSS.sql
```

### db-pull-replace
**Usage**
```
db-pull-replace $ENVIRONMENT $FILENAME $SEARCH $REPLACE
db-pull-replace dev example.com dev.example.com example.com.local:8888
```
**Returns**
```
$ENVIRONMENT-$FILENAME-$DATETIME.sql
dev-example.com-YYYYMMDD-HHMMSS.sql

$FILENAME-$DATETIME.sql
example.com-YYYYMMDD-HHMMSS.sql
```

## References
- https://pantheon.io/blog/importing-large-wordpress-sites-pantheon
- http://stackoverflow.com/questions/3268789/add-mysqldump-to-mamp-mysql-w-apache-php-on-macos-x