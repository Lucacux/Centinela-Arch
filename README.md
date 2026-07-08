# Centinela-Arch

Variante del bot de monitoreo **Centinela** adaptada para el servidor **Arch Linux** (`server-mbp`). Es el mismo bot que [`Centinela-Pentium`](https://github.com/Lucacux/Centinela-Pentium), con el código ajustado a las particularidades del host Arch (servicios systemd, rutas y comandos propios de esa máquina).

Monitorea el host y reporta a Discord: estado de servicios systemd, intentos de SSH/brute-force, uso de swap y temperatura, con panel interactivo y loop de autoheal.

## Configuración

Copiar `.env.example` a `.env` y completar con los valores reales:

```bash
cp .env.example .env
# editar .env con el token, channel id y parámetros del host
```

| Variable | Descripción |
|---|---|
| `DISCORD_TOKEN` | Token del bot de Discord (secreto). |
| `DISCORD_CHANNEL_ID` | ID del canal donde reporta. |
| `SERVER_NAME` | Nombre del host (ej. `arch`). |
| `DEBUG_MODE` | `true`/`false`. |
| `BACKUP_PATH` | Ruta de backups a vigilar. |
| `SAFE_SUBNETS` | Prefijos de subredes consideradas seguras. |
| `WATCHED_SERVICES` | Servicios systemd a monitorear (coma-separados). |
| `ALLOWED_RESTART` | Servicios que el bot puede reiniciar. |
| `SWAP_ALERT_PCT` | Umbral de alerta de swap (%). |
| `TEMP_ALERT_C` | Umbral de alerta de temperatura (°C). |

## Ejecución

```bash
python -m venv venv && source venv/bin/activate
pip install -r requirements.txt
python main.py
```

Corre como servicio systemd (`discord-bot.service`) en el Arch.
