<p align="center">
  <img src="tactical-ops-web/public/tandem-logo.png" alt="Tandem Logo" width="128" height="128" />
</p>

<h1 align="center">Tandem</h1>

> **Decentralized Tactical Edge Logistics and High-Altitude Winter Stocking Intelligence**

[![React](https://img.shields.io/badge/React-19-black?logo=react)](https://react.dev)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.9-black?logo=typescript)](https://www.typescriptlang.org)
[![Vite](https://img.shields.io/badge/Vite-6.2-black?logo=vite)](https://vitejs.dev)
[![Tailwind CSS](https://img.shields.io/badge/TailwindCSS-v4-black?logo=tailwindcss)](https://tailwindcss.com)
[![Leaflet](https://img.shields.io/badge/Leaflet-GIS-black?logo=leaflet)](https://leafletjs.com)
[![License: MIT](https://img.shields.io/badge/License-MIT-black)](https://opensource.org/licenses/MIT)

Tandem is a decentralized tactical logistics command and stock forecasting system built for high-altitude mountain sectors along the Line of Actual Control (LAC) in Eastern Ladakh.

Forward operating bases along the frontier (Leh, Kargil, Nyoma, Daulat Beg Oldi, and Diskit) cannot centralize operational stock ledgers due to defense classification boundaries and hostile electronic warfare. Tandem combines on-device federated learning, mountain road network graphs, microclimate stocking telemetry, and electronic warfare threat monitoring without relying on external cloud servers or paid API keys.

## Tech Stack

- **Frontend & UI:** React 19, TypeScript, Vite, Tailwind CSS v4, Lucide Icons
- **Mapping & Geospatial:** Leaflet, React-Leaflet, OpenStreetMap CartoDB Dark GIS, Esri World Imagery
- **Data Visualization:** Recharts (elevation cross-sections, 12-month burn curves, threat radar)
- **Edge Federated Learning Architecture:** Clustered FL (CFL), Adaptive Renyi DP-SGD, SecAgg+ zero-knowledge masking, Top-k 90% sparsification, Directional Cosine Momentum Byzantine filtering
- **Telemetry & Standards:** NASA SRTM 30m DEM elevation profiles, DRDO DFRL 4,500 kcal combat ration baselines, Indian Army Advance Winter Stocking (AWS) fuel burn coefficients

## Key Features

- **Executive Operations Dashboard:** Real-time sector navigability scores, reachable corridor mileage, longitudinal elevation profiles, and dispatch queues calculated dynamically from corridor and pass data.
- **Interactive Tactical GIS Map:** High-contrast Dark GIS and Satellite HD layers showing active corridors, pass closures, and station callouts. Allows switching the active operational base directly from map nodes.
- **Consumption & Winter Stocking (AWS):** 12-month historical consumption trends and 90-day depletion forecasts for winter diesel, 155mm artillery shells, DFRL rations, and drone battery cells with sub-zero seasonal multipliers.
- **Convoy & UAV Tactical Pathfinder:** Geodesic mountain routing with a 1.35x winding factor. Computes transit times, fuel burn, and pass clearances for heavy vehicle convoys and DRDO 200kg logistics drones.
- **Himalayan Risk & EW Early Warning:** Per-sector threat radars tracking electronic jamming, pass closures, and road damage. Includes interactive controls for DP-SGD noise, SecAgg+ masking, and peer-to-peer gossip rounds.
- **EMCON Mode & Live Telemetry Stream:** Emissions Control toggle for radio silence. An expandable bottom console streams packet events, gradient compression logs, and local SQLite memory buffering.
- **Tactical Authentication:** Dark login screen supporting Google sign-in, GitHub access, SAML SSO, Passkey, and direct Duty Officer access with session persistence.

## System Architecture

```text
[ Forward Depots: SEC-1 Leh | SEC-2 Kargil | SEC-3 Nyoma | SEC-4 DBO | SEC-5 Diskit ]
                                    │
                    Local On-Device Training (GRU & ST-GNN)
                                    │
           ┌────────────────────────┴────────────────────────┐
           ▼                                                 ▼
   [ Normal Radio Conditions ]                     [ EMCON Silence Active ]
   - Top-k 90% Sparsification                      - Radio emissions cut
   - SecAgg+ Pairwise Masking                      - Updates buffered in local SQLite
   - Renyi DP-SGD Noise (eps=1.85)                 - Zero RF signature emitted
   - P2P Gossip Consensus Round                    - Sync resumes when EMCON lifts
                                    │
                                    ▼
       [ Tactical Dashboard: Navigability, Runways & Convoy Dispatch ]
```

## Grounded Open Datasets

The entire system runs on free, open-access, local-first datasets with zero third-party cloud trackers:

| Dataset | Source | Resolution / Size | Tactical Role |
| :--- | :--- | :--- | :--- |
| NASA SRTM / Cartosat DEM | OpenTopography | 30-meter GeoTIFF | Slope drag and elevation cross-sections |
| Ladakh Road Network | OpenStreetMap / OSMnx | 15,000+ Segments | Highway corridors and mountain switchbacks |
| Himalayan Climate Series | NASA POWER / IMD | Daily Records | Pass freeze windows and sub-zero fuel factors |
| High-Altitude Nutrition | DRDO DFRL Mysore | 4,500 kcal/day | Ration depletion runway calculations |

## Repository Structure

```text
Tandem/
├── tactical-ops-web/             # React + TypeScript + Vite frontend
│   ├── public/
│   │   ├── tandem-logo.png       # Tandem emblem
│   │   └── favicon.png           # Browser icon
│   ├── src/
│   │   ├── components/
│   │   │   ├── TopNavbar.tsx     # Sector switcher, sensor dates, EMCON toggle
│   │   │   ├── Sidebar.tsx       # Navigation and authenticated account control
│   │   │   ├── ExecutiveDashboardView.tsx   # Fleet readiness and elevation profile
│   │   │   ├── InteractiveTacticalMapView.tsx # Leaflet GIS map and station markers
│   │   │   ├── ConsumptionTrendsView.tsx    # AWS stocking and depletion charts
│   │   │   ├── ConvoyPathfinderView.tsx     # Route planning and sortie dispatch
│   │   │   ├── RiskEarlyWarningView.tsx     # Threat radar and FL security panel
│   │   │   ├── TelemetryConsole.tsx         # Live bottom telemetry stream drawer
│   │   │   ├── LoginPage.tsx                # Authentication screen
│   │   │   ├── DocsModal.tsx                # Technical documentation and FAQ
│   │   │   └── ExportModal.tsx              # JSON dossier and CSV ledger export
│   │   ├── data/
│   │   │   └── sectorsData.ts    # Authentic depot, pass, and corridor telemetry
│   │   ├── App.tsx               # Root component and view routing
│   │   ├── main.tsx              # Entry point
│   │   └── index.css             # Tailwind v4 styles and Leaflet overrides
│   ├── package.json
│   ├── vite.config.ts
│   └── vercel.json               # SPA route rewrites for Vercel
└── README.md
```

## Getting Started

### Prerequisites

- Node.js 18+ (Node.js 20 recommended)
- npm or pnpm

### Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/ankitgpt18/Tandem.git
   cd Tandem/tactical-ops-web
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Start the local development server:
   ```bash
   npm run dev
   ```

4. Open your browser and navigate to:
   ```text
   http://localhost:5173/
   ```

### Production Build

To verify TypeScript types and build optimized production assets:

```bash
npm run build
```

The output will be generated in `tactical-ops-web/dist/`.

## Deployment to Vercel

Tandem is pre-configured for deployment on Vercel:

1. Import the `ankitgpt18/Tandem` repository into Vercel.
2. Set the **Root Directory** to `tactical-ops-web`.
3. Framework preset will automatically detect **Vite**.
4. Leave environment variables blank (zero external API keys needed).
5. Click **Deploy**.

## Author

- **Ankit Gupta**
- **GitHub:** [@ankitgpt18](https://github.com/ankitgpt18)
- **Email:** ankitgupta18k@gmail.com

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for details.
