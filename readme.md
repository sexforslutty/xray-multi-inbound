<div align="center">

```text
█   █ █   █ ████   ███  █   █ █   █ █   █ ████    
█░ █ ░█░  █░█░░░█ █ ░░█  █ █ ░█░  █░██ ██░ ░░░█   
███ ░ █░░ █░████░░█░ ░█░  █ ░ █░░ █░█░█ █░░███░░  
█░░█ ░█░░ █░█░░█░ █░░ █░░ █░ ░█░░ █░█░░░█░░ ░░█ ░ 
█░░░█  ███ ░█░░░█░ ███ ░░ █░░  ███ ░█░░ █░████░░  
 ░░  ░  ░░░ ░░░  ░  ░░░ ░  ░░   ░░░ ░░░  ░░░░░░ ░ 
  ░   ░  ░░░  ░   ░  ░░░    ░    ░░░  ░   ░ ░░░░  
```

### `kur0yum3` · Xray × Remnawave

[![Xray](https://img.shields.io/badge/Xray-Core-000000?style=for-the-badge\&logo=xray\&logoColor=white)](https://github.com/XTLS/Xray-core)
[![Remnawave](https://img.shields.io/badge/Remnawave-111827?style=for-the-badge)](https://github.com/remnawave)
[![VLESS](https://img.shields.io/badge/VLESS-REALITY-5865F2?style=for-the-badge)](https://github.com/XTLS/Xray-core)
[![TCP](https://img.shields.io/badge/TCP-56789-22C55E?style=for-the-badge)](#)
[![XHTTP](https://img.shields.io/badge/XHTTP-56790-F59E0B?style=for-the-badge)](#)
[![gRPC](https://img.shields.io/badge/gRPC-56791-E11D48?style=for-the-badge)](#)

**Производительная конфигурация Xray Core для Remnawave**

`VLESS` · `REALITY` · `TCP` · `XHTTP` · `gRPC` · `Self-Steal` · `Routing`

</div>

---

## ✦ Обзор

Этот репозиторий содержит готовую конфигурацию **Xray Core** для использования совместно с **Remnawave**, а также шаблон клиентской подписки с собственной системой маршрутизации.

Конфигурация ориентирована на несколько вариантов подключения через `VLESS + REALITY` и поддерживает транспортные протоколы `TCP`, `XHTTP` и `gRPC`.

### Архитектура

```text
                     ┌───────────────────────┐
                     │       REMNAWAVE       │
                     └───────────┬───────────┘
                                 │
                                 ▼
                     ┌───────────────────────┐
                     │       XRAY CORE       │
                     └───────────┬───────────┘
                                 │
              ┌──────────────────┼──────────────────┐
              │                  │                  │
              ▼                  ▼                  ▼
        ┌───────────┐      ┌───────────┐      ┌───────────┐
        │   VLESS   │      │   VLESS   │      │   VLESS   │
        │    TCP    │      │   XHTTP   │      │   gRPC    │
        │   :56789  │      │   :56790  │      │   :56791  │
        └─────┬─────┘      └─────┬─────┘      └─────┬─────┘
              │                  │                  │
              └──────────────────┼──────────────────┘
                                 ▼
                         ┌──────────────┐
                         │    REALITY   │
                         └──────┬───────┘
                                ▼
                         Self-Steal Target
                                │
                                ▼
                            Интернет
```

---

## ✦ Возможности

* `VLESS + REALITY`
* `TCP` transport
* `XHTTP` transport
* `gRPC` transport
* Self-Steal архитектура
* DNS-стратегия только через IPv4
* DNS-серверы `1.1.1.1` + `9.9.9.9`
* HTTP/TLS sniffing
* Блокировка приватных IP-адресов
* Блокировка приватных доменов
* Блокировка BitTorrent
* Пользовательская маршрутизация на стороне клиента
* Модель маршрутизации `proxy / direct / block`
* Российский трафик → `direct`
* Выбранные домены → `proxy`
* Локальные `SOCKS5` / `HTTP` inbounds
* Поддержка статистики трафика

---

## ✦ Способы подключения

| Транспорт | Безопасность |    Порт | Тег               |
| :-------: | :----------: | ------: | ----------------- |
|   `TCP`   |   `REALITY`  | `56789` | `TCP-SELFSTEAL`   |
|  `XHTTP`  |   `REALITY`  | `56790` | `XHTTP-SELFSTEAL` |
|   `gRPC`  |   `REALITY`  | `56791` | `GRPC-SELFSTEAL`  |

 


