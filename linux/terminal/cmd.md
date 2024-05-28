# Команды

{% code title="Обновить все пакеты" overflow="wrap" %}
```bash
sudo pacman -Syu
```
{% endcode %}

### Установка

{% code title="Найти пакет" overflow="wrap" %}
```bash
sudo pacman -Ss ...
```
{% endcode %}

{% code title="Установить пакет" overflow="wrap" %}
```bash
sudo pacman -S ...
```
{% endcode %}

### Удаление

{% code title="Удалить пакет" overflow="wrap" %}
```bash
sudo pacman -Rns ...
```
{% endcode %}

{% hint style="warning" %}
Опция `-Rns` используется для удаления указанного пакета и всех его ненужных зависимостей (т.е. те зависимости, которые не требуются другими установленными пакетами).

Опция `-Rsc` используется для удаления указанного пакета и всех его зависимостей, независимо от того, требуются ли они другими пакетами. Эта опция может привести к удалению большого количества пакетов, поэтому её следует использовать с осторожностью.
{% endhint %}

### Очистка

{% code title="Удаление ненужных пакетов с зависимостями" overflow="wrap" %}
```bash
sudo pacman -Rns $(pacman -Qdtq)
```
{% endcode %}

{% code title="Очистка кэша пакетов" overflow="wrap" %}
```bash
sudo pacman -Sc
```
{% endcode %}

{% code title="Очистка кэша AUR" overflow="wrap" %}
```bash
yay -Sc
```
{% endcode %}
