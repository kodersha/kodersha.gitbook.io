# Базовые команды терминала

{% tabs %}
{% tab title="arch" %}
### Менеджер пакетов pacman

{% code title="Обновить все пакеты" overflow="wrap" %}
```bash
sudo pacman -Syu
```
{% endcode %}

{% code title="Установить пакет" overflow="wrap" %}
```bash
sudo pacman -S ...
```
{% endcode %}

{% code title="Найти пакет" overflow="wrap" %}
```bash
sudo pacman -Ss ...
```
{% endcode %}

{% code title="Удалить пакет" overflow="wrap" %}
```bash
sudo pacman -Rsc ...
```
{% endcode %}
{% endtab %}

{% tab title="nixos" %}
{% code title="Собрать билд из папки конфигурации" overflow="wrap" %}
```bash
sudo nixos-rebuild swith --flake .#travkina
```
{% endcode %}

{% code title="Очистка" overflow="wrap" %}
```bash
sudo nix-collect-garbadge -d
```
{% endcode %}

{% code title="Удлаить устаревшие билды" overflow="wrap" %}
```bash
sudo nix-env --delete-generationbs old
```
{% endcode %}

{% code title="Оптимизация, удаление лишних зависимостей" overflow="wrap" %}
```bash
sudo nix-store --optimise
```
{% endcode %}
{% endtab %}
{% endtabs %}
