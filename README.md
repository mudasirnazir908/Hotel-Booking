# Haven — Room Rental & Booking Platform

A full-stack room rental and accommodation booking site: a modern minimalist frontend
(search, filters, room detail with live map, multi-step checkout) backed by a real
REST API with availability-aware pricing and booking creation.

**Live demo:** _add your Netlify/Vercel URL here_
**API:** _add your Render/Railway URL here_

## Stack

- **Frontend:** HTML, Tailwind CSS (CDN), vanilla JS, Leaflet.js for maps — no build step
- **Backend:** Node.js, Express, SQLite (`better-sqlite3`), JWT auth, Zod validation

## Structure

```
haven-project/
  backend/    # REST API — see backend/README.md for full docs
  frontend/   # static site — index.html, fetches the API at runtime
```

## Run locally

```bash
# 1. API
cd backend
npm install
cp .env.example .env
npm run seed
npm start          # http://localhost:4000

# 2. Frontend (separate terminal, from /frontend)
cd frontend
npx serve -l 5500  # http://localhost:5500
```

Open `http://localhost:5500` in Chrome. The frontend's `API_BASE` constant near the
top of `frontend/index.html`'s `<script>` points at `http://localhost:4000/api` by
default — update it to your deployed API URL before hosting the frontend publicly.

## Features

- Location/date/guest search with live filtering (price, room type, amenities)
- Featured destinations pulled from the database with real listing counts
- Room detail page: photo gallery, host info, amenities, house rules, real map (Leaflet + OpenStreetMap)
- Price calculation engine: nights × rate + cleaning fee + service fee, computed server-side
- Availability checking that blocks double-booking
- Guest checkout (no account required) with a generated booking reference
- Favorites and reviews, JWT-based auth for registered users

## Deployment

- **Backend** → Render, Railway, or Fly.io (needs a persistent disk, or swap SQLite for a hosted Postgres/Mongo for production)
- **Frontend** → Netlify, Vercel, or GitHub Pages (static file, drag-and-drop deploy)

See `backend/README.md` for the full API reference.
