# 🚚 ReturnTrip — Smart Return-Trip Delivery Optimization System

Delivery vehicles often drive back **empty** after completing a delivery. ReturnTrip
connects those returning vehicles with customers and businesses who need goods moved
**along the same return route** — cutting empty miles, cost and carbon.

> **Example:** A truck delivers Hyderabad → Vijayawada. On the way back
> (Vijayawada → Guntur → Hyderabad) it has spare capacity. ReturnTrip automatically
> matches it with nearby requests — Electronics (Vijayawada → Guntur), Clothing
> (Guntur → Hyderabad), Groceries (Vijayawada → Hyderabad) — and lets the driver
> accept extra bookings that fit.

---

## ✨ Features

- **Three user roles** — Admin, Delivery Company / Driver, and Customer, each with its own dashboard and access-controlled pages.
- **Smart return-route matching** — a real geographic algorithm (not random/hardcoded) that checks:
  1. whether pickup & drop-off lie within a corridor of the return route,
  2. correct travel direction (pickup before drop-off),
  3. remaining vehicle capacity,
  4. delivery deadline vs. estimated arrival,
  then **ranks feasible matches by score** and lists rejected ones with reasons.
- **Multi-product allocation** — one vehicle carries several requests while respecting weight, remaining capacity and handling info (dimensions + special care, not weight alone).
- **Interactive map** — Leaflet + map tiles showing original route, return route, pickups, drop-offs and a simulated vehicle position with distinct markers.
- **Booking & tracking** — 7 statuses (Request Submitted → Match Found → Booking Confirmed → Product Picked Up → In Transit → Delivered / Cancelled) with a customer-facing timeline.
- **Contact details** — validated 10-digit phone numbers shared between the matched driver and customer.
- **Accounts** — registration & login with role selection, form validation and strong-password rules.
- **Responsive UI** — professional navy / white / orange logistics design for laptop, tablet and mobile.

---

## 🛠️ Tech stack

| Layer | Technology |
|-------|-----------|
| Markup / styling | HTML5, CSS3 (no framework) |
| Logic | Vanilla JavaScript (no React/Angular/Vue) |
| Maps | [Leaflet.js](https://leafletjs.com/) + Esri / CARTO / OpenStreetMap tiles |
| Storage | Browser `localStorage` (demo mode) — swappable for Firebase Firestore |
| Hosting | Static — works on GitHub Pages or Netlify |

Everything lives in a **single `index.html` file** — no build step, no server.

---

## 🚀 Run it

**Locally:** download `index.html` and open it in any modern browser (Chrome, Edge, Firefox, Safari). An internet connection is needed only for the map tiles.

**Online (GitHub Pages):**
1. Put `index.html` at the repository root.
2. Repo **Settings → Pages → Branch: `main` / root → Save**.
3. Visit `https://<your-username>.github.io/<repo-name>/`.

---

## 🔑 Demo accounts

The app seeds demo data on first run. Log in with any of these (password **`demo123`**):

| Role | Email | Phone |
|------|-------|-------|
| Admin | `admin@demo.io` | 9000000001 |
| Driver | `driver@demo.io` (Ravi Kumar) | 9876500011 |
| Driver | `driver2@demo.io` (Anil Reddy) | 9876500022 |
| Customer | `customer@demo.io` (Priya Sharma) | 9123400011 |
| Customer | `customer2@demo.io` (Meena Rao) | 9123400022 |
| Customer | `customer3@demo.io` (Suresh Babu) | 9123400033 |

---

## 🧪 How to try the full flow

1. **As a driver** (`driver@demo.io`) → *My trips* already has an active return
   (Vijayawada → Guntur → Nalgonda → Hyderabad) → open **Find matches** to see ranked,
   compatible requests and **Accept** them (watch capacity update).
2. **As a customer** (`customer@demo.io`) → *New request* → submit a delivery →
   open **My requests** to see available returning vehicles and **Book** one.
3. **Track** the booking (customer) and **update status** (driver) through the 7 stages.
4. **As admin** (`admin@demo.io`) → monitor users, vehicles, trips, requests and bookings.

---

## 📦 Data / storage note

This build runs in **DEMO MODE**: all data is stored only in **this browser's
`localStorage`**. It is **not** shared between different users, browsers or devices,
and there is no backend server.

To make the data real and shared, replace the `DB` object's internals with
**Firebase Firestore** and wire `Auth` to **Firebase Authentication** — the rest of the
app reads/writes through `DB.*`, so the UI does not change. Suggested collections:
`users`, `vehicles`, `trips`, `deliveryRequests`, `bookings`, `trackingHistory`.

---

## 🗺️ Roadmap ideas

- Real Firebase Firestore + Auth backend with security rules
- Live GPS tracking instead of simulated position
- Real road-distance routing via OSRM for every match (partial support already included, with fallback)
- Payments and driver payouts
- Email / SMS notifications

---

## 📄 License

Released for educational / demonstration purposes. Add a license of your choice (e.g. MIT) if you plan to reuse it.
