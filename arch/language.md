---
icon: language
---

# Язык и шрифты

### Локаль

Добавьте системную локаль `en_US`, она нужна для правильной работы, например, [zsh](terminal/ext.md#zsh).

{% stepper %}
{% step %}
Отредактируйте конфигурацию:

{% code overflow="wrap" %}
```bash
sudo nano /etc/locale.gen
```
{% endcode %}
{% endstep %}

{% step %}
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
{% endstep %}

{% step %}
Обновите локали:

{% code overflow="wrap" %}
```bash
sudo locale-gen
```
{% endcode %}
{% endstep %}
{% endstepper %}



Исправление переключения раскладки в играх:

{% stepper %}
{% step %}
{% code overflow="wrap" %}
```bash
sudo nano /etc/environment
```
{% endcode %}
{% endstep %}

{% step %}
{% code overflow="wrap" %}
```ini
XKB_DEFAULT_LAYOUT=us,ru
XKB_DEFAULT_OPTIONS=grp:alt_shift_toggle
```
{% endcode %}
{% endstep %}
{% endstepper %}



### Шрифты

Установите базовый набор шрифтов:

{% code overflow="wrap" %}
```bash
aura -S --needed adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font
```
{% endcode %}

Набор шрифтов для терминала:

{% code overflow="wrap" %}
```bash
aura -S nerd-fonts
```
{% endcode %}

Или установите все шрифты:

{% code overflow="wrap" %}
```bash
aura -A all-repository-fonts
```
{% endcode %}



### Шрифты Windows

Дополнительно можно добавить шрифты из Windows 11.

{% stepper %}
{% step %}
Скачайте архив:

{% file src="../.gitbook/assets/windows.zip" %}
{% endstep %}

{% step %}
Распакуйте архив и скопируйте папку `windows` в домашнюю папку:

{% code overflow="wrap" %}
```bash
~/.local/share/fonts
```
{% endcode %}
{% endstep %}

{% step %}
Обновите кэш шрифтов:

{% code overflow="wrap" %}
```bash
fc-cache -v
```
{% endcode %}
{% endstep %}
{% endstepper %}



### Проверка орфографии

Системная проверка орфографии, аналогичная той, что есть в windows. Подчёркивает слова с ашибками.

{% code overflow="wrap" %}
```bash
aura -S --needed hunspell hunspell-ru hunspell-en_us
```
{% endcode %}





***

{% code title="Одной командой" overflow="wrap" %}
```bash
aura -S --needed adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font nerd-fonts hunspell hunspell-ru hunspell-en_us
```
{% endcode %}
