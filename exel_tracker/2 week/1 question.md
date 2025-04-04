# Чем reverse proxy отличается от forward proxy?

Reverse proxy и forward proxy — это два разных типа проксирующих серверов, и их основное различие связано с тем, как они обрабатывают трафик и кто их использует. Вот основные отличия между ними:

# 1. Forward Proxy (Прямой прокси):

- Кто использует: Обычно используется клиентами (например, компьютерами пользователей) для доступа к интернет-ресурсам.

- Как работает: Когда пользователь (клиент) делает запрос в интернет, его запрос сначала отправляется на прокси-сервер. Прокси-сервер затем передает этот запрос на целевой сервер в интернете, а затем возвращает ответ обратно пользователю.

- Назначение:

  - Скрытие IP-адреса клиента.

  - Блокировка доступа к определенным сайтам.

  - Управление трафиком, например, кэширование.

  - Фильтрация контента, например, для школьных или корпоративных сетей.

- Пример использования: Компания может использовать forward proxy для того, чтобы ограничить доступ сотрудников к определенным сайтам или отслеживать их интернет-активность.

# 2. Reverse Proxy (Обратный прокси):

- Кто использует: Обычно используется серверами (например, веб-серверами) для обработки входящего трафика от клиентов.

- Как работает: Когда клиент (например, браузер) отправляет запрос на сервер, запрос сначала попадает на обратный прокси-сервер, который перенаправляет его на соответствующий сервер (например, веб-приложение). Ответ от сервера идет обратно через обратный прокси к клиенту.

- Назначение:

  - Балансировка нагрузки между несколькими серверами.

  - Скрытие структуры внутренней сети от внешнего мира.

  - Кэширование данных для ускорения отклика.

  - Обеспечение безопасности и защиты от DDoS-атак.

- Пример использования: Веб-сайт, который использует несколько серверов для обработки запросов, может поставить перед этими серверами обратный прокси, чтобы распределять трафик и контролировать доступ.

# Визуализация:

Forward Proxy:
Клиент → Прокси-сервер → Интернет

Reverse Proxy:
Клиент → Обратный прокси → Веб-сервер

Основные отличия:

| Характеристика      | Forward Proxy                                 | Reverse Proxy                                     |
|---------------------|-----------------------------------------------|---------------------------------------------------|
| Кто использует      | Клиенты (например, пользователи, устройства)  | Серверы (например, веб-серверы)                   |
| Направление трафика | Из клиента в интернет                         | Из интернета на сервер                            | 
| Использование       | Фильтрация, анонимизация, ограничение доступа | Балансировка нагрузки, безопасность, кэширование  |
| Скрытие             | Скрывает клиента (IP адрес)                   | Скрывает сервер (IP адрес, внутреннюю структуру)  |

Таким образом, forward proxy работает "от клиента к серверу", а reverse proxy — наоборот, "от сервера к клиенту".