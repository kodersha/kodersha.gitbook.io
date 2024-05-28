# Настройка GNOME

### Удаление предустановленных пакетов

Обычно я пользуюсь оболочкой GNOME и после установки ОС удаляю ненужные, предустановленные пакеты.

***

{% code title="Анализатор использования дисков" overflow="wrap" %}
```bash
sudo pacman -Rns baobab
```
{% endcode %}

{% code title=" Веб-брауpер" overflow="wrap" %}
```bash
sudo pacman -Rns epiphany
```
{% endcode %}

{% code title="Видео" overflow="wrap" %}
```bash
sudo pacman -Rns totem
```
{% endcode %}

{% code title="Камера" overflow="wrap" %}
```bash
sudo pacman -Rns snapshot
```
{% endcode %}

{% code title=" Карты" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-maps
```
{% endcode %}

{% code title="Контакты" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-contacts
```
{% endcode %}

{% code title="Музыка" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-music
```
{% endcode %}

{% code title="Погода" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-weather
```
{% endcode %}

{% code title="Подключения" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-connections
```
{% endcode %}

{% code title="Предустановленные расширения" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-shell-extensions
```
{% endcode %}

{% code title="Родительский контроль" overflow="wrap" %}
```bash
sudo pacman -Rns malcontent
```
{% endcode %}

{% code title="Сканер документов" overflow="wrap" %}
```bash
sudo pacman -Rns simple-scan
```
{% endcode %}

{% code title="Справка" overflow="wrap" %}
```bash
sudo pacman -Rns yelp
```
{% endcode %}

{% code title="Текстовый редактор" overflow="wrap" fullWidth="false" %}
```bash
sudo pacman -Rns gnome-text-editor
```
{% endcode %}

{% code title="Экскурсия" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-tour
```
{% endcode %}

{% code title="Центр приложений" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-software
```
{% endcode %}

{% code title="Часы" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-clocks
```
{% endcode %}

***

Удалить всё одной командой:

{% code overflow="wrap" %}
```bash
sudo pacman -Rns baobab epiphany totem snapshot gnome-maps gnome-contacts gnome-music gnome-weather gnome-connections simple-scan yelp gnome-text-editor gnome-tour gnome-software gnome-clocks malcontent
```
{% endcode %}



### Терминал вместо консоли

{% code title="Удалите консоль" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-console
```
{% endcode %}

{% code title="Установите терминал" overflow="wrap" %}
```bash
sudo pacman -S gnome-terminal
```
{% endcode %}

### Менеджер расширений

{% code overflow="wrap" %}
```bash
yay -S extension-manager
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