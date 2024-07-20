# Команды

### Установка

#### pacman

Пакетный менеджер Arch Linux. Позволяет устанавливать, обновлять, удалять пакеты и их зависимости.

<pre class="language-bash" data-title="Найти пакет в репозитории:" data-overflow="wrap"><code class="lang-bash">sudo pacman -Ss <a data-footnote-ref href="#user-content-fn-1">pkg</a>
</code></pre>

<pre class="language-bash" data-title="Установить пакет:" data-overflow="wrap"><code class="lang-bash">sudo pacman -S <a data-footnote-ref href="#user-content-fn-2">pkg</a>
</code></pre>

{% embed url="https://archlinux.org/packages/" %}

#### yay

Помощник для управления пакетами в Arch Linux, упрощает установку и управление пакетами из AUR (см. После установки - Репозитории).

{% content-ref url="../after-install/repo.md" %}
[repo.md](../after-install/repo.md)
{% endcontent-ref %}

<pre class="language-bash" data-title="Найти пакет в репозитории AUR:" data-overflow="wrap"><code class="lang-bash">yay -Ss <a data-footnote-ref href="#user-content-fn-3">pkg</a>
</code></pre>

<pre data-title="Установить пакет из AUR:" data-overflow="wrap"><code>yay -S <a data-footnote-ref href="#user-content-fn-4">pkg</a>
</code></pre>

{% embed url="https://aur.archlinux.org/packages" %}



### Обновление

{% code title="Обновить пакеты:" overflow="wrap" %}
```bash
sudo pacman -Syu
```
{% endcode %}

Или с помощью `topgrade` (см. Терминал - Расширения):

```bash
topgrade
```

{% content-ref url="ext.md" %}
[ext.md](ext.md)
{% endcontent-ref %}



### Удаление

<pre class="language-bash" data-title="Удалить пакет:" data-overflow="wrap"><code class="lang-bash">sudo pacman -Rns <a data-footnote-ref href="#user-content-fn-5">pkg</a>
</code></pre>

{% hint style="warning" %}
Опция `-Rns` используется для удаления указанного пакета и всех его ненужных зависимостей (т.е. те зависимости, которые не требуются другими установленными пакетами).

Опция `-Rsc` используется для удаления указанного пакета и всех его зависимостей, независимо от того, требуются ли они другими пакетами. Эта опция может привести к удалению большого количества пакетов, поэтому её следует использовать с осторожностью.
{% endhint %}



### Очистка

{% code title="Удаление неиспользуемых пакетов с зависимостями:" overflow="wrap" %}
```bash
sudo pacman -Rns $(pacman -Qdtq)
```
{% endcode %}

{% code title="Очистка кэша пакетов:" overflow="wrap" %}
```bash
sudo pacman -Sc
```
{% endcode %}

{% code title="Очистка кэша AUR:" overflow="wrap" %}
```bash
yay -Sc
```
{% endcode %}

[^1]: Название пакета

[^2]: Название пакета

[^3]: Название пакета

[^4]: Название пакета

[^5]: Название пакета