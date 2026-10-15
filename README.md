<p align="center">
  <img src="logo.svg" alt="Tandem Logo" width="128" height="128" />
</p>

<h1 align="center">Tandem</h1>

> **Decentralized Tactical Edge Logistics and High-Altitude Stocking Intelligence**

[![React](https://img.shields.io/badge/React-19-black?logo=react)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-black?logo=typescript)](https://www.typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-6.2-black?logo=vite)](https://vitejs.dev)
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-v4-black?logo=tailwindcss)](https://tailwindcss.com)
[![Leaflet](https://img.shields.io/badge/Leaflet-GIS-black?logo=leaflet)](https://leafletjs.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-black)](https://opensource.org/licenses/MIT)

Tandem is a decentralized tactical logistics and supply forecasting platform built for high-altitude mountain sectors along the Line of Actual Control (LAC) in Eastern Ladakh. It coordinates stock forecasting, mountain corridor pathfinding, and pass closure monitoring across forward operating bases without relying on central cloud servers or external API keys.

## Tech Stack

- **Frontend & GIS:** React 19, TypeScript, Vite, Tailwind CSS v4, Leaflet, Recharts, Lucide Icons
- **Federated Edge Learning:** Clustered FL, Adaptive Renyi DP-SGD, SecAgg+ zero-knowledge masking, Top-k sparsification, Byzantine filtering
- **Telemetry & Standards:** NASA SRTM 30m DEM elevation profiles, DRDO DFRL nutrition baselines, sub-zero fuel burn curves
- **Routing:** Geodesic mountain corridor optimization with winding factor calibration and heavy-lift logistics drone corridors

## Key Features

- **Operations Dashboard:** Real-time navigability scores, reachable corridor mileage, elevation profiles, and sortie queues.
- **Interactive Tactical GIS Map:** Dark GIS and Satellite layers showing active corridors, pass closures, and operational base selection.
- **Consumption & Winter Stocking:** 12-month trends and 90-day depletion forecasts for diesel, ammunition, rations, and battery cells.
- **Convoy & UAV Pathfinder:** Mountain distance calculations, transit times, fuel burn, and sortie dispatch generation.
- **Himalayan Risk & Early Warning:** Threat radar, node health, and live privacy controls for DP-SGD and SecAgg+.
- **EMCON Mode & Live Telemetry:** Radio silence toggle and real-time telemetry event stream.
- **Tactical Authentication:** Dark login interface supporting Google, GitHub, SAML SSO, Passkey, and Duty Officer access.

## Quickstart

```bash
git clone https://github.com/ankitgpt18/Tandem.git
cd Tandem/tactical-ops-web
npm install
npm run dev
```

Open `http://localhost:5173/` in your browser.

## Deployment

Tandem deploys directly to Vercel with zero external API keys:

1. Import the repository in Vercel.
2. Set the Root Directory to `tactical-ops-web`.
3. Framework preset detects Vite automatically.
4. Click Deploy.

## Author

- **Ankit Gupta**
- **GitHub:** [@ankitgpt18](https://github.com/ankitgpt18)
- **Email:** ankitgupta18k@gmail.com

## License

This project is licensed under the MIT License.
