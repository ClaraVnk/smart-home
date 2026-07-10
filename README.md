<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Poppins&weight=600&size=34&pause=1000&color=41BDF5&center=true&vCenter=true&width=650&height=60&lines=My+House+That+Thinks;A+passive+smart+home;Home+Assistant+%2B+Claude+AI" alt="My House That Thinks" />

**A real, production Home Assistant setup** — for a household of 2 adults, a baby, a dog and a cat, in a 3rd-floor flat.
Matter + Zigbee, a Claude AI brain, a nightly voice brief, UniFi cameras, energy tracking, and a touchscreen Pi wall panel.

<a href="https://www.home-assistant.io/"><img src="https://img.shields.io/badge/Home_Assistant-%2341BDF5.svg?style=for-the-badge&logo=home-assistant&logoColor=white" alt="Home Assistant"></a>
<img src="https://img.shields.io/badge/Matter-%231a1a2e.svg?style=for-the-badge&logo=matter&logoColor=white" alt="Matter">
<img src="https://img.shields.io/badge/Zigbee-%23EB0443.svg?style=for-the-badge&logo=zigbee&logoColor=white" alt="Zigbee">
<a href="https://www.anthropic.com/"><img src="https://img.shields.io/badge/Claude_AI-%23D97757.svg?style=for-the-badge&logo=anthropic&logoColor=white" alt="Claude AI"></a>

<img src="https://img.shields.io/badge/Mushroom-cards-%238E44AD?style=for-the-badge" alt="Mushroom">
<img src="https://img.shields.io/badge/Passive-smart%20home-%232ECC71?style=for-the-badge" alt="Passive smart home">
<img src="https://img.shields.io/badge/Mobile-first-%23000000?style=for-the-badge&logo=apple&logoColor=white" alt="Mobile first">

<img src="https://img.shields.io/github/license/ClaraVnk/smart-home?style=flat-square&color=blue" alt="License MIT">
<img src="https://img.shields.io/github/last-commit/ClaraVnk/smart-home?style=flat-square" alt="Last commit">
<img src="https://img.shields.io/github/stars/ClaraVnk/smart-home?style=flat-square&color=yellow" alt="Stars">
<img src="https://img.shields.io/github/languages/top/ClaraVnk/smart-home?style=flat-square" alt="Top language">

