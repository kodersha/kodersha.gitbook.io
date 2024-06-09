# Пользовательский репозиторий

Пользовательский репозиторий AUR (Arch User Repository) - поддерживаемое сообществом хранилище программ для пользователей Arch.

[aur.archlinux.org](https://aur.archlinux.org)

***

### yay

Установите `yay` - менеджер пакетов AUR.

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -si
```
{% endcode %}

Теперь можно устанавливать пакеты из репозитория AUR.

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">yay -S <a data-footnote-ref href="#user-content-fn-1">pkg</a>
</code></pre>

[github.com/jguer/yay](https://github.com/Jguer/yay)

### aura

Альтернативный, более безопасный, менеджер официальных и AUR пакетов.

{% code overflow="wrap" %}
```bash
sudo pacman --needed git base-devel && git clone https://aur.archlinux.org/aura-bin.git && cd aura-bin && makepkg -si
```
{% endcode %}

Теперь можно устанавливать пакеты из репозитория AUR.

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">sudo aura -A <a data-footnote-ref href="#user-content-fn-2">pkg</a>
</code></pre>

[github.com/fosskers/aura](https://github.com/fosskers/aura)

### flatpak

{% code title="Установите flatpak" overflow="wrap" %}
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

[^1]: Название пакета AUR

[^2]: Название пакета AUR
