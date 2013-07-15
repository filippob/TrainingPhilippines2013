

# Using MySQL


---

## MySQL options

- Environment variables (e.g. *$MYSQL_HOME*)
- Configuration file
- Command line

&iexcl;In this order of priority!

---

## Command line

Extended format

    --host=localhost --user=root --password

Short format

    -h localhost -u root -p

Connect to a mysql server:

    mysql -h localhost -u root -p

---

## Configuration file
     
    mysql --help --verbose

    /etc/my.cnf     #general options

    #example file
    host=localhost
    user=root
    password=chosen_password
    ;comment


---

##  Manage a database

Connect to a database

    mysql -u root -p buffalo

View data

    select * from animals;

Insert record

    insert into animals values ('','ES060606',
    'Rodeo','2006-01-10',0,'USM123456','')






