# php-dev-exercises

## Exercises for lecture #3 Класи

- Переписати кожний з контролерів HomeController.php, AboutController.php, ContactController.php, ErrorController.php, використовуючи класи. В кожному з контролерів створити метод index(), що визначає змінні $title та $content, наприклад в HomeController:

```php
    public function index()
    {
        $title = "Home page";
        $content = render('index', compact('title'));

        $this->response = new Response($content);
        $this->response->send();
       
    } 

```

- Виконайте push проекту php.dev на власний віддалений git-репозиторій 
