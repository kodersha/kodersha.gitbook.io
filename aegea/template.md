---
description: >-
  Создать свой шаблон для Эгеи не так сложно как может показаться на первый
  взгляд. Давайте разберем основные принципы построения шаблона используя
  некоторые простые примеры.
---

# 🍋 Пользовательский шаблон

В папке `themes`, что в корне Эгеи, скопируйте папку со стандартной темой `plain` (Либо любой другой стандартной темой Эгеи) и переименуйте скопированную папку шаблона, например, в `mytheme`. В папке `mytheme` отредактируйте конфигурационный файл `theme-info.php`.

```php
<?php return array (
    'index' => 99, // Порядковый номер шаблона

    'display_name' => array (
        'en' => 'My theme', // Название шаблона на английском
        'ru' => 'Моя тема', // Название шаблона на русском
    ),

    'colors' => array (
        'background' => '#fff',
        'headings' => '#000',
        'text' => '#000',
        'link' => '#0060a0',
    ),

    'meta_viewport' => 'width=device-width, initial-scale=1',
    'supports_dark_mode' => true,
); ?>
```

Здесь, в строке `index`, укажите порядковый номер шаблона, а в `display_name` задайте имя на русском и английском, для его отображения в списке шаблонов, в настройках Эгеи.

{% hint style="warning" %}
Пользовательские темы находятся в папке `./user/themes` в корне блога. Скопируйте ваш шаблон туда и активируйте его в настройках сайта.
{% endhint %}

<figure><img src=".gitbook/assets/template.png" alt=""><figcaption></figcaption></figure>

В папке темы также существует несколько папок из которых Эгея подхватывает скрипты, стили, изображения и файлы разметки:

* `./themes/mytheme/images` — Изображения.
* `./themes/mytheme/js` — JS скрипты.
* `./themes/mytheme/src` — Исходные sass/less файлы стилей.
* `./themes/mythemey/styles` — CSS стили.
* `./themes/mytheme/templates` — PHP файлы шаблона.

Если файлов в папках нет, они будут подхватываться из стандартной темы Эгеи, которая находится по пути `./system/theme`.

{% hint style="danger" %}
Чтобы внести изменения в стандартные шаблоны Эгеи, скопируйте необходимый файл из `./system/theme/templates` в папку `templates` вашей темы и уже там производите все изменения. Вносить правки в системной папке не стоит, так как после обновления движка все изменения перезапишутся свежей установкой.
{% endhint %}



### Разбор основных шаблонов

{% hint style="danger" %}
Статья устарела и не всё написанное в ней отражает действительность, так как Эгея периодически обновляется. Тем не менее она всё равно может оказаться полезной.
{% endhint %}

Теперь стоит подробнее разобрать содержимое папки `templates`, для наглядности того, как выглядит тот или иной элемент в живую, я добавила соответствующие файлам скриншоты.

