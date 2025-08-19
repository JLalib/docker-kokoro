# Kokoro TTS | Texto a voz autoalojado de alto rendimiento

Este proyecto despliega Kokoro, un modelo de texto a voz (TTS) ligero y de código abierto, usando Docker Compose.
La configuración permite convertir texto en voz de alta calidad de forma eficiente, ya sea en proyectos personales o en entornos de producción.

## 📦 Requisitos

- Docker
- Docker Compose

## 📂 Estructura de Archivos
```
.
└── compose.yml
```

## ⚙️ Configuración

Revisa el archivo `compose.yml`:

```yaml
services:
  kokoro:
    image: ghcr.io/remsky/kokoro-fastapi-cpu:latest
    container_name: kokoro
    restart: unless-stopped
    ports:
      - "8880:8880"

#  kokoro:
#    image: ghcr.io/remsky/kokoro-fastapi-gpu:latest    # GPU Nvidia
#    container_name: kokoro
#    restart: unless-stopped
#    ports:
#        - "8880:8880"
#    deploy:
#        resources:
#            reservations:
#                devices:
#                    - driver: nvidia
#                      count: all
#                      capabilities:
#                          - gpu
```

👉 Nota: La configuración por defecto utiliza la imagen para **CPU**.  
👉 Si tienes una **GPU Nvidia**, comenta la sección de CPU y descomenta la de GPU.

## 🚀 Uso

Levantar el contenedor:

```bash
docker compose up -d
```

Detenerlo:

```bash
docker compose down
```

Revisar logs:

```bash
docker compose logs -f
```

## 🌐 Acceso a Kokoro

Una vez iniciado, abre en tu navegador:

👉 [http://localhost:8880](http://localhost:8880)

Si corres Kokoro en otra máquina, sustituye `localhost` por la IP de tu servidor.

## 🛠 Variables de Entorno

La configuración del servicio se maneja a través de la imagen de Docker.
Para opciones adicionales y documentación completa de la API, consulta el repositorio del proyecto:

- Implementación con FastAPI: [Kokoro-FastAPI](https://github.com/remsky/Kokoro-FastAPI)

## 🔗 Enlaces de Referencia

- Modelo Kokoro en Hugging Face: [hexgrad/Kokoro-82M](https://huggingface.co/hexgrad/Kokoro-82M)

