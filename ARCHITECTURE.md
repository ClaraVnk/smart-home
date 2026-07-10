# Architecture

System overview. Real IPs and the actual domain are intentionally replaced
with placeholders.

```
                   ┌─ iPhone Companion (notifications, Assist, Scriptable widget)
                   │
    Reverse proxy ── HAOS (local IP)
       │              │
       │              ├── Aqara Hub M3 ── (Matter) ── 30+ Aqara sensors
       │              ├── Zigbee2MQTT ── Lixee Linky, sensors, plugs
       │              ├── Hue Bridge ── lights + motion
       │              ├── UniFi Console ── G4 Instant (motion + person_detected)
       │              ├── Netatmo ── temp/humidity/CO₂ per room + outdoor + rain gauge
       │              ├── Daikin ── living-room AC
       │              ├── Tesla ── charge, climate, location
       │              ├── Roborock S8 Pro Ultra ── map + zones
       │              ├── Samsung ── dishwasher / washer / dryer / oven
       │              ├── Prusa + Bambu ── 3D printing
       │              ├── Anthropic API ── Claude (brief + vision)
       │              └── 7" kiosk Pi in the hallway (Wi-Fi, SSH key)
       │
       └─ remote access (home.example.com)
```

## Design principles

- **HA is the source of truth.** Cloud integrations (HomeKit, Apple, Samsung…)
  are exposed *from* HA, never depended on *as* a data source. We expose to
  Apple via a HomeKit bridge; we don't depend on Apple → HA.
- **Config in packages.** Each theme (a room's lighting, climate, the baby's
  night light, modes) is a self-contained package in `packages/` — isolatable,
  readable, reloadable.
- **MQTT via an external broker.** Zigbee2MQTT and HA publish/subscribe on a
  dedicated MQTT broker, with MQTT auto-discovery for the Zigbee entities.
- **Externalized secrets.** Everything goes through `!secret` (see `secrets.yaml.example`).

## The wall panel: 7" touchscreen Pi in the hallway

Raspberry Pi + official 7" DSI touchscreen in Chromium kiosk mode.
A panoramic 800×480 dashboard: per-room light tiles (tap = toggle, hold = popup),
motorized shutters with inline controls, global actions (Leaving, Baby nap,
Nanny, Holiday), weather + next calendar event. Wakes on Hue motion detection,
sleeps 2 min after everyone leaves. See [`dashboards/tablette.yaml`](./dashboards/tablette.yaml).
