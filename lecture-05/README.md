# php-dev-exercises

## Exercises for lecture #5 namespace

- Переписати кожний з контролерів HomeController.php, AboutController.php, ContactController.php, ErrorController.php, використовуючи простори імен, наприклад  HomeController:

```php

<?php

// app/Controllers/HomeController.php
declare(strict_types=1);

namespace Controllers;

```
- В ContactController після отримання результату $result, передайте його разом з $title до представлення наступним чином:


```php

   public function index()
    {
        $title = "Contact page";
        $config = require_once dirname(__DIR__, 2).'/config/db.php';
        $pdo = Connection::make($config['database']);

        $sql = "SELECT * FROM feedback";
        $statement = $pdo->prepare($sql);
        $statement->execute();
        $result = $statement->fetchAll();
        
        $content = render('contact', compact('title', 'result'));
       
        $this->response = new Response($content);
        $this->render($content);       
    }

```

- В представленні contact.php потрібно відобразити результат $result у вигляді таблиці, використовуючи цикл foreach наступним чином:

```php
   <?php foreach($result as $item):?>
      <table>

      </table>
   <?php endforeach;?>
```


- Виконайте push проекту php.dev на власний віддалений git-репозиторій 
