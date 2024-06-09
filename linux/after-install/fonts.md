# Шрифты

Установите базовый набор шрифтов:

{% tabs %}
{% tab title="pacman" %}
{% code overflow="wrap" %}
```bash
sudo pacman -S adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font
```
{% endcode %}
{% endtab %}

{% tab title="aura" %}
{% code overflow="wrap" %}
```bash
sudo aura -S adobe-source-sans-pro-fonts ttf-dejavu ttf-opensans noto-fonts freetype2 terminus-font ttf-bitstream-vera ttf-dejavu ttf-droid ttf-fira-mono ttf-fira-sans ttf-freefont ttf-inconsolata ttf-liberation libertinus-font
```
{% endcode %}
{% endtab %}
{% endtabs %}

Или установите все шрифты:

{% tabs %}
{% tab title="yay" %}
{% code overflow="wrap" %}
```bash
yay -S all-repository-fonts
```
{% endcode %}
{% endtab %}

{% tab title="aura" %}
{% code overflow="wrap" %}
```bash
sudo aura -A all-repository-fonts
```
{% endcode %}
{% endtab %}
{% endtabs %}

Набор шрифтов для терминала:

{% tabs %}
{% tab title="pacman" %}
{% code overflow="wrap" %}
```bash
sudo pacman -S nerd-fonts
```
{% endcode %}
{% endtab %}

{% tab title="aura" %}
```bash
sudo aura -S nerd-fonts
```
{% endtab %}
{% endtabs %}
