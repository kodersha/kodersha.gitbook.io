# Репозитории

{% tabs %}
{% tab title="fedora" %}
Подключаем репозитории rpmfusion free и nonfree.

{% code overflow="wrap" %}
```bash
sudo dnf install https://mirrors.rpmfusion.org/free/fedora/rpmfusion-free-release-$(rpm -E %fedora).noarch.rpm https://mirrors.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-$(rpm -E %fedora).noarch.rpm
```
{% endcode %}
{% endtab %}

{% tab title="arch" %}
Пользовательский репозиторий Arch (Arch User Repository, AUR) — поддерживаемое сообществом хранилище программ для пользователей Arch.

Установим yay - менеджер пакетов AUR.

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}
{% endtab %}
{% endtabs %}

***

### flatpak

{% code title="Репозиторий flathub для system" overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}

{% code title="Репозиторий flathub для user" overflow="wrap" %}
```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}
