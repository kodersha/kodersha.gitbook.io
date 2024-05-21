# Пользовательский репозиторий AUR

Yay это менеджер пакетов AUR - [Arch User Repository](#user-content-fn-1)[^1].

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}

[^1]: Пользовательский репозиторий Arch (Arch User Repository, AUR) — поддерживаемое сообществом хранилище программ для пользователей Arch. AUR был создан с целью организации совместного доступа к новым пакетам, которые были созданы сообществом.
