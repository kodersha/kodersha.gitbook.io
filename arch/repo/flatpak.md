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



Установите `flatpak`:

{% code overflow="wrap" %}
```bash
aura -S flatpak
```
{% endcode %}

Добавьте репозиторий `flathub`:

{% code overflow="wrap" %}
```bash
flatpak remote-add --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```
{% endcode %}



#### Основные команды

*   Установка приложений

    {% code overflow="wrap" %}
    ```bash
    flatpak install <удалённый-репозиторий> <имя-пакета>
    ```
    {% endcode %}
*   Запуск приложений

    {% code overflow="wrap" %}
    ```bash
    flatpak run <имя-пакета>
    ```
    {% endcode %}
*   Удаление приложений

    {% code overflow="wrap" %}
    ```bash
    flatpak uninstall <имя-пакета>
    ```
    {% endcode %}
*   Обновление приложений

    {% code overflow="wrap" %}
    ```bash
    flatpak update
    ```
    {% endcode %}
*   Список установленных приложений

    {% code overflow="wrap" %}
    ```bash
    flatpak list
    ```
    {% endcode %}

#### Управление репозиториями

*   Добавление репозитория

    {% code overflow="wrap" %}
    ```bash
    flatpak remote-add <имя-репозитория> <URL-репозитория>
    ```
    {% endcode %}
*   Удаление репозитория

    {% code overflow="wrap" %}
    ```bash
    flatpak remote-delete <имя-репозитория>
    ```
    {% endcode %}
*   Список репозиториев

    {% code overflow="wrap" %}
    ```bash
    flatpak remotes
    ```
    {% endcode %}

#### Управление разрешениями

*   Проверка разрешений приложения

    {% code overflow="wrap" %}
    ```bash
    flatpak info --show-permissions <имя-пакета>
    ```
    {% endcode %}
* Используйте приложение [Flatseal](https://flathub.org/apps/details/com.github.tchx84.Flatseal) для редактирования разрешений.

#### Утилиты

*   Проверка информации о приложении

    {% code overflow="wrap" %}
    ```bash
    flatpak info <имя-пакета>
    ```
    {% endcode %}
*   Очистка кэша

    {% code overflow="wrap" %}
    ```
    flatpak uninstall --unused
    ```
    {% endcode %}
*   **Д**иагностика и отладка

    {% code overflow="wrap" %}
    ```bash
    flatpak repair
    flatpak ps
    ```
    {% endcode %}
*   Запуск команды в окружении приложения

    {% code overflow="wrap" %}
    ```bash
    flatpak enter <ид-процесса> <команда>
    ```
    {% endcode %}

#### Пример использования:

*   Установка приложения из Flathub:

    {% code overflow="wrap" %}
    ```bash
    flatpak install flathub com.spotify.Client
    ```
    {% endcode %}
*   Запуск приложения:

    {% code overflow="wrap" %}
    ```bash
    flatpak run com.spotify.Client
    ```
    {% endcode %}

