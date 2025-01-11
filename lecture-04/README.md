# php-dev-exercises

## Exercises for lecture #4 mySQL

- Налаштувати базу даних проекту, зберігши налаштування у файлі .env, наприклад

```php

APP_ENV=dev
APP_TIMEZONE=UTC
DB_HOST=127.0.0.1
DB_NAME=shopaholic
DB_USERNAME=root
DB_PASSWORD=password 

```
- Створити таблицю categories з настуаними полями:

```sql
   id int(11) unsigned NOT NULL AUTO_INCREMENT,
   name varchar(20) NOT NULL,
   image varchar(255) NOT NULL,
   PRIMARY KEY (id)
```

- Створити таблицю brands з настуаними полями:

```sql
   id int(11) unsigned NOT NULL AUTO_INCREMENT,
   name varchar(20) NOT NULL,
   description text NOT NULL,
   PRIMARY KEY (id)
```

- Створити таблицю tags з настуаними полями:

```sql
   id int(11) unsigned NOT NULL AUTO_INCREMENT,
   name varchar(20) NOT NULL,
   slug varchar(20) NOT NULL,
   PRIMARY KEY (id)
```

- Створити таблицю badges з настуаними полями:

```sql
   id int(11) unsigned NOT NULL AUTO_INCREMENT,
   title varchar(20) NOT NULL,
   PRIMARY KEY (id)
```
- Заповнити кожну з таблиць тестовими даними. Написати sql-запити, що повертають всі дані з кожної таблиці.

- Виконайте push проекту php.dev на власний віддалений git-репозиторій 
