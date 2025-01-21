---
description: Смена языка режима «Рабочего Стола» на русский.
icon: language
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
---

# Язык

{% stepper %}
{% step %}
Перейдите в режим рабочего стола и откройте термина `Konsole`.
{% endstep %}

{% step %}
Установите пароль администратора, если он ещё не установлен:

{% code overflow="wrap" %}
```bash
passwd
```
{% endcode %}
{% endstep %}

{% step %}
Отключите `read-only` режим:

{% code overflow="wrap" %}
```bash
sudo steamos-readonly disable
```
{% endcode %}
{% endstep %}

{% step %}
Cоздайте необходимые ключи для проверки подписи пакетов, командой:

{% code overflow="wrap" %}
```bash
sudo pacman-key --init && sudo pacman-key --populate archlinux
```
{% endcode %}
{% endstep %}

{% step %}
Обновите пакет `glibc`:

{% code overflow="wrap" %}
```bash
sudo pacman -Syu glibc
```
{% endcode %}
{% endstep %}

{% step %}
Откройте файл `locale.gen`:

{% code overflow="wrap" %}
```bash
sudo nano /etc/locale.gen
```
{% endcode %}
{% endstep %}

{% step %}
Найдите и уберите комментарий (#) у строк:

{% code title="locale.gen" %}
```editorconfig
en_US.UTF-8
ru_RU.UTF-8
```
{% endcode %}

_Сохраните изменения `Ctrl` + `O` и закройте редактор `Ctrl` + `X`._
{% endstep %}

{% step %}
Генерируйте локаль:

{% code overflow="wrap" %}
```bash
 sudo locale-gen
```
{% endcode %}
{% endstep %}

{% step %}
Откройте файл `locale.conf`:

{% code overflow="wrap" %}
```bash
sudo nano /etc/locale.conf
```
{% endcode %}
{% endstep %}

{% step %}
Замените строку:

{% code title="locale.conf" %}
```editorconfig
LANG=en_US.UTF-8
```
{% endcode %}

На:

{% code title="locale.conf" %}
```editorconfig
LANG=ru_RU.UTF-8
```
{% endcode %}

_Сохраните изменения `Ctrl` + `O` и закройте редактор `Ctrl` + `X`._
{% endstep %}

{% step %}
Установите локаль в качестве основной:

{% code overflow="wrap" %}
```bash
sudo localectl set-locale ru_RU.UTF-8
```
{% endcode %}
{% endstep %}

{% step %}
Удалите стандартный файл конфигурации, который используется окружением рабочего стола KDE для хранения локальных настроек пользователя:

{% code overflow="wrap" %}
```bash
sudo rm ~/.config/plasma-localerc
```
{% endcode %}
{% endstep %}

{% step %}
Снова включите `read-only` режим:

```bash
sudo steamos-readonly disable
```
{% endstep %}
{% endstepper %}





***

{% embed url="https://steamcommunity.com/discussions/forum/26/3722818378189549225/" %}
