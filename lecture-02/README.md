# php-dev-exercises

## Exercises for lecture #2 MVC

- В корені проєкту створіть каталоги app, bootstrap, config, views
- В середині каталогу app створіть каталог Controllers
- В середині каталогу Controllers створіть файли HomeController.php, AboutController.php, ContactController.php
- В середині каталогу bootstrap створіть файл app.php
- В середині каталогу config створіть файл routes.php
- В середині каталогу views створіть файли index.php, about.php, contact.php
- В середині каталогу views створіть каталог layouts
- В середині каталогу views/layouts створіть файл app.php

**Результатом повинна стати така структура:**

```

├────── /public
│   ├── index.php
│   ├── favicon.ico
│   └── .htaccess
├────── /app
│   └───── /Controllers
│     ├── HomeController.php
│     ├── AboutController.php
│     └── ContactController.php
├────── /bootstrap
│   └── app.php
├────── /config
│   └── routes.php
├────── /views
│   └───── /layouts
│    ├── └── app.php
│    ├── index.php
│    ├── about.php
│    └── contact.php
├── /.git
├── .gitignore
├── LICENSE
└── README.md

```

### файл bootstrap/app.php:

```php

function getEnvs()
{
    return $_ENV;
}

function boot(): void
{
    date_default_timezone_set(getenv('APP_TIMEZONE') ?: 'UTC');
}

boot();

function render(string $view, array $context = []): string
{
    ob_start(null, 2048);
    $content = template($view, $context);
    $layout = dirname(__DIR__, 1) . '/views/layouts/app.php';
    // require_once dirname(__DIR__, 1) . '/views/layouts/app.php';
    require_once $layout;
    return str_replace("{{ content }}", $content, ob_get_clean());
}

function template(string $view, array $context) : string
{
    $file = dirname(__DIR__, 1) . "/views/$view.php";

    if (!file_exists($file)) {
        die("The file ($file) could not be found.");
    }

    ob_start();
    extract($context);
    include ($file);
    return ob_get_clean();

}

function uri(): string
{
    return $_SERVER['REQUEST_URI'];
}

switch ($request) {
    case '/':
       require_once dirname(__DIR__, 1) . '/app/Controllers/HomeController.php';
       break;
       
    case '/about':
        require_once dirname(__DIR__, 1) . '/app/Controllers/AboutController.php';
        break;

    case '/contact':
        require_once dirname(__DIR__, 1) . '/app/Controllers/ContactController.php';
        break;
}

```

- В кожному з контролерів HomeController.php, AboutController.php, ContactController.php визначити змінні $title та $breadcrumbs, наприклад в HomeController:

```php
// app/Controllers/HomeController.php
$title = "Home page";

$breadcrumbs =[
    'title' => "Home page",
    'link' => "/",
];

```

- В кожному з контролерів HomeController.php, AboutController.php, ContactController.php викличте фунуцію render, визначену в bootstrap/app.php, наприклад в HomeController:

```php
<?php
// app/Controllers/HomeController.php

...

echo render('index', compact('title', 'breadcrumbs'));
```

- В середині каталогу Controllers створіть файл ErrorController.php
- В середині каталогу views створіть файл error.php, що містить повідомлення про помилку 404.
- Перепишіть блок маршрутизації у файлі bootstrap/app.php, замінивши оператор switch на match. 

```php
switch ($request) {
    case '/':
       require_once dirname(__DIR__, 1) . '/app/Controllers/HomeController.php';
       break;
       
    case '/about':
        require_once dirname(__DIR__, 1) . '/app/Controllers/AboutController.php';
        break;

    case '/contact':
        require_once dirname(__DIR__, 1) . '/app/Controllers/ContactController.php';
        break;
}

```

- Визначити шаблон за замовчуванням в операторі match, що відповідає підключенню контролера ErrorController.php.

- Виконайте push проекту php.dev на власний віддалений git-репозиторій 
