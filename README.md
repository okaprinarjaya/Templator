# Templator
## An awesome [Twig](twig.sensiolabs.org) wrapper to control your layout like a boss!

[![Build Status](https://travis-ci.org/Kristories/Templator.png)](https://travis-ci.org/Kristories/Templator)

## What Templator can do for you?
- Gives freedom to the template designer to design & create layout's widgets as many as they want without worrying how the developers consume and arrange the layout later
- Gives the developer a simple way to consume and adjust layouts that provided by the template designer
- Focus on position
- Widget can be displayed in all the positions of a template

---


# The Concept
### You are template designer

```html   
<!DOCTYPE html>
<html lang="en">
<head>
<title>{{ title }}</title>
</head>
<body>
    {% block header %}{% endblock %}
    {% block left %}{% endblock %}
    {% block content %}{% endblock %}
    {% block right %}{% endblock %}
    {% block footer %}{% endblock %}
</body>
</html>
```

![1](assets/1.png)

---



### You are developer
As a developer you can control the layout easily looks like below:

```php
$templator->widgets(array(
    'block' => array('widget')
));
```

#### Let see the big picture of the concept below

If you do this

```php
$templator->widgets(array(
    'header'    => array('widget_a'),
    'left'      => array('widget_b'),
    'right'     => array('widget_c'),
    'footer'    => array('widget_d')
));
```

You get

![2](assets/2.png)

---


If you do this

```php
$templator->widgets(array(
    'header'    => array('widget_a'),
    'right'     => array('widget_c'),
    'footer'    => array('widget_d')
));
```

You get

![3](assets/3.png)

---


If you do this

```php
$templator->widgets(array(
    'header'    => array('widget_a'),
    'right'     => array('widget_b', 'widget_c', 'widget_e', 'widget_f'),
    'footer'    => array('widget_d')
));
```

You get

![4](assets/4.png)

---



## Installation

Add the following into your `composer.json` file:

```json
{
    "require": {
        "kristories/templator": "*"
    }
}
```

Then run

    composer install


## Usage

### Basic

```php
$templator = new \Templator\Templator();

// Set data
$templator->data('foo', 'bar');

// Render
echo $templator->render('base_template', 'page');
```

### Config

```php
$templator = new \Templator\Templator(array(
    'path'  => array(
        'root'      => 'templates',
        'base'      => 'base',
        'pages'     => 'pages',
        'widgets'   => 'widgets'
    ),
    'cache' => NULL
));
```

Structure :

    ├── templates/
    |   ├── base/
    |   |   └── base_template.html
    |   ├── pages/
    |   |   ├── home.html
    |   |   ├── about.html
    |   |   ├── contact.html
    |   |   └── ...
    |   └── widgets/
    |   |   ├── logo.html
    |   |   ├── menu.html
    |   |   ├── tags.html
    |   |   ├── search.html    
    |   |   └── ...
    └── cache

### Data

```php
$templator->data('foo', 'bar');
// or
$templator->data(array(
    'foo' => 'bar',
    'bar' => 'baz'
));
```

### Arrange the blocks

```php
$templator->widgets(array(
    'header' => array('logo', 'mainmenu', 'search'),
    'footer' => array('copyright, 'footermenu')
));
```

## More examples
TL;DR

## Why Twig?

### Twig is a modern template engine for PHP

- **Fast**: Twig compiles templates down to plain optimized PHP code. The overhead compared to regular PHP code was reduced to the very minimum.
- **Secure**: Twig has a sandbox mode to evaluate untrusted template code. This allows Twig to be used as a template language for applications where users may modify the template design.
- **Flexible**: Twig is powered by a flexible lexer and parser. This allows the developer to define its own custom tags and filters, and create its own DSL.
