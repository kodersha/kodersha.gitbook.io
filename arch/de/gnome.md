# GNOME

### Удаление предустановленных пакетов

Обычно я пользуюсь оболочкой GNOME и после установки ОС удаляю ненужные, предустановленные пакеты.

{% code title="Анализатор использования дисков" overflow="wrap" %}
```bash
aura -Rsu baobab
```
{% endcode %}

{% code title="Веб-брауpер" overflow="wrap" %}
```bash
aura -Rsu epiphany
```
{% endcode %}

{% code title="Видео" overflow="wrap" %}
```bash
aura -Rsu totem
```
{% endcode %}

{% code title="Камера" overflow="wrap" %}
```bash
aura -Rsu snapshot
```
{% endcode %}

{% code title=" Карты" overflow="wrap" %}
```bash
aura -Rsu gnome-maps
```
{% endcode %}

{% code title="Календарь" overflow="wrap" %}
```bash
aura -Rsu gnome-calendar
```
{% endcode %}

{% code title="Контакты" overflow="wrap" %}
```bash
aura -Rsu gnome-contacts
```
{% endcode %}

{% code title="Музыка" overflow="wrap" %}
```bash
aura -Rsu gnome-music
```
{% endcode %}

{% code title="Погода" overflow="wrap" %}
```bash
aura -Rsu gnome-weather
```
{% endcode %}

{% code title="Подключения" overflow="wrap" %}
```bash
aura -Rsu gnome-connections
```
{% endcode %}

{% code title="Предустановленные расширения" overflow="wrap" %}
```bash
aura -Rsu gnome-shell-extensions
```
{% endcode %}

{% code title="Родительский контроль" overflow="wrap" %}
```bash
aura -Rsu malcontent
```
{% endcode %}

{% code title="Системный монитор" overflow="wrap" %}
```bash
aura -Rsu gnome-system-monitor
```
{% endcode %}

{% code title="Сканер документов" overflow="wrap" %}
```bash
aura -Rsu simple-scan
```
{% endcode %}

{% code title="Справка" overflow="wrap" %}
```bash
aura -Rsu yelp
```
{% endcode %}

{% code title="Текстовый редактор" overflow="wrap" fullWidth="false" %}
```bash
aura -Rsu gnome-text-editor
```
{% endcode %}

{% code title="Экскурсия" overflow="wrap" %}
```bash
aura -Rsu gnome-tour
```
{% endcode %}

{% code title="Центр приложений" overflow="wrap" %}
```bash
aura -Rsu gnome-software
```
{% endcode %}

{% code title="Часы" overflow="wrap" %}
```bash
aura -Rsu gnome-clocks
```
{% endcode %}

#### Удалить всё одной командой:

{% code overflow="wrap" %}
```bash
aura -Rsu baobab epiphany totem snapshot gnome-maps gnome-contacts gnome-music gnome-weather gnome-connections simple-scan yelp gnome-text-editor gnome-tour gnome-software gnome-clocks gnome-calendar gnome-characters gnome-system-monitor gnome-font-viewer gnome-logs gnome-remote-desktop gnome-backgrounds gnome-user-docs gnome-user-share gnome-menus gnome-tweaks malcontent evince sushi loupe orca rygel gvfs-afc gvfs-dnssd gvfs-goa gvfs-gphoto2 gvfs-mtp gvfs-nfs gvfs-smb gvfs-wsdd gvfs-google gvfs-onedrive htop vim nm-connection-editor network-manager-applet
```
{% endcode %}

{% hint style="warning" %}
`flatpak` будет удалён как зависимость при удалении пакета родительского контроля `malcontent`, если нужен верните: `aura -S flatpak`. Также из предустановленных пакетов я удаляю `htop` и `vim`.
{% endhint %}



### Отключение лишних служб

{% code title="Служба графического планешта wacom" overflow="wrap" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.Wacom.service
```
{% endcode %}

{% code title="Служба печати" overflow="wrap" %}
```bash
systemctl --user mask org.gnome.SettingsDaemon.PrintNotifications.service
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



### Удаление лишних ярлыков

{% code overflow="wrap" %}
```bash
sudo rm /usr/share/applications/avahi-discover.desktop && sudo rm /usr/share/applications/bssh.desktop && sudo rm /usr/share/applications/bvnc.desktop && sudo rm /usr/share/applications/qv4l2.desktop && sudo rm /usr/share/applications/qvidcap.desktop && sudo rm /usr/share/applications/org.gnome.OnlineAccounts.OAuth2.desktop && sudo rm /usr/share/applications/nautilus-autorun-software.desktop && sudo rm /usr/share/applications/gcm-import.desktop && sudo rm /usr/share/applications/org.gnome.Extensions.desktop
```
{% endcode %}



### Терминал вместо консоли

{% code overflow="wrap" %}
```bash
aura -S gnome-terminal && aura -Rsu gnome-console
```
{% endcode %}



### Редактор меню

<figure><img src="../../.gitbook/assets/libre-menu-editor.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install page.codeberg.libre_menu_editor.LibreMenuEditor
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -A libre-menu-editor
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Менеджер расширений GNOME

<figure><img src="../../.gitbook/assets/extension-manager.png" alt=""><figcaption></figcaption></figure>

{% tabs %}
{% tab title="flatpak" %}
{% code overflow="wrap" %}
```bash
flatpak install com.mattjakeman.ExtensionManager
```
{% endcode %}
{% endtab %}

{% tab title="pkg" %}
{% code overflow="wrap" %}
```bash
aura -A extension-manager
```
{% endcode %}
{% endtab %}
{% endtabs %}



### Раскладка клавиатуры

Смена раскладки клавиатуры на `shift` + `alt`

{% code overflow="wrap" %}
```bash
gsettings set org.gnome.desktop.wm.keybindings switch-input-source-backward "['<Shift>Alt_L']" && gsettings set org.gnome.desktop.wm.keybindings switch-input-source "['<Alt>Shift_L']"
```
{% endcode %}
