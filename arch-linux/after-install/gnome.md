# Настройка GNOME

### Удаление предустановленных программ

Обычно я пользуюсь оболочкой GNOME и после установки ОС удаляю ненужные, предустановленные пакеты.

***

Анализатор использования дисков

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove baobab
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc baobab
```
{% endcode %}
{% endtab %}
{% endtabs %}

Веб-брауpер

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove firefox firefox-langpacks
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc epiphany
```
{% endcode %}
{% endtab %}
{% endtabs %}

Видео

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove totem
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc totem
```
{% endcode %}
{% endtab %}
{% endtabs %}

Камера

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove snapshot
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc snapshot
```
{% endcode %}
{% endtab %}
{% endtabs %}

Карты

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove gnome-maps
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-maps
```
{% endcode %}
{% endtab %}
{% endtabs %}

Контакты

{% tabs %}
{% tab title="undefined" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove gnome-contacts
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-contacts
```
{% endcode %}
{% endtab %}
{% endtabs %}

Музыка

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove rhythmbox
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-music
```
{% endcode %}
{% endtab %}
{% endtabs %}

Погода

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove gnome-weather
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-weather
```
{% endcode %}
{% endtab %}
{% endtabs %}

Подключения

{% tabs %}
{% tab title="fedora" %}
```bash
sudo dnf remove gnome-connections
```
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-connections
```
{% endcode %}
{% endtab %}
{% endtabs %}

Сканер документов

{% tabs %}
{% tab title="fedora" %}
```bash
sudo dnf remove simple-scan
```
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc simple-scan
```
{% endcode %}
{% endtab %}
{% endtabs %}

Справка

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove yelp
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc yelp
```
{% endcode %}
{% endtab %}
{% endtabs %}

Текстовый редактор

{% tabs %}
{% tab title="fedora" %}
```bash
sudo dnf remove gnome-text-editor
```
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" fullWidth="false" %}
```bash
sudo pacman -Rsc gnome-text-editor
```
{% endcode %}
{% endtab %}
{% endtabs %}

Экскурсия

{% tabs %}
{% tab title="fedora" %}
```bash
sudo dnf remove gnome-tour
```
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc gnome-tour
```
{% endcode %}
{% endtab %}
{% endtabs %}

LibreOffice

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove libreoffice-core
```
{% endcode %}
{% endtab %}
{% endtabs %}

***

Удалить всё одной командой:

{% tabs %}
{% tab title="fedora" %}
{% code overflow="wrap" %}
```bash
sudo dnf remove baobab totem snapshot gnome-maps gnome-contacts gnome-music gnome-weather gnome-connections simple-scan yelp gnome-text-editor gnome-tour
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
{% code overflow="wrap" %}
```bash
sudo pacman -Rsc baobab epiphany totem snapshot gnome-maps gnome-contacts gnome-music gnome-weather gnome-connections simple-scan yelp gnome-text-editor gnome-tour
```
{% endcode %}
{% endtab %}
{% endtabs %}

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