📖 The full story, behind the scenes → **[cyberloutre.fr](https://cyberloutre.fr)**

<img src="./screenshots/showcase-desktop.png" width="90%" alt="Desktop showcase">

</div>

---

## 📖 Table of contents

- [The idea: a *passive* smart home](#-the-idea-a-passive-smart-home)
- [Highlights](#-highlights)
- [Dashboards](#-dashboards)
- [Signature automations](#-signature-automations)
- [The stack](#-the-stack)
- [Explore the code](#-explore-the-code)
- [By the numbers](#-by-the-numbers)
- [Why not an off-the-shelf system?](#-why-not-an-off-the-shelf-system)
- [Reusing this repo](#-reusing-this-repo)

---

## 🧠 The idea: a *passive* smart home

No "Hey Siri, turn on the light." The house **observes and acts on its own**:

- The bathroom lights up when you walk in, **stays on while you shower**, turns off when you leave
- The shutters close when it **rains while a window is open**
- The oven only notifies the iPhones of people **currently home**
- Claude AI writes a **natural evening brief** of the day, every night

Quiet, contextual, and it frees up mental space.

---

## ✨ Highlights

<table>
<tr>
<td width="50%" valign="top">

### 🌙 A nightly brief written by Claude AI
Every evening at 10 PM, a snapshot of the day (power use, per-room temps, presence, anomalies) is sent to **Claude Haiku 4.5**, which writes a warm, natural situation report to both iPhones — not a dump of numbers. **~30 cents / month.**

</td>
<td width="50%" valign="top">

### 🖨️ Spaghetti detection by computer vision
During a 3D print, every 10 minutes a camera snapshot is sent to **Claude vision**. If it spots a failed print, you get an iPhone notification with actionable **Pause / Cancel** buttons.

</td>
</tr>
<tr>
<td width="50%" valign="top">

### 🎛️ 100% Mushroom + glassmorphism UI
Every dashboard is hand-built with **[Mushroom cards](https://github.com/piitaya/lovelace-mushroom)** + `card_mod`, Apple-like glass style, **mobile-first**. All YAML included.

</td>
<td width="50%" valign="top">

### 📟 A 7" touchscreen wall panel
A Raspberry Pi in the hallway runs a Chromium kiosk dashboard that **wakes on motion** and sleeps when everyone leaves.

</td>
</tr>
</table>

---

## 📸 Dashboards

Everything below is built with **Mushroom cards** + `card_mod`, glassmorphism / Apple-like, **mobile-first**. Full YAML in [`dashboards/`](./dashboards).

### 🏠 Overview

<p align="center">
  <img src="./screenshots/showcase-mobile-1.png" width="24%">
  <img src="./screenshots/showcase-mobile-2.png" width="24%">
  <img src="./screenshots/showcase-mobile-3.png" width="24%">
  <img src="./screenshots/showcase-mobile-4.png" width="24%">
  <img src="./screenshots/showcase-mobile-5.png" width="24%">
  <img src="./screenshots/showcase-mobile-6.png" width="24%">
  <img src="./screenshots/showcase-mobile-7.png" width="24%">
  <img src="./screenshots/showcase-mobile-8.png" width="24%">
</p>

### ⚡ Energy

Linky (Lixee TIC over Zigbee) + RTE Tempo tariff + Power Flow Card.

<p align="center">
  <img src="./screenshots/energy-1.png" width="24%">
  <img src="./screenshots/energy-2.png" width="24%">
  <img src="./screenshots/energy-3.png" width="24%">
  <img src="./screenshots/energy-graph-1.png" width="24%">
  <img src="./screenshots/energy-graph-2.png" width="24%">
</p>

### 🎨 Tempo (EDF Tempo tariff)

<p align="center">
  <img src="./screenshots/tempo-1.png" width="30%">
  <img src="./screenshots/tempo-2.png" width="30%">
</p>

### 🧰 Maintenance & recurring tasks

Due-date tracking for filters, mopping, the pet fountain, the litter box… surfaced as actionable cards.

<p align="center">
  <img src="./screenshots/maintenance-1.png" width="30%">
  <img src="./screenshots/maintenance-2.png" width="30%">
  <img src="./screenshots/maintenance-3.png" width="30%">
</p>

### 🔋 Batteries · 📅 Calendar · 📦 Parcels

<p align="center">
  <img src="./screenshots/batteries.png" width="30%">
  <img src="./screenshots/calendar.png" width="30%">
  <img src="./screenshots/parcels.png" width="30%">
</p>

### 🤖 Robot vacuum (Roborock S8 Pro Ultra)

<p align="center">
  <img src="./screenshots/vacuum-1.png" width="30%">
  <img src="./screenshots/vacuum-2.png" width="30%">
  <img src="./screenshots/vacuum-3.png" width="30%">
</p>

### 🖨️ 3D printing (Prusa + Bambu · Claude vision)

<p align="center">
  <img src="./screenshots/printer-1.png" width="30%">
  <img src="./screenshots/printer-2.png" width="30%">
  <img src="./screenshots/printer-3.png" width="30%">
</p>

### 🚗 Tesla

<p align="center">
  <img src="./screenshots/tesla-1.png" width="24%">
  <img src="./screenshots/tesla-2.png" width="24%">
  <img src="./screenshots/tesla-3.png" width="24%">
  <img src="./screenshots/tesla-4.png" width="24%">
</p>

### 📟 Wall panel — 7" touchscreen Pi in the hallway

Raspberry Pi + official 7" DSI touchscreen in Chromium kiosk mode. Wakes on Hue
motion, sleeps 2 min after everyone leaves. YAML in [`dashboards/tablette.yaml`](./dashboards/tablette.yaml).

<p align="center"><img src="./screenshots/pi-kiosk.png" width="70%"></p>

---

## ⭐ Signature automations

| | Automation |
|---|---|
| 🌧️ | **Rain + open window → shutters close.** Netatmo rain gauge > 0.1 mm/h and a window left open → exposed shutters close + iPhone notification. |
| 🚿 | **Shower in progress → light protected.** Aqara P2 motion + bathroom humidity. While RH > 55% and someone is in the room, the light won't turn off — even on an accidental tap or a phantom firmware timer. → [`packages/sdb_lampes.yaml`](./packages/sdb_lampes.yaml) |
| 🤖 | **Autonomous vacuum (Wed/Sat/Sun).** Everyone away > 5 min → Roborock starts. Someone comes home → immediate dock return. It remembers the remaining zone and resumes next time. |
| 🌙 | **10 PM Claude AI brief.** A snapshot of the day → Claude Haiku 4.5 → a warm, natural situation report to both iPhones. |
| 🖨️ | **Prusa spaghetti detection (Claude vision).** Every 10 min during a print, a snapshot goes to Claude; on a detected failure, an iPhone notification with Pause / Cancel buttons. |
| 🚨 | **Oven on + nobody home → critical alert.** `interruption-level: critical` (bypasses every iOS focus) with a "🛑 Stop remotely" button. |

---

## 🧰 The stack

| Layer | Tech |
|-------|------|
| **Backbone** | Home Assistant OS · reverse proxy (Pangolin) |
| **Matter / Zigbee** | Aqara Hub M3 (Matter bridge) · Zigbee2MQTT · UniFi Protect · Hue |
| **Climate** | Daikin (custom bridge: living-room `input_number` = source of truth) |
| **Energy** | Lixee Linky (Zigbee) · RTE Tempo · Power Flow Card+ |
| **AI** | Anthropic Claude Haiku 4.5 (evening brief + Prusa vision) |
| **Voice** | HA Companion iOS Assist (Voice PE planned) |
| **Wall panel** | Raspberry Pi + 7" touchscreen, Chromium kiosk |

---

## 📂 Explore the code

| Folder | Contents |
|--------|----------|
| [`dashboards/`](./dashboards) | `ui-lovelace.yaml` (main "Overview" + "Everything" views) and dedicated dashboards (energy, maintenance, showcase, tablet, Tesla, 3D printer). Mushroom + `card_mod`, glassmorphism, mobile-first. |
| [`automations/`](./automations) | `automations.yaml`, `scripts.yaml`, `scenes.yaml`. |
| [`packages/`](./packages) | Automations grouped by theme (per-room lighting, living-room climate, baby night light, recurring tasks, holiday/nanny modes, Nabaztag, notifications, zones…). |
| [`secrets.yaml.example`](./secrets.yaml.example) | The `!secret` keys referenced across the repo — fill in with your own values. |

> 🔒 **Security:** every secret (tokens, passwords, domain, internal IPs, GPS coordinates)
> is externalized via `!secret` or redacted. No sensitive data is published.

---

## 📊 By the numbers

- **~160** active automations (YAML + packages)
- **30+** Aqara sensors paired over Matter
- **4** UniFi cameras with AI person detection
- **6** rooms with individual temperature / humidity / CO₂ sensors
- **1** daily Claude AI brief (~30 cents / month)

---

## 🤔 Why not an off-the-shelf system?

1. **Local data** — everything stays on the network; Anthropic only sees the brief requests, not the house in real time.
2. **No proprietary cloud** — if Aqara / Tesla / Samsung shut down their service tomorrow, the house keeps running on the local bus.
3. **Extensibility** — new integration? 5 min of YAML. New automation? 30 lines.
4. **Cost** — ~5 €/month (Claude API + electricity).

---

## ♻️ Reusing this repo

Shared as **reference / inspiration**, not a turnkey product: the `entity_id`s, `device_id`s
and room names are those of my own install. Grab the patterns (Mushroom cards, Jinja templates,
package structure) and adapt them.

<div align="center">

**If this gave you ideas, drop a ⭐ — it helps others find it.**

🦦 [**cyberloutre.fr**](https://cyberloutre.fr) · code + care

</div>
