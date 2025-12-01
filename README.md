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
   
2. **Open Node-RED** and go to the editor:

   ```text
   http://<your-node-red-ip>:1880


3. **Import the flow:**

- Menu → **Import** → **Clipboard**
- Open `Space Stations & Telescopes Node-Red Flows.json` from this repo
- Copy its contents into the Import dialog
- Click **Import**

4. **Edit the HTTP Request nodes** for:

- ISS  
- CSS  
- Hubble  
- Chandra  

In each URL, replace the `apiKey=...` value with **your own N2YO API key**  
(and optionally update the latitude/longitude to match your observer location).

5. **Deploy** the flow in Node-RED.

6. Open the WorldMap in your browser:

http://<your-node-red-ip>:1880/worldmapSpaceStations

You should now see all four objects moving in real time, each with a detailed popup and regional description.

---

## 🧭 Region Classification

Each popup includes an **“Approx. region”** line that uses latitude and longitude to map the object to a broad, human-friendly area, such as:

- Western / Central / Eastern Europe  
- North / Central / South America  
- Caribbean  
- Northern / Central / Southern Africa  
- Western / Central / Eastern / Southern / Southeast Asia  
- Australasia / Oceania  
- North / South Atlantic, Pacific, Indian Ocean  
- Arctic / Southern Ocean  

This is intentionally **approximate** (not city-accurate) but far more readable than raw coordinates alone.

---

## 🔧 Customizing

You can easily modify:

- **Update frequency**  
  - Adjust the Inject node interval (default is ~32 seconds)
- **Marker colors & icons**  
  - Edit each `* Attributes` function node (`iconColor`, `layer`, tooltips, etc.)
- **Region logic**  
  - Modify the `regionFromLatLon()` function inside each Attributes node
- **Track behavior**  
  - Customize `worldmap-tracks` depth, smoothing, or layer assignment
- **Units**  
  - Currently displays both metric and US units (km + mi, km/s + mph)

---

## 📚 Background & Previous Version

This repository is the expanded version of my earlier project:

- **Original repo (ISS + CSS only):**  
https://github.com/TheDyslexicCoder/node-red-space-station-worldmap

The original project focused on tracking only two space stations.  

This upgraded version adds:
  - Two major space telescopes (Hubble & Chandra)  
  - Enhanced popups with more scientific data  
  - Smart regional mapping for better context  
  - Better formatting, icons, and event handling  
  - Historical tracks for each spacecraft  

---

## 📄 License

This project is open-source.

If using MIT License, create a `LICENSE` file containing:

```text
MIT License

