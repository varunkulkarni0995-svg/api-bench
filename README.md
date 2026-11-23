# API Bench

A lightweight, single-file API testing tool that runs in the browser. Pick a pre-configured API or add your own, fill a friendly input form, send the request, and read the result in plain language next to the raw JSON.

## Versions

Each page shows its own version in small text next to its title — click it to open
[CHANGELOG.md](CHANGELOG.md), which lists what changed in every version of every page.
The four pages ship independently, so they have separate version numbers.

| Page | File | Version |
|---|---|---|
| API tester (home) | `index.html` | v1.3.3 |
| Compare models | `compare.html` | v1.5.0 |
| Web research | `web.html` | v1.2.4 |
| Vision eval | `vision.html` | v1.2.1 |
| Device check | `device.html` | v1.0.0 |

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
| Location | Photon place search + reverse, OSRM routing, Nominatim reverse geocoding | No |
| Money | Frankfurter exchange rates, CoinGecko crypto prices | No |
| Knowledge | REST Countries, Wikipedia summary, Countries GraphQL | No |
| Practice | JSONPlaceholder (GET / POST / PUT / DELETE), httpbin echo and error codes | No |

## Web research (web.html)

Tests the Fit Check Web researcher end to end: **search → read pages → summarize**.

| Step | Tools | Notes |
|---|---|---|
| 1 Search | Serper (recommended), Firecrawl search, Tavily | Drops Amazon pages, results without the exact brand name, and anything older than the window. Undated results are checked on the page itself |
| 2 Read pages | Firecrawl (recommended) with Jina Reader or WebScraping.AI as backup | Reddit, Amazon, YouTube and social sites are never opened; their snippets are used |
| 3 Summarize | Groq, Gemini or OpenRouter with the Web researcher prompt (`webresearch_prompt.txt`) | Output is the JSON the Fit Check Decider expects |

Export JSON or Markdown after a run to grade it. Keys are shared with Compare models and stay in your browser.

## Vision eval (vision.html)

Compare models shows you prose. This page forces every model into **one fixed JSON shape** and
scores the answers against labels you set yourself.

| Step | What you do |
|---|---|
| 1 Models | Pick any vision-capable models. Rows that can't see images are flagged and skipped |
| 2 Task | A prompt and a JSON Schema. Ships with the Layer Up garment reading; edit either |
| 3 Fixtures | Drop photos **or shoot one with the camera**, label each. Mark photos with **no garment** as negatives |
| 4 Run | Every model × every fixture, one call each |

**Enforcement is the experiment.** "Auto" uses each provider's strongest mechanism — a response
schema on Gemini, a forced tool call on Anthropic, `json_schema` on OpenAI-compatible routes.
Set it to **Prompt only** to find out which models hold the shape with nothing but instructions.
That gap is usually the most useful number on the page.

What it measures per model:

| | |
|---|---|
| Returned usable JSON | And how often it needed repairing — a fenced or embedded reply counts as a miss |
| Refused every negative | A model that reads a garment out of a desk has failed. Pass bar is 100% |
| Slot accuracy, warmth error, flag accuracy | Against your labels |
| Warmth spread | Catches a model that rates everything the same |
| Unobservable claims | Brands and fibre compositions a photo can't show. A legible label cited in evidence is exempt |
| Uniform confidence | One number for every field means the confidences are decoration |
| Calibration error | Whether a stated 0.9 means 90%. Without this the other numbers can't be acted on |
| Latency and tokens | What actually decides which one you ship |

It also shows **where models disagree** on the same photo — different slot, or warmth more than
2 apart. Those are the photos worth looking at yourself.

Export CSV, Markdown or JSON. Keys are shared with Compare models and stay in your browser.

## Device check (device.html)

What the phone or laptop in your hand actually gives a web app. Nothing leaves the device; there are no keys and no network calls.

| Section | What it answers |
|---|---|
| **Camera** | Which lens you get when you ask for the back one, what resolution the stream hands over, and how big the photo is before and after the resize that gets sent to a model |
| **Camera — library photo** | Whether a photo already on the device carries EXIF, whether that includes **GPS**, and whether the resize removes it. Also flags an orientation tag, which a plain canvas redraw ignores — that is how a photo reaches a model rotated |
| **Auth — passkeys** | Whether there is a built-in authenticator (Touch ID, Windows Hello, Android screen lock), how long create and verify take, and whether the device actually did a biometric check or just confirmed someone was there |

The passkey test is local: the challenge is random and no server verifies the signature, so it answers whether the hardware and the prompt work here, not whether a login is secure.

Location, motion sensors, clipboard, notifications, storage quota and network type come next.

## Run it

- Open `index.html` in Chrome, or
- Use the GitHub Pages link once Pages is enabled for this repo

## Copy and paste

| Button | Copies |
|---|---|
| **Copy all** (top) | Inputs, request, response and readable result as one Markdown block |
| **Copy request** / **Copy as curl** | The request as plain HTTP text, or as a curl command for the terminal |
| **Copy response** | Status, time, size and the JSON body |
| **Copy** (Inputs / Result) | The form values, or the plain-language result |

API keys are always replaced with placeholders like `<gemini_key>` in anything copied. Very large responses are cut at 20,000 characters.

## Add your own API

1. Click **+ Add API**
2. Enter the URL. Write path inputs as `{name}`, e.g. `https://api.example.com/v1/items/{id}?city=NYC`
3. Click **Detect from URL**, then set a type, default and options for each input
4. Optional: a JSON body template using `{name}` placeholders

Your APIs are saved in this browser (localStorage).

## Limits

- Requests go straight from the browser, so only APIs that allow browser calls (CORS) respond
- Don't put real secret keys in a front-end tool; route keyed APIs through a backend
