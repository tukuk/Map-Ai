# MapAi — Universal Cross-Platform AI GPS Navigation & Live Traffic

**MapAi** is a cross-platform AI GPS navigation app and Waze alternative built with **React 18 + TypeScript + Vite + Tailwind CSS** on the web frontend, **Kotlin + Jetpack Compose** for Android, **Rust / Tauri** for high-performance desktop, and an Express + Socket.IO + SQLite backend server.

It is designed to run seamlessly across all operating systems: **Android, iOS, Windows, Linux, macOS, Huawei (HarmonyOS), and Smart TVs (Android TV, Fire TV, Apple TV, WebOS, Tizen)**.

🚀 **Live Web View Demo:** [https://map.tukuk.org/](https://map.tukuk.org/)  
📦 **GitHub Repository:** [https://github.com/tukuk/Map-Ai](https://github.com/tukuk/Map-Ai)

---

## Key Features

| Module | Features & Capabilities |
|--------|--------------------------|
| **Interactive Map & Routing** | OpenStreetMap (Leaflet / osmdroid) & MapLibre GL, place search, waypoint navigation, OSRM & Google Directions API integration |
| **Gemini AI Navigation Copilot** | Gemini 3.6 Flash AI copilot for instant route queries, direction finding, live traffic advice, and auto-triggered navigation |
| **Live Express Delivery Hubs** | Real-time rider hubs & status indicators for **Maxim, GrabFood, GrabExpress, and Foodpanda (pandamart)** |
| **NASA Live Telemetry & Feed** | Real-time ISS station satellite tracking (speed & altitude) plus NASA Live video feed and EONET wildfire/storm alerts |
| **Live Multi-Device Phone Tracker** | Real-time tracking of family members, fleet drivers, and express riders |
| **Crowdsourced Traffic Alerts** | Real-time hazard reporting — police traps, traffic jams, accidents, roadworks, speed cameras — with density confidence scoring |
| **Smart Speedometer & Drive Tab** | Real-time GPS speedometer, speed limit warnings, road weather conditions, and speed camera alerts |
| **Media & Dashcam Vault** | Local in-app camera capture and dashcam video recording with geotagging and export |
| **Emergency SOS System** | Instant siren trigger, fake incoming call simulator, SMS/Call emergency contacts, and live location broadcasting |
| **Vercel Cron & Cloud Automation** | Scheduled daily maintenance endpoint (`/api/cron`, `vercel.json`) with `CRON_SECRET` authorization for SOS and report cache cleanup |
| **Studio Installation & Multi-Stack** | Clean Installation & Studio Build panel in Settings supporting **Gradle (Android), React (PWA), Rust (Tauri), Windows (.exe), and Smart TV** |

---

## Universal Cross-Platform & Multi-Stack Builds

MapAi supports multiple build technologies tailored for every device and operating system:

| Technology Stack | Target Platform | Build Command / Output |
|------------------|-----------------|------------------------|
| **Gradle (Android / TV)** | Android 8.0+ Phone, Tablet, Android TV, Huawei HarmonyOS | `./workflow.sh build` → `app-debug.apk` |
| **React 18 + Vite PWA** | Web Browsers, iOS Safari, Android Chrome, Edge | `npm run build` → PWA Web Manifest & Service Worker |
| **Rust + Tauri** | Windows 10/11, macOS, Linux (Debian/Ubuntu/Fedora) | `cargo tauri build` → Lightweight native `.exe` / `.deb` / `.dmg` |
| **Windows Executable** | Windows PCs, Laptops, Tablets | Installable PWA via Edge/Chrome or native Rust `.exe` |
| **Smart TV Mode** | Android TV, Fire TV, LG WebOS, Samsung Tizen | 10ft remote-friendly D-Pad view & full-screen launcher |

---

## Technology Stack

### Frontend & Web PWA
- **React 18** + **TypeScript** + **Vite**
- **Tailwind CSS** + **Lucide React** icons
- **Leaflet.js** & **MapLibre GL** for map tile rendering
- **OpenStreetMap** tile servers & **OSRM** routing engine
- **PWA Web Manifest** with standalone theme configuration

### Native Android Module
- **Kotlin** + **Jetpack Compose** (Material 3)
- **osmdroid** for offline-capable OpenStreetMap tiles
- **Google Play Services Location** (FusedLocationProviderClient)
- **Retrofit 2** + **Gson** for HTTP API communications
- **Socket.IO Client** for push events

### Desktop Native Module (Rust)
- **Tauri 2** + **Rust Toolchain**
- Native C++/Rust WebView2 binding (&lt;30MB memory footprint)

### Backend Server
- **Node.js 20+** + **Express.js** API proxy
- **better-sqlite3** with WAL (Write-Ahead Logging) mode
- **Socket.IO** for WebSocket real-time push
- **Gemini 3.6 Flash AI SDK** (`@google/genai`) for route & copilot responses
- **NASA Open API** integration for APOD, EONET events, and ISS satellite tracking

---

## Project Structure

```
MapAi/
├── src/                          # Web & PWA Frontend
│   ├── components/               # React UI tabs & widgets
│   │   ├── MapView.tsx           # Leaflet / MapLibre map component
│   │   ├── ChatTab.tsx           # Gemini AI Copilot & route trigger
│   │   ├── DriveTab.tsx          # Speedometer, weather & camera warnings
│   │   ├── ExploreTab.tsx        # POIs & Maxim/Grab/Foodpanda hubs
│   │   ├── PhoneTrackerTab.tsx   # Multi-device GPS tracking
│   │   ├── GalleryVaultTab.tsx   # Media & Dashcam vault recording
│   │   ├── NasaWidget.tsx        # NASA TV Live & ISS telemetry tracking
│   │   ├── AlertsTab.tsx         # Traffic hazards & crowd alerts
│   │   ├── SettingsTab.tsx       # Studio Build & App Install launcher
│   │   ├── AppBuilderStudioModal.tsx # Personal App & Keystore generator
│   │   ├── TvInstallModal.tsx    # Multi-stack & TV installation guide
│   │   ├── GitLabHub.tsx         # GitLab repository & CI/CD status hub
│   │   └── SosTab.tsx            # Emergency SOS & siren simulator
│   ├── services/                 # API client & backend proxy handlers
│   ├── lib/                      # i18n & utilities
│   └── types.ts                  # Shared TypeScript interfaces
├── app/                          # Native Android app module (Gradle)
│   ├── api/cron/route.ts         # Vercel / Next.js Serverless Cron Route
│   └── src/main/java/com/example/mapai/
│       ├── data/                 # Models, repository & Retrofit client
│       ├── location/             # Location tracking service
│       └── ui/                   # Jetpack Compose screens
├── backend/                      # Express + SQLite + Socket.IO server
│   ├── server.js                 # API routes, Cron endpoint & Gemini/NASA proxy
│   └── public/                   # Live map web viewer
├── vercel.json                   # Vercel Cron configuration schedule
├── admob_config.properties       # AdMob App ID & Unit configuration (V-1 Empty)
├── keystore_config.properties    # Android Release signing identity credentials
├── public/                       # PWA manifest, favicon & icons
├── server.ts                     # Dev server entry point & /api/cron handler
├── workflow.sh                   # Main automation script
└── README.md                     # Documentation
```

---

## Quick Start & Installation (`tukuk.org` / Port 3333)

### 1. Local & Server Installation (`npm install` on Port 3333)
Run the full-stack web + API + Socket.IO server directly on your server IP or `tukuk.org`:

```bash
# 1. Clone the repository
git clone https://github.com/tukuk/Map-Ai.git
cd Map-Ai

# 2. Install dependencies
npm install

# 3. Copy & configure environment variables
cp .env.example .env
# Edit .env to set PORT=3333 and optional API keys (GEMINI_API_KEY, NASA_API_KEY)
```

#### Development Mode
```bash
npm run dev
# Runs on http://0.0.0.0:3333
```

#### Production Mode (`tukuk.org`)
```bash
# Build frontend (Vite) & backend bundle (esbuild)
npm run build

# Start production server on Port 3333
NODE_ENV=production npm start
```
Access directly via `http://<server-ip>:3333` or `https://tukuk.org` (via Nginx reverse proxy below).

---

### 2. Deploying on `tukuk.org` with PM2 & Nginx (Recommended)

#### A. Keep Server Running 24/7 with PM2
```bash
npm install -g pm2
cd /path/to/Map-Ai
npm install
npm run build
NODE_ENV=production PORT=3333 pm2 start dist/server.cjs --name mapai
pm2 save
pm2 startup
```

#### B. Open Firewall Port (if accessing via IP:3333)
```bash
sudo ufw allow 3333/tcp
```

#### C. Nginx Reverse Proxy for `https://tukuk.org` (HTTP + WebSocket / Socket.IO)
Create `/etc/nginx/sites-available/tukuk.org`:
```nginx
server {
    listen 80;
    server_name tukuk.org www.tukuk.org;

    location / {
        proxy_pass http://127.0.0.1:3333;
        proxy_http_version 1.1;
        proxy_set_header Upgrade $http_upgrade;
        proxy_set_header Connection "upgrade";
        proxy_set_header Host $host;
        proxy_set_header X-Real-IP $remote_addr;
        proxy_set_header X-Forwarded-For $proxy_add_x_forwarded_for;
        proxy_set_header X-Forwarded-Proto $scheme;
        proxy_read_timeout 86400;
    }
}
```
Enable site & SSL certificate:
```bash
sudo ln -s /etc/nginx/sites-available/tukuk.org /etc/nginx/sites-enabled/
sudo nginx -t && sudo systemctl reload nginx
sudo certbot --nginx -d tukuk.org -d www.tukuk.org
```

---

### 3. Android APK Build (Gradle)
```bash
# Build Android APK via Gradle wrapper
./workflow.sh build
# or run directly:
./gradlew assembleDebug
```
Output location: `app/build/outputs/apk/debug/app-debug.apk`

In the Android app, go to **Settings → Server URL** and set:
- Production domain: `https://tukuk.org`
- Direct server IP: `http://<your-server-ip>:3333`
- Android Emulator: `http://10.0.2.2:3333`

### 4. Standalone Backend Server (SQLite)
```bash
cd backend
npm install
PORT=3333 npm start
```

---

## Panduan Penggunaan & Kegunaan (Usage Guide)

MapAi direka sebagai sistem navigasi GPS pintar dan hab keselamatan pemanduan masa nyata:

1. **Map & Navigation (Peta & Navigasi Utama)**
   - Cari destinasi atau klik pada peta untuk merancang laluan pemanduan (*turn-by-turn*) menggunakan enjin OSRM / Google Directions.
   - Paparan lapisan **Radar Seismik Gempa Bumi (USGS)**, laporan trafik komuniti secara langsung, dan stesen pengecas EV / minyak / tempat letak kereta.
   - Sokongan peta luar talian (*Offline Map Cache*) untuk kawasan berdekatan.

2. **Gemini AI Copilot & Studio (`Chat` & Butang AI Terapung)**
   - Tanya soalan laluan, keadaan jalan, arah kiblat, atau tempat menarik menggunakan **Google Search Grounding** dan **Google Maps Grounding**.
   - Aktifkan mod **High Thinking** untuk analisis laluan atau bencana yang kompleks, serta sokongan input suara (*transcribe audio*).

3. **Alerts & USGS Earthquake Monitor (Amaran Trafik & Gempa Bumi)**
   - Pantau amaran trafik masa nyata (sekatan polis, kemalangan, jalan rosak, kamera had laju) dan sahkan laporan pemandu lain.
   - Akses suapan rasmi **USGS Real-Time Earthquakes** dengan penapis magnitud (`M2.5+`, `M4.5+`, `M6.0+`), penapis kedalaman seismik, amaran tsunami, analisis ramalan gempa susulan AI, dan pemantauan paras air/banjir (**USGS Water Data**).

4. **Drive Mode & Speedometer (Mod Pemanduan)**
   - Meter kelajuan GPS masa nyata (`km/h` atau `mph`), amaran kamera had laju, keadaan cuaca jalan raya, dan paparan fokus pemandu.

5. **Explore & Express Delivery Hubs (Teroka & Hab Penghantaran)**
   - Cari lokasi penting berhampiran (stesen minyak, hospital, ATM, restoran) serta hab penghantaran aktif untuk pemandu/penunggang **Maxim, Grab, dan Foodpanda**.

6. **Phone Tracker & NASA Live Telemetry**
   - Jejaki lokasi peranti keluarga/armada secara langsung melalui kod bilik/pautan perkongsian.
   - Pantau kedudukan **Stesen Angkasa Antarabangsa (ISS)**, amaran bencana **NASA EONET**, dan suapan **NASA Live**.

7. **Media & Dashcam Vault**
   - Rakam video dashcam dan gambar kejadian jalan raya dengan penandaan koordinat GPS secara automatik.

8. **Emergency SOS (Kecemasan)**
   - Butang siren kecemasan pantas, simulasi panggilan palsu, mesej/panggilan terus kepada kenalan kecemasan, dan penyiaran lokasi SOS ke pelayan.

9. **Settings & Custom UI (Tetapan)**
   - Tukar penyedia peta, bahasa (`en` / `ms` / `ar` / `es`), URL pelayan (`https://tukuk.org` atau `http://<ip>:3333`), mod paparan gelap/terang, serta pilihan susunan ikon navigasi bawah.

---

## Environment Variables Configuration

Create a `.env` file in the root directory (or copy `.env.example`):

```env
# Optional Gemini API key for AI Copilot & Multimodal features
GEMINI_API_KEY=your_gemini_api_key_here

# Optional NASA API key (defaults to NASA DEMO_KEY if omitted)
NASA_API_KEY=your_nasa_api_key_here

# Secret authorization key for Vercel Cron Jobs & Cloud Scheduler
CRON_SECRET=your_secret_cron_token_here

# Server port configuration (defaults to 3333 on external servers)
PORT=3333

# Local storage directory for uploads and data
DATA_DIR=./data
```

---

## Vercel Cron Jobs Configuration

MapAi supports scheduled serverless cron jobs for automated system maintenance (pruning expired SOS logs and stale hazard reports):

1. **Cron Schedule (`vercel.json`)**:
   ```json
   {
     "crons": [
       {
         "path": "/api/cron",
         "schedule": "0 10 * * *"
       }
     ]
   }
   ```

2. **Route Handlers**:
   - Next.js App Router: `app/api/cron/route.ts` & `app/api/cron/route.js`
   - Express Server: `server.ts` (`/api/cron`)
   - Backend Production Server: `backend/server.js` (`/api/cron`)

3. **Security Authorization**:
   - Vercel automatically passes the `Authorization: Bearer <CRON_SECRET>` header. Requests with invalid or missing secrets return `401 Unauthorized`.

---

## Automation Script Commands

MapAi includes a convenient workflow script (`./workflow.sh`):

```bash
./workflow.sh status   # Display git status, branch & build state
./workflow.sh build    # Build Android APK via Gradle
./workflow.sh push     # Commit and push changes to GitHub
./workflow.sh live     # Run backend server locally (Port 3333)
./workflow.sh deploy   # Show cloud deployment options (Render / Railway / Docker)
```

---

## License & Open Source

This project is open-source and released under the **MIT License**.
Contributions are welcome! Feel free to open an issue or submit a pull request on GitHub.
