# Язык и шрифты

### Локаль

Добавьте системную локаль `en_US`, она нужна для правильной работы, например, zsh.

Отредактируйте конфигурацию:

{% code overflow="wrap" %}
```bash
sudo nano /etc/locale.gen
```
{% endcode %}

Найдите и раскомментируйте строку `en_US.UTF-8 UTF-8`:

{% code title="Пример" overflow="wrap" %}
```ini
...
#en_SG ISO-8859-1
en_US.UTF-8 UTF-8
#en_US ISO-8859-1
...
```
{% endcode %}

Обновите локали:

{% code overflow="wrap" %}
```bash
sudo locale-gen
```
{% endcode %}



### X11

```bash
localectl set-x11-keymap us,ru "" "" grp:alt_shift_toggle
```



### Исправление раскладки в играх

{% code overflow="wrap" %}
```bash
sudo nano /etc/environment
```
{% endcode %}

```ini
XKB_DEFAULT_LAYOUT=us,ru
XKB_DEFAULT_OPTIONS=grp:alt_shift_toggle
```



### Шрифты

Установите базовый набор шрифтов:

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font
```
{% endcode %}

Набор шрифтов для терминала:

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed nerd-fonts
```
{% endcode %}

Или установите все шрифты:

{% code overflow="wrap" %}
```bash
yay -S --needed all-repository-fonts
```
{% endcode %}



### Шрифты Windows

Дополнительно можно добавить шрифты из Windows 11.

{% file src="../.gitbook/assets/windows.zip" %}

Скачайте архив, распакуйте и скопируйте папку `windows` в домашнюю папку:

```bash
~/.local/share/fonts
```

Обновите кэш шрифтов:

```bash
fc-cache -v
```



### Проверка орфографии

Системная проверка орфографии, аналогичная той, что есть в windows. Подчёркивает слова с ашибками.

```bash
sudo pacman -S --needed hunspell hunspell-ru hunspell-en_us
```
