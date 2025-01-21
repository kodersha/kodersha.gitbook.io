---
description: >-
  Позволяет устанавливать и запускать приложения в изолированных контейнерах,
  обеспечивая совместимость между дистрибутивами, автоматическое управление
  зависимостями и безопасное обновление.
layout:
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: false
  pagination:
    visible: false
---

# Flatpak



### Установка

Установите `flatpak`:

<pre class="language-bash" data-overflow="wrap"><code class="lang-bash"><a data-footnote-ref href="#user-content-fn-1">aura</a> -S flatpak
</code></pre>

Добавьте репозиторий `flathub`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}



### Команды

* Основные  команды:
  * `flatpak install <имя-пакета>`: Установка приложения.
  * `flatpak run <имя-пакета>`: Запуск приложения.
  * `flatpak uninstall <имя-пакета>`: Удаление приложения.
  * `flatpak update`: Обновление приложений.
  * `flatpak list`: Список установленных приложений.
* Управление репозиториями:
  * `flatpak remote-add <имя-репозитория> <URL-репозитория>`: Добавление репозитория.
  * `flatpak remote-delete <имя-репозитория>`: Удаление репозитория.
  * `flatpak remotes`: Список текущих репозиториев.
* Управление  разрешениями:
  * `flatpak info --show-permissions <имя-пакета>`: Проверка разрешений приложения.
* Утилиты:
  * `flatpak info <имя-пакета>`: Информация о приложении.
  * `flatpak uninstall --unused`: Очистка кэша.
  * `flatpak repair && flatpak ps`: Диагностика и отладка.





***

{% embed url="https://flathub.org/ru" %}

[^1]: См. руководство по [aura](aura.md).
