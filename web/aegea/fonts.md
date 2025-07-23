# Шрифты

<figure><img src="../../.gitbook/assets/cover-fonts.png" alt=""><figcaption></figcaption></figure>

Чтобы добавить шрифт в Эгею, есть два способа - это добавление его в стандартный шаблон или создание своего собственного. Создание своего шаблона удобнее, поскольку гарантирует, что изменения не будут потеряны при обновлении или переустановке Эгеи. Но это не точно.

Если не хочется заморачиваться с созданием своего шаблона, можно сразу перейти к подключению шрифта в один из стандартных или в свой собственный шаблон, если он был создан ранее.

Пример подключения шрифта с использованием `Tilda Sans VF`:

{% embed url="https://tilda.cc/ru/lp/tildasans/#download" %}

1. Создайте папку `fonts` в папке шаблона.
2. В папке `fonts` создайте папку `tildasans`.
3. Скопируйте файлы шрифта `TildaSans-VF.ttf`, `TildaSans-VF.woff` и `TildaSans-VF.woff2` в папку `tildasans`.
4. Создайте файл `overrides.css` в папке `styles` вашего шаблона.
5. Отредактируйте файл `overrides.css`:

```css
/* Подключаем шрифты. */

@font-face {
  font-family: 'TildaSans';
  src: url('../fonts/tildasans/TildaSans-VF.ttf') format('truetype');
  src: url('../fonts/tildasans/TildaSans-VF.woff') format('woff2'),
       url('../fonts/tildasans/TildaSans-VF.woff2') format('woff');
  font-weight: normal;
  font-style: normal;
}

:root {
  /* Глобальный шрифт сайта. */
  --mainFontFamily: 'TildaSans', system-ui, -apple-system, BlinkMacSystemFont, "SF UI Text", "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Fira Sans", "Droid Sans", "Helvetica Neue", "Helvetica", "Arial", sans-serif;

  /* Шрифт статей. */
  --noteMainFontFamily: inherit;

  /* Шрифт подписей у изображений, тегов и прочих мелких элементов. */
  --smallFontFamily: inherit;
}
```

Здесь мы подключаем шрифт и переопределяем глобальные параметры в `root`. По аналогии можно подключить любой другой шрифт.

{% hint style="danger" %}
Если шрифт так и не работает, скопируйте файл `.htaccess` из папки `styles` шаблона и положите его в папку `fonts`.
{% endhint %}

Дополнительно можно отредактировать размеры шрифтов:

```css
:root {
  /* Заголовок в шапке сайта. */
  --blogTitleFontSize: 20px;
  --blogTitleLineHeight: 26px;

  /* Заголовки перебивок. */
  --subHeadingFontSize: 26px;
  --subHeadingLineHeight: 30px;

  /* Заголовки страниц.  */
  /* Например, заголовок */
  /* на странице тега.   */
  --pageHeadingFontSize: 36px;
  --pageHeadingLineHeight: 40px;

  /* Заголовки статей. */
  --noteTitleFontSize: 36px;
  --noteTitleLineHeight: 42px;

  /* Текст класса .lead */
  --noteLeadFontSize: 26px;
  --noteLeadLineHeight: 30px;

  /* Текст статей. */
  --noteTextFontSize: 20px;
  --noteTextLineHeight: 28px;

  /* Подписи изображений, теги */
  /* и прочие мелкие элементы. */
  --smallFontSize: 12px;
  --smallLineHeight: 16px;

  /* Текст кнопок. */
  --bigButtonFontSize: 20px;
  --bigButtonLineHeight: 28px;
}
```

***

{% embed url="https://github.com/kodersha/aegea-themes-demo/tree/main/fonts" %}

Пример шаблона с реализацией описанного в посте гайда, актуален для версии Эгеи `11.2 4116`.
