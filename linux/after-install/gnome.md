# Настройка GNOME

### Удаление предустановленных программ

Обычно я пользуюсь оболочкой GNOME и после установки ОС удаляю ненужные, предустановленные пакеты.

***

Анализатор использования дисков

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc baobab
```
{% endcode %}

Веб-брауpер

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc epiphany
```
{% endcode %}

Видео

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc totem
```
{% endcode %}

Камера

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc snapshot
```
{% endcode %}

Карты

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-maps
```
{% endcode %}

Контакты

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-contacts
```
{% endcode %}

Музыка

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-music
```
{% endcode %}

Погода

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-weather
```
{% endcode %}

Подключения

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-connections
```
{% endcode %}

Сканер документов

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc simple-scan
```
{% endcode %}

Справка

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc yelp
```
{% endcode %}

Текстовый редактор

{% code overflow="wrap" fullWidth="false" %}
```bash
sudo pacman -Rsc gnome-text-editor
```
{% endcode %}

Экскурсия

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-tour
```
{% endcode %}

***

Удалить всё одной командой:

{% code overflow="wrap" %}
```bash
sudo pacman -Rsc baobab epiphany totem snapshot gnome-maps gnome-contacts gnome-music gnome-weather gnome-connections simple-scan yelp gnome-text-editor gnome-tour
```
{% endcode %}

### Смена раскладки клавиатуры

{% code title="Shift + Alt" overflow="wrap" %}
```bash
gsettings set org.gnome.desktop.wm.keybindings switch-input-source-backward "['<Shift>Alt_L']"
```
{% endcode %}

{% code title="Alt + Shift" overflow="wrap" %}
```bash
gsettings set org.gnome.desktop.wm.keybindings switch-input-source "['<Alt>Shift_L']"
```
{% endcode %}
