# GNOME

### Удаление предустановленных пакетов

Обычно я пользуюсь оболочкой GNOME и после установки ОС удаляю ненужные, предустановленные пакеты.

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

{% code title="Календарь" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-calendar
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

{% code title="Системный монитор" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-system-monitor
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

#### Удалить всё одной командой:

{% code overflow="wrap" %}
```bash
sudo pacman -Rns baobab epiphany totem snapshot gnome-maps gnome-contacts gnome-music gnome-weather gnome-connections simple-scan yelp gnome-text-editor gnome-tour gnome-software gnome-clocks gnome-calendar gnome-characters gnome-system-monitor gnome-font-viewer gnome-logs gnome-remote-desktop gnome-shell-extensions gnome-backgrounds gnome-user-docs malcontent orca rygel
```
{% endcode %}

{% hint style="warning" %}
Удаление пакета `malcontent` удаляет `flatpak` в качестве зависимости. Если он всё же нужен, установите командой `sudo pacman -S flatpak`
{% endhint %}



### Отключение лишних служб

{% code title="Служба графического планешта wacom" overflow="wrap" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.Wacom.service
```
{% endcode %}

{% code title="Служба печати" overflow="wrap" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.PrintNotifications.service:
```
{% endcode %}

{% code title="Служба специальных возможностей" overflow="wrap" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.A11ySettings.service
```
{% endcode %}

{% code title="Служба автоматической блокировки экрана" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.ScreensaverProxy.service
```
{% endcode %}

{% code title="Служба общего доступа" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.Sharing.service
```
{% endcode %}

{% code title="Служба интеграции с картридером" overflow="wrap" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.Smartcard.service
```
{% endcode %}



### Патчи производительности

{% code overflow="wrap" %}
```bash
yay -S gnome-shell-performance mutter-performance
```
{% endcode %}



### Терминал вместо консоли

{% code title="Установите терминал" overflow="wrap" %}
```bash
sudo pacman -S gnome-terminal
```
{% endcode %}

{% code title="Удалите консоль" overflow="wrap" %}
```bash
sudo pacman -Rns gnome-console
```
{% endcode %}



### Менеджер расширений GNOME

{% code overflow="wrap" %}
```bash
yay -S extension-manager
```
{% endcode %}

{% embed url="https://mattjakeman.com/apps/extension-manager.html" %}



### Редактор меню

{% code overflow="wrap" %}
```bash
yay -S libre-menu-editor
```
{% endcode %}

{% embed url="https://codeberg.org/libre-menu-editor/libre-menu-editor" %}



### Смена раскладки клавиатуры на Shift Alt

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
