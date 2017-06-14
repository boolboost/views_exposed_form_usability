## Описание

Модуль позволяет использовать вложености в форме "views_exposed_form".

Так же помещает заголовки из $info в атрибут элементов формы.

## Отображение формы

Элементы отображаются в следующем порядке.

- фильтры в корне формы, в порядке указаном во views.
- фильтры и кнопки в обёртках например в fieldset, custom элементы.
- кнопки в корне формы.

> Используется нестандартный шаблон https://github.com/boolboost/views_exposed_form_usability/blob/master/theme/views-exposed-form.tpl.php.

Примеры ниже выполняются в `hook_form_alter()` или `hook_form_views_exposed_form_alter()`.

## Пример 1

Переместить любой элемент в div "wrap".

~~~ php
$form['wrap']['element'] = $form['element'];
$form['element']['#type'] = 'hidden';
~~~

## Пример 2

Посмотреть заголовок фильтра.

~~~ php
// widget textfield
$form['field_name']['#title'];
// widget range
$form['field_name']['value']['#title'];
~~~

## Пример 3

Переместить кнопку submit в div "actions".

> Физически нельзя удалять элемент "submit" из корня.
>
> Данный код отменяет его отображение.

~~~ php
$form['actions']['submit'] = $form['submit'];
$form['submit']['#printed'] = TRUE;
~~~
