# Пользовательский репозиторий

Пользовательский репозиторий AUR (Arch User Repository) - поддерживаемое сообществом хранилище программ для пользователей Arch.

{% embed url="https://aur.archlinux.org/packages" %}



### yay

Установите `yay` - менеджер пакетов AUR.

{% code overflow="wrap" %}
```bash
sudo pacman -S --needed git base-devel && git clone https://aur.archlinux.org/yay.git && cd yay && makepkg -rsi && cd .. && rm -rf yay
```
{% endcode %}

Теперь можно устанавливать пакеты из репозитория AUR.

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">yay -S <a data-footnote-ref href="#user-content-fn-1">pkg</a>
</code></pre>

{% embed url="https://github.com/Jguer/yay" %}



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

{% embed url="https://flatpak.org/" %}

[^1]: Название пакета AUR
