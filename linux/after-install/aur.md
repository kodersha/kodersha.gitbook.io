# Пользовательский репозиторий

Пользовательский репозиторий Arch (Arch User Repository, AUR) - поддерживаемое сообществом хранилище программ для пользователей Arch.

Установите `yay` - менеджер пакетов AUR.

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}

***

### flatpak

{% code overflow="wrap" %}
```bash
sudo pacman -S flatpak
```
{% endcode %}

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
