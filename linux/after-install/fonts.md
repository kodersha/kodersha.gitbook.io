# Шрифты

Установите базовый набор шрифтов:

{% code overflow="wrap" %}
```bash
sudo pacman -S adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font
```
{% endcode %}

Набор шрифтов для терминала:

{% code overflow="wrap" %}
```bash
sudo pacman -S nerd-fonts
```
{% endcode %}



Или установите все шрифты:

{% code overflow="wrap" %}
```bash
yay -S all-repository-fonts
```
{% endcode %}



### Шрифты Windows

Дополнительно можно добавить шрифты из Windows 11.&#x20;

{% file src="../../.gitbook/assets/windows.zip" %}

Скачайте архив, распакуйте и скопируйте папку `windows` в домашнюю папку:

```bash
~/.local/share/fonts
```

Обновите кэш шрифтов:

```bash
fc-cache -v
```
