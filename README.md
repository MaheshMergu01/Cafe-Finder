# Cafe Finder

A responsive JavaScript project that finds nearby cafes using live place data from Google Maps Platform.

## Features

- Search by city or area (for example, Solapur)
- Use the browser's current location (permission required)
- Display nearby cafes on an interactive Google Map
- Show cafe name, rating, address, price level (when supplied), and open status (when supplied)
- Open a cafe in Google Maps
- Responsive layout for mobile and desktop

## Requirements

- A Google account
- A Google Maps Platform project with billing enabled
- Maps JavaScript API and Places API (New) enabled
- An API key restricted to your website/referrer

## 1. Get a Google Maps API key

1. Open https://console.cloud.google.com/
2. Create or select a Google Cloud project.
3. Set up billing for the project.
4. Enable **Maps JavaScript API** and **Places API (New)**.
5. Create an API key under APIs & Services → Credentials.
6. Restrict the key to **Websites (HTTP referrers)** and allow only the APIs you enabled.
7. Do not publish an unrestricted key or commit it to a public GitHub repository.

Google Maps Platform usage may incur charges. Review the current pricing and free usage thresholds before deploying.

## 2. Add the API key

At the bottom of `index.html`, just before `</body>`, add this script tag. Replace `YOUR_API_KEY`:

```html
<script
  async
  src="https://maps.googleapis.com/maps/api/js?key=YOUR_API_KEY&loading=async&callback=initMap&v=weekly"
></script>
```

Keep `<script src="app.js"></script>` before the Google Maps script so `initMap` exists when the callback runs. This project imports the Maps, Places, and Marker libraries using `google.maps.importLibrary()` and uses **Nearby Search (New)**.

## 3. Run the project

1. Open the `cafe-finder` folder in VS Code.
2. Install the **Live Server** extension.
3. Right-click `index.html` → **Open with Live Server**.
4. Search for a city/area or click **Use my current location**.
5. Allow location permission if prompted.

Use `http://localhost` through Live Server rather than opening the file directly. Browser geolocation requires a secure context (localhost is treated as secure).

## Troubleshooting

- **Map is blank / API key error:** check the key, billing, API enablement, and website restrictions.
- **REQUEST_DENIED:** check that Maps JavaScript API and Places API are enabled for the same project and billing is active.
- **No cafes found:** try a larger town/area or search again.
- **Location blocked:** allow location access for your local development site, or use the text search.
- **Google Maps says your key is not authorized:** add your local origin/referrer (for example `http://127.0.0.1:5500/*` and/or `http://localhost:5500/*`) to the key's website restrictions.

## Project structure

```text
cafe-finder/
├── index.html
├── style.css
├── app.js
└── README.md
```

## Note about the API

This starter uses **Places API (New)** with `Place.searchNearby()` and a field mask. Google documents the new Nearby Search method here: https://developers.google.com/maps/documentation/javascript/nearby-search
