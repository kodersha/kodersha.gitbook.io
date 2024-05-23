# Пользовательские репозитории

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

Установка yay - менеджера пакетов AUR.

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}
{% endtab %}
{% endtabs %}
