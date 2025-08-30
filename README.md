# LLM Agent POC — Browser-based (RAJNEESH)

**Author:** RAJNEESH  
**GitHub:** https://github.com/Raj-RR2004

This is a minimal browser-based LLM agent proof-of-concept. It demonstrates the OpenAI-style **function-calling** workflow and three tool integrations:
- **search** — web search (SerpAPI if provided; DuckDuckGo Instant Answer as fallback)
- **aipipe** — call an AI Pipe proxy endpoint (user-provided)
- **run_js** — execute JavaScript in a sandboxed iframe and return the result

> Security note: This POC runs in the browser and requires the user to paste their API keys directly into the UI. **Do not** use production secrets in public demos. For production, move API calls to a server-side proxy.

---

## Files
- `index.html` — single-file web app (HTML + JS) (open this in your browser)
- `README.md` — this file
- `WRITEUP.md` — 200–300 word explanation (deliverable)
- `LICENSE` — MIT license

---

## Quickstart (no install)
1. Extract the zip and open `index.html` in a modern browser (Chrome/Edge/Firefox).
2. In the Settings panel, paste your **OpenAI API Key** (or an equivalent provider). For search, optionally paste a **SerpAPI key**.
3. Type a message and press **Send**.
4. If the LLM requests `search`, `aipipe`, or `run_js`, the app will attempt to execute the tool and feed the result back to the model automatically.

---

## How to get keys
### OpenAI
1. Create an account at https://platform.openai.com/
2. Go to API Keys → Create new secret key → copy it. Paste into the app's OpenAI API Key input.

### SerpAPI (optional, for reliable search)
1. Create an account at https://serpapi.com/
2. Copy your API key and paste into the SerpAPI Settings field.
If you don't provide a SerpAPI key, the app will attempt DuckDuckGo's Instant Answer API as a fallback.

### AI Pipe (optional)
- If you run or have access to an AI Pipe proxy, paste its endpoint URL into the AI Pipe field. The app will POST `{ "input": "..." }` to that URL when the agent asks for `aipipe`.

---

## Deploy (GitHub Pages)
1. Create a GitHub repo `auto-llm-agent` and push these files.
2. In GitHub repo settings → Pages → Deploy from `main` branch `/ (root)`.
3. The site will be live at `https://<your-username>.github.io/auto-llm-agent/`

---

## Troubleshooting & notes
- If OpenAI returns errors about invalid key or model, re-check your key and model name.
- SerpAPI may have CORS or rate limits; if search fails, try the DuckDuckGo fallback or use a server proxy.
- The POC intentionally keeps code minimal for hackability.