<figure><img src=".gitbook/assets/shablon-01.png" alt=""><figcaption><p><code>user-picture.tmpl.php</code> — Аватар блога.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-02.png" alt=""><figcaption><p><code>author-menu.tmpl.php</code> — Меню автора.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-03.png" alt=""><figcaption><p><code>search-heading.tmpl.php</code> — Форма поиска.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-04.png" alt=""><figcaption><p><code>notes.tmpl.php</code> — Пост.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-05.png" alt=""><figcaption><p><code>pages.tmpl.php</code> — Навигация между постами.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-06.png" alt=""><figcaption><p><code>comments-heading.tmpl.php</code> — Заголовок списка комментариев с счетчиком их количества.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-07.png" alt=""><figcaption><p><code>comments.tmpl.php</code> — Список комментариев.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-08.png" alt=""><figcaption><p><code>form-comment.tmpl.php</code> — Форма комментария.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-09.png" alt=""><figcaption><p><code>form-comment-reply.tmpl.php</code> — Форма ответа на комментарий.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-10.png" alt=""><figcaption><p><code>popular.tmpl.php</code> — Блок популярных постов.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-11.png" alt=""><figcaption><p><code>pages-earlier.tmpl.php</code> — Кнопка к постам «Ранее».</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-12.png" alt=""><figcaption><p><code>pages-later.tmpl.php</code> — Кнопка к постам «Позднее».</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-13.png" alt=""><figcaption><p><code>notes-list.tmpl.php</code> — Список всех постов блога.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-14.png" alt=""><figcaption><p><code>heading.tmpl.php</code> — Заголовки на большинстве страниц.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-15.png" alt=""><figcaption><p><code>form-note.tmpl.php</code> — Форма публикации поста.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-16.png" alt=""><figcaption><p><code>form-note-delete.tmpl.php</code> — Форма удаления поста.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-17.png" alt=""><figcaption><p><code>form-note-publish.tmpl.php</code> — Кнопка публикации поста.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-18.png" alt=""><figcaption><p><code>drafts.tmpl.php</code> — Список черновиков.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-19.png" alt=""><figcaption><p><code>form-preferences.tmpl.php</code> — Форма общих настроек блога.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-20.png" alt=""><figcaption><p><code>form-password.tmpl.php</code> — Форма смены админ-пароля.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-21.png" alt=""><figcaption><p><code>form-database.tmpl.php</code> — Форма подключения к базе данных.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-22.png" alt=""><figcaption><p><code>sessions.tmpl.php</code> — Список текущих сессий.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-23.png" alt=""><figcaption><p><code>form-install.tmpl.php</code> — Форма установки Эгеи.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-24.png" alt=""><figcaption><p><code>form-login.tmpl.php</code> — Форма авторизации.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-25.png" alt=""><figcaption><p><code>tags.tmpl.php</code> — Список всех тегов блога.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-26.png" alt=""><figcaption><p><code>form-tag.tmpl.php</code> — Форма редактирования тега.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-27.png" alt=""><figcaption><p><code>form-tag-delete.tmpl.php</code> — Форма удаления тега.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-28.png" alt=""><figcaption><p><code>tags-menu.tmpl.php</code> — Меню избранных тегов.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-29.png" alt=""><figcaption><p><code>form-search.tmpl.php</code> — Форма поиска на странице поиска.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-30.png" alt=""><figcaption><p><code>login-element.tmpl.php</code> — Кнопка авторизации в футере.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-31.png" alt=""><figcaption><p><code>form-password-reset-email.tmpl.php</code> — Страница сброса пароля.</p></figcaption></figure>

<figure><img src=".gitbook/assets/shablon-32.png" alt=""><figcaption><p><code>layout.tmpl.php</code> — Основная разметка шаблона внутри body, здесь подключаются другие части шаблона.</p></figcaption></figure>



`main.tmpl.php` — Разметка внутри `html`, здесь подключается `head.tmpl.php` содержащий метатеги, сам `layout.tmpl.php`, `js` и `css`.

Эти файлы можно копировать в папку `templates` своей темы и редактировать на свой вкус.

***

Подключить свою собственную часть шаблона можно создав файл типа `name.tmpl.php` в папке `templates` и затем вызвать его в любом другом месте или в `layout.tmpl.php`. Например, можно создать файл `menu.tmpl.php` со своим меню и ссылками на соц-сети, сверстанными на `html` и `css`, и вызвать его в `layout.tmpl.php` специальным макросом. Илья Бирман в справке к Эгее пишет:

> Шаблон может вызывать другие шаблоны для отображения конкретного фрагмента: `_T ()` — вызывает шаблон по имени. (…) Шаблон `layout.tmpl.php` «срабатывает» потому, что `main.tmpl.php` вызывает его для формирования тела страницы.

Так, чтобы вывести содержимое файла `menu.tmpl.php` где-нибудь на сайте, достаточно небольшого кода:

```php
<?php _T ('menu') ?>
```

К слову, если вам нужно вывести часть шаблона, скажем, только на главной странице, но не на странице поста, оберните код вывода следующим уточнением:

```php
<?php if ($content['class'] == 'frontpage') { ?>
    <?php _T ('menu') ?>
<?php } ?>
```

Или, если нужно вывести эту часть шаблона только на странице поста:

```php
<?php if ($content['class'] == 'note') { ?>
   <?php _T ('menu') ?>
<?php } ?>
```

`JS` и `CSS` в тему Эгеи тоже подключаются специальными макросами. Для наглядности откройте стандартный `main.tmpl.php` и посмотрите в конец файла, после закрывающего тега `body`:

```php
<?php _CSS ('main') ?>
<?php _JS ('main') ?>
```

Здесь подхватываются `./js/main.js` и `./styles/main.css` из папки темы, или из стандартной темы, если нет соответствующих файлов. По такому принципу можно добавить, например, скрипт `bootstrap.min.js` в папку `js` и подключить его кодом:

```php
<?php _JS ('bootstrap.min') ?>
```

Таким образом можно редактировать отдельные части шаблона Эгеи при создании своей темы, подключать стили и скрипты. Также, для более полной информации, рекомендую ознакомиться с официальной документацией по темам оформления Эгеи.
