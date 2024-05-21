# Минимизация GNOME



### Удаление предустановленных программ

Обычно я пользуюсь оболочкой GNOME и после установки Arch удаляю ненужные, предустановленные пакеты.

***

{% code title="Анализатор использования дисков" overflow="wrap" %}
```bash
sudo pacman -Rsc baobab
```
{% endcode %}

{% code title="Веб-брауpер" overflow="wrap" %}
```bash
sudo pacman -Rsc epiphany
```
{% endcode %}

{% code title="Видео" overflow="wrap" %}
```bash
sudo pacman -Rsc totem
```
{% endcode %}

{% code title="Камера" overflow="wrap" %}
```bash
sudo pacman -Rsc snapshot
```
{% endcode %}

{% code title="Карты" overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-maps
```
{% endcode %}

{% code title="Контакты" overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-contacts
```
{% endcode %}

{% code title="Музыка" overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-music
```
{% endcode %}

{% code title="Погода" overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-weather
```
{% endcode %}

{% code title="Подключения" overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-connections
```
{% endcode %}

{% code title="Сканер документов" overflow="wrap" %}
```bash
sudo pacman -Rsc simple-scan
```
{% endcode %}

{% code title="Справка" overflow="wrap" %}
```bash
sudo pacman -Rsc yelp
```
{% endcode %}

{% code title="Текстовый редактор" overflow="wrap" fullWidth="false" %}
```bash
sudo pacman -Rsc gnome-text-editor
```
{% endcode %}

{% code title="Экскурсия" overflow="wrap" %}
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

