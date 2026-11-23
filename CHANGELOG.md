# Versions

Every page in API Bench carries its own version number in small text next to its
title. Click it to come here.

The four pages ship and change independently, so they have separate version
numbers. There is no single "API Bench version".

| Page | File | Version |
|---|---|---|
| API tester (home) | `index.html` | **v1.3.3** |
| Compare models | `compare.html` | **v1.5.0** |
| Web research | `web.html` | **v1.2.4** |
| Vision eval | `vision.html` | **v1.1.0** |
| Device check | `device.html` | **v1.0.0** |

How to read the numbers: **major.minor.patch** — a new way of working bumps the
minor, a fix or a small adjustment bumps the patch.

---

## API tester — `index.html`

The home page. Versions before v1.3.2 were not shown on the page; they are
reconstructed here from the commit history.

| Version | What changed |
|---|---|
| **v1.3.3** | Link to Device check added |
| v1.3.2 | Version number now shown on the page, next to the API Bench name in the sidebar |
| v1.3.1 | Link to Vision eval added |
| v1.3.0 | Photon place search and reverse lookup added |
| v1.2.0 | Copy buttons for inputs, request, curl, response, result and all |
| v1.1.0 | Free Gen AI APIs: Gemini, Groq, OpenRouter, Hugging Face |
| v1.0.0 | First release — three-pane browser API tester |

## Compare models — `compare.html`

| Version | What changed |
|---|---|
| **v1.5.0** | Take photo — capture an image with the device camera instead of uploading a file; resized to 1280px and stripped of metadata in the browser before it is sent |
| v1.4.3 | Link to Device check added |
| v1.4.2 | Groq default model is now `openai/gpt-oss-120b` (llama-3.3 was retired by Groq); links to Web research and Vision eval added |
| v1.4.1 | Rows start with a model, model lists load automatically, Run is blocked with a clear message when a row has no model |
| v1.4.0 | Image and PDF attachments, capability detection, section swap |
| v1.3.4 | Full model list in a dropdown, lists saved in the browser, non-chat Groq models hidden |
| v1.3.3 | Models that reject `temperature` are re-sent without it automatically, noted in the evidence |
| v1.3.2 | Version label shown on the page |
| v1.3.1 | Re-clicking Conversation no longer resets the session; evidence export includes every session's transcript |
| v1.3.0 | Conversation mode — the main button continues the session (Start / Send turn N) |
| v1.2.0 | Mistral, Cohere, DeepSeek, Together, Fireworks, OpenAI and Anthropic providers; free model defaults refreshed; thinking / empty / cut-off and refusal flags, seed |
| v1.1.0 | Full request and response in the evidence log, reliable copy, error types, run id and attempts, trials, JSON export |
| v1.0.0 | First release — same prompt to many Gen AI models, evidence export |

## Web research — `web.html`

| Version | What changed |
|---|---|
| **v1.2.4** | Link to Device check added |
| v1.2.3 | Link to Vision eval added |
| v1.2.2 | On review sites the brand must appear in the page title or the link, not anywhere on the page |
| v1.2.1 | Review-site pages must still name the brand |
| v1.2.0 | Review-site queries run without the date filter; shop listings dropped (Walmart item pages, Shein, Temu, eBay) |
| v1.1.0 | Search asked for recent results (`tbs`), review sites kept and their dated entries read, the brand's own site dropped, drop reasons shown, clearer empty result |
| v1.0.0 | First release — Serper / Firecrawl / Tavily search, Firecrawl / Jina / WebScraping.AI reading, LLM summary with the Web researcher prompt; brand, date and Amazon filters; JSON and Markdown export |

## Vision eval — `vision.html`

| Version | What changed |
|---|---|
| **v1.1.0** | Take photo — shoot a garment with the device camera and it becomes a fixture, ready to run against every model |
| v1.0.2 | Link to Device check added |
| v1.0.1 | Version number links here |
| v1.0.0 | First release — one fixed JSON shape enforced across every model, scored against your own labels. Enforcement selector (auto / schema / JSON mode / prompt only), negative fixtures, calibration error, warmth spread, uniform-confidence and unobservable-claim checks, model disagreement table, CSV / Markdown / JSON export |

## Device check — `device.html`

| Version | What changed |
|---|---|
| **v1.0.0** | First release — camera (lens selection, stream resolution, capture, resize to the size actually sent to a model) and EXIF inspection on library photos: whether GPS was present and whether the resize removed it, plus the orientation tag. Passkey section: platform authenticator detection, create and verify, user-verification flags. Markdown report. Everything runs on the device; nothing is sent anywhere |
