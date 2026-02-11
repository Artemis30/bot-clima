# 🌤️ Daily Telegram Weather Bot

Bot de Telegram automatizado que envía un informe diario del clima para dos ciudades configurables utilizando **OpenWeatherMap API** y ejecutado mediante **GitHub Actions**.

Diseñado con un enfoque minimalista, seguro y fácilmente extensible.

---

## 📌 Overview

Este proyecto implementa un sistema automatizado que:

- Consulta el clima actual de dos ciudades
- Genera mensajes personalizados según las condiciones meteorológicas
- Envía automáticamente el informe a un chat de Telegram
- Se ejecuta una vez al día mediante GitHub Actions

El sistema está completamente desacoplado de credenciales sensibles gracias al uso de **variables de entorno y GitHub Secrets**.

---

## 🧱 Arquitectura

Flujo de ejecución:

1. El workflow programado ejecuta el script.
2. El script obtiene las variables de entorno.
3. Consulta la API meteorológica.
4. Procesa la respuesta.
5. Genera un mensaje con lógica condicional.
6. Envía el informe a Telegram.

---

## ⚙️ Configuración

El proyecto depende exclusivamente de variables de entorno para su configuración.

### 🔐 Variables necesarias

| Variable            | Descripción |
|---------------------|------------|
| `WEATHER_API_KEY`   | API Key de OpenWeatherMap |
| `TELEGRAM_TOKEN`    | Token del bot de Telegram |
| `CHAT_ID`           | ID del chat destino |
| `CIUDAD`            | Ciudad principal |
| `CIUDAD2`           | Ciudad secundaria |

Estas variables deben configurarse como **GitHub Secrets** en: