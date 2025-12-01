# 🌍 node-red-space-station-telescope-observatory-tracker

Live worldmap tracker for multiple **space stations (International Space Station (ISS) & Chinese Space Station (CSS))** and **space telescopes (Hubble Space Telescope, Chandra X-ray Observatory)** using **Node-RED** and **N2YO API**.

This flow lets you visualize—on a single interactive map:

- 🛰 **International Space Station (ISS)**
- 🛰 **Chinese Space Station — Tiangong (CSS)**
- 🔭 **Hubble Space Telescope**
- 🔭 **Chandra X-ray Observatory**

Each object shows:

- Latitude / Longitude (with bold labels in the popup)
- Altitude in **km** and **miles**
- Velocity in **km/s** and **mph** (with sensible fallbacks if velocity isn’t returned by the API)
- Direction of travel (degrees + compass label, e.g. “245.3° (SW)”)
- Elevation angle
- “In Earth’s shadow” (Yes / No)
- Local time at the observation timestamp
- Historical **tracks** drawn via `worldmap-tracks`

There is also a custom **region classifier**, so instead of raw lat/lon only, you see friendly descriptions like:

- `over Western Europe`
- `over Northern South America`
- `over the Caribbean region`
- `over Southern Africa`
- `over Southeast Asia`
- `over the North Pacific Ocean`
- `over the Arctic region`

---

## 🛰 Satellites & Telescopes in this Flow

| Object                        | Type              | NORAD ID | Layer Name | Icon Color |
|------------------------------|-------------------|----------|------------|-----------|
| International Space Station  | Space Station     | 25544    | `ISS`      | Royal Blue |
| Chinese Space Station (CSS)  | Space Station     | 48274    | `CSS`      | Red       |
| Hubble Space Telescope       | Telescope (LEO)   | 20580    | `Hubble`   | Gold      |
| Chandra X-ray Observatory    | Telescope (HEO)   | 25867    | `Chandra`  | Saffron   |

> 🔑 **API keys are not included.** You must supply your own N2YO API key in the HTTP Request nodes.

---

## 📦 Prerequisites

Before using this flow, you should have:

- A free account at **[N2YO.com](https://www.n2yo.com/)** to get:
  - Your **observer latitude & longitude**
  - Your **API key**
- A working **Node-RED** installation  
- The **WorldMap** node:
  - Install via Node-RED Palette: `node-red-contrib-web-worldmap`

---

## 🛠 Installation & Setup

1. **Clone or download this repo**:

   ```bash
   git clone https://github.com/TheDyslexicCoder/node-red-space-station-telescope-observatory-tracker.git
