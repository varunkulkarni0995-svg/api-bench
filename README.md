# API Bench

A lightweight, single-file API testing tool that runs in the browser. Pick a pre-configured API or add your own, fill a friendly input form, send the request, and read the result in plain language next to the raw JSON.

## Layout

| Pane | What it does |
|---|---|
| **Left** | Pre-configured APIs (weather, location, money, knowledge, practice) and **+ Add API** for your own |
| **Middle** | The request: method, URL, params, headers, body, auth. Raw response below with status, time and size |
| **Right** (collapsible) | **Inputs** as a form (dropdowns, multi-select, number fields) and the **Result** in readable form |

## Pre-configured APIs

| Group | API | Key needed |
|---|---|---|
| Gen AI | Gemini, Groq, OpenRouter, Hugging Face (chat + list models) | Free key per provider, stored only in your browser |
| Weather | Open-Meteo forecast and geocoding | No |
| Location | OSRM routing, Nominatim reverse geocoding | No |
| Money | Frankfurter exchange rates, CoinGecko crypto prices | No |
| Knowledge | REST Countries, Wikipedia summary, Countries GraphQL | No |
| Practice | JSONPlaceholder (GET / POST / PUT / DELETE), httpbin echo and error codes | No |

## Run it

- Open `index.html` in Chrome, or
- Use the GitHub Pages link once Pages is enabled for this repo

## Add your own API

1. Click **+ Add API**
2. Enter the URL. Write path inputs as `{name}`, e.g. `https://api.example.com/v1/items/{id}?city=NYC`
3. Click **Detect from URL**, then set a type, default and options for each input
4. Optional: a JSON body template using `{name}` placeholders

Your APIs are saved in this browser (localStorage).

## Limits

- Requests go straight from the browser, so only APIs that allow browser calls (CORS) respond
- Don't put real secret keys in a front-end tool; route keyed APIs through a backend
