# Команды

### Установка

Найти пакет в официальном репозитории:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">sudo pacman -Ss <a data-footnote-ref href="#user-content-fn-1">pkg</a>
</code></pre>

{% embed url="https://archlinux.org/packages/" %}

Установить пакет из официального репозитория:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">sudo pacman -S <a data-footnote-ref href="#user-content-fn-2">pkg</a>
</code></pre>



Найти пакет в репозитории AUR:

<pre class="language-bash"><code class="lang-bash">yay -Ss <a data-footnote-ref href="#user-content-fn-3">pkg</a>
</code></pre>

{% embed url="https://aur.archlinux.org/packages" %}

Установить пакет из AUR:

<pre><code>yay -S <a data-footnote-ref href="#user-content-fn-4">pkg</a>
</code></pre>



### Обновление

Обновить пакеты:

{% code overflow="wrap" %}
```bash
sudo pacman -Syu
```
{% endcode %}



### Удаление

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash">sudo pacman -Rns <a data-footnote-ref href="#user-content-fn-5">pkg</a>
</code></pre>

{% hint style="warning" %}
Опция `-Rns` используется для удаления указанного пакета и всех его ненужных зависимостей (т.е. те зависимости, которые не требуются другими установленными пакетами).

Опция `-Rsc` используется для удаления указанного пакета и всех его зависимостей, независимо от того, требуются ли они другими пакетами. Эта опция может привести к удалению большого количества пакетов, поэтому её следует использовать с осторожностью.
{% endhint %}



### Очистка

Удаление ненужных пакетов с зависимостями:

{% code overflow="wrap" %}
```bash
sudo pacman -Rns $(pacman -Qdtq)
```
{% endcode %}

Очистка кэша пакетов:

{% code overflow="wrap" %}
```bash
sudo pacman -Sc
```
{% endcode %}

Очистка кэша AUR:

{% code overflow="wrap" %}
```bash
yay -Sc
```
{% endcode %}

[^1]: Название пакета

[^2]: Название пакета

[^3]: Название пакета

[^4]: Название пакета

[^5]: Название пакета
