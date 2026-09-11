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

**Production-oriented Xray configuration for Remnawave**

`VLESS` · `REALITY` · `TCP` · `XHTTP` · `gRPC` · `Self-Steal` · `Routing`

</div>

---

## ✦ Overview

Этот репозиторий содержит готовую конфигурацию **Xray Core** для использования с **Remnawave**, а также шаблон клиентской подписки с собственной системой маршрутизации.

### Server

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
                            Internet
```

---

## ✦ Features

* `VLESS + REALITY`
* `TCP` transport
* `XHTTP` transport
* `gRPC` transport
* Self-Steal architecture
* IPv4 DNS strategy
* DNS `1.1.1.1` + `9.9.9.9`
* HTTP/TLS sniffing
* Private IP blocking
* Private domain blocking
* BitTorrent blocking
* Custom client-side routing
* `proxy / direct / block` routing model
* Russian traffic → `direct`
* Selected domains → `proxy`
* Local SOCKS5 / HTTP inbounds
* Traffic statistics support

---

## ✦ Connection Methods

| Transport |  Security |    Port | Tag               |
| :-------: | :-------: | ------: | :---------------- |
|   `TCP`   | `REALITY` | `56789` | `TCP-SELFSTEAL`   |
|  `XHTTP`  | `REALITY` | `56790` | `XHTTP-SELFSTEAL` |
|   `gRPC`  | `REALITY` | `56791` | `GRPC-SELFSTEAL`  |

> [!TIP]
> Наличие нескольких транспортов позволяет использовать разные варианты подключения в зависимости от клиента и сети.

---

# ⚙️ Installation

## 1. Requirements

Перед началом убедитесь, что у вас есть:

* [x] Remnawave
* [x] Xray Core
* [x] VPS / сервер
* [x] REALITY key pair
* [x] Short ID
* [x] Self-Steal domain
* [x] открытые порты `56789`, `56790`, `56791`

---

## 2. REALITY Parameters

В конфигурации используются следующие значения:

```text
PRIVATE KEY
SHORT ID
SERVER NAME
TARGET
FINGERPRINT
```

Основной блок:

```json
{
  "target": "127.0.0.1:8081",
  "spiderX": "/",
  "shortIds": [
    "YOUR_SHORT_ID"
  ],
  "privateKey": "YOUR_PRIVATE_KEY",
  "fingerprint": "firefox",
  "serverNames": [
    "YOUR_SELFSTEAL_DOMAIN"
  ]
}
```

### Replace

```diff
- YOUR_SHORT_ID
- YOUR_PRIVATE_KEY
- YOUR_SELFSTEAL_DOMAIN
+ YOUR_REAL_VALUES
```

> [!CAUTION]
> Никогда не публикуйте `privateKey`, UUID
