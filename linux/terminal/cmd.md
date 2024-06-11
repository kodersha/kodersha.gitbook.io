# Команды

### Установка

Найти пакет в официальном репозитории:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">sudo pacman -Ss <a data-footnote-ref href="#user-content-fn-1">pkg</a>
</code></pre>

Установить пакет из официального репозитория:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">sudo pacman -S <a data-footnote-ref href="#user-content-fn-2">pkg</a>
</code></pre>

{% embed url="https://archlinux.org/packages/" %}



### Обновление

Обновить все пакеты официального репозитория:

{% code overflow="wrap" %}
```bash
sudo pacman -Syu
```
{% endcode %}



### Удаление

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">sudo pacman -Rns <a data-footnote-ref href="#user-content-fn-3">pkg</a>
</code></pre>

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

[^1]: Название пакета

[^2]: Название пакета

[^3]: Название пакета
