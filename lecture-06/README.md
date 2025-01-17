# php-dev-exercises

## Exercises for lecture #6 inherits

- Переписати кожний з контролерів HomeController.php, AboutController.php, ContactController.php, ErrorController.php, розширюючи їх від базового класу BaseController:

```php

<?php declare(strict_types=1);

namespace App\Core\Http;

use App\Core\Kernel;
use App\Core\Renderer\View;

class BaseController
{
    private View $view;
    protected string $layout;

    public function __construct() 
    {
        $templates = dirname(__DIR__, 2)."/views";
        $this->view = new View(path: $templates, layout: $this->layout);
    }
    protected function view(): View
    {
        return $this->view;
    }
}

`

- Виконайте push проекту php.dev на власний віддалений git-репозиторій 
