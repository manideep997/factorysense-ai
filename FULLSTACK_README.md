# FactorySense AI 2.0

A production-aware energy intelligence platform for Indian SME manufacturing, built for Schneider Electric Smart Manufacturing Challenge 04.

## Stack
- **Backend:** Java 25, Spring Boot 4.1.1, Spring Web, Validation, Actuator, Spring Data JPA, H2
- **Frontend:** React, Vite, Recharts, Lucide React, custom CSS
- **Deployment:** Vercel (frontend) + Railway/Render (Spring Boot API)
- **Industrial integration target:** MQTT / OPC-UA → Edge Gateway → Analytics → Dashboard / ERP / MES

Spring Boot 4.1.1 is a current stable release. Java 25 is the current LTS line.

## Run locally
### Backend
```bash
cd backend
mvn spring-boot:run
```
API: `http://localhost:8080/api/overview`

### Frontend
```bash
cd frontend
npm install
npm run dev
```
UI: `http://localhost:5173`

Optional `.env`:
```env
VITE_API_URL=http://localhost:8080/api
```

## Production deployment
Deploy `backend` to Railway or Render using the Dockerfile. Set the public API URL as `VITE_API_URL` in the Vercel frontend project.

For the hackathon prototype, the backend runs a deterministic simulated factory telemetry stream. Replace the simulation service with real MQTT/OPC-UA ingestion when plant data is available.

## Architecture
Sensors / meters / PLC → Edge Gateway → MQTT / OPC-UA → Spring Boot analytics API → React control room → ERP / MES / SCADA integration.
