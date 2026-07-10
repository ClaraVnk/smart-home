# Architecture

Vue d'ensemble du système. Les IP et le domaine réels sont volontairement
remplacés par des placeholders.

```
                   ┌─ iPhone Companion (notif, Assist, widget Scriptable)
                   │
    Reverse proxy ── HAOS (IP locale)
       │              │
       │              ├── Aqara Hub M3 ── (Matter) ── 30+ capteurs Aqara
       │              ├── Zigbee2MQTT ── Lixee Linky, capteurs, prises
       │              ├── Hue Bridge ── lights + motion
       │              ├── UniFi Console ── G4 Instant (motion + person_detected)
       │              ├── Netatmo ── T°/HR/CO₂ par pièce + extérieur + pluviomètre
       │              ├── Daikin ── clim salon
       │              ├── Tesla ── charge, climate, location
       │              ├── Roborock S8 Pro Ultra ── map + zones
       │              ├── Samsung ── lave-vaisselle / lave-linge / sèche-linge / four
       │              ├── Prusa + Bambu ── impression 3D
       │              ├── Anthropic API ── Claude (brief + vision)
       │              └── Pi 7" kiosk entrée (Wi-Fi, SSH key)
       │
       └─ accès distant (home.example.com)
```

## Principes de conception

- **HA = source de vérité.** Les intégrations cloud (HomeKit, Apple, Samsung…)
  sont exposées *depuis* HA, jamais dépendues *comme* source. On expose vers
  Apple via un bridge HomeKit ; on ne dépend pas d'Apple → HA.
- **Config en packages.** Chaque thème (éclairages d'une pièce, climat,
  veilleuse bébé, modes) est un package autonome dans `packages/` — isolable,
  lisible, rechargeable.
- **MQTT via broker externe.** Zigbee2MQTT et HA publient/souscrivent sur un
  broker MQTT dédié. Auto-discovery MQTT pour les entités Zigbee.
- **Secrets externalisés.** Tout passe par `!secret` (voir `secrets.yaml.example`).

## Le wall panel : Pi 7" tactile dans l'entrée

Raspberry Pi + écran DSI officiel 7" tactile en mode Chromium kiosk.
Dashboard panoramique 800×480 : tuiles lumières par pièce (tap = toggle,
hold = popup), volets motorisés inline, actions globales (Quitter, Sieste,
Nounou, Vacances), météo + prochain événement calendrier.
Réveil sur détection présence Hue motion, veille 2 min après absence.
Voir [`dashboards/tablette.yaml`](./dashboards/tablette.yaml).
