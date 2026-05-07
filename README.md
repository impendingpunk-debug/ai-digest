# ⚡ AI Digest

A lightweight, zero-backend personal news app that delivers a daily briefing of the latest AI headlines — powered by Claude with live web search.

---

## Overview

AI Digest is a single-file web application built entirely in vanilla HTML, CSS, and JavaScript. There are no servers, no databases, no subscriptions, and no third-party accounts required beyond an Anthropic API key. Open the file in a browser, tap a button, and within seconds you have a curated, sourced list of today's most important AI news organized by topic.

The app was designed with mobile-first use in mind — it can be saved to your phone's home screen and used like a native app.

---

## Features

- **On-demand news fetch** — tap once to pull the latest AI headlines from across the web via Claude's live web search
- **Headline-first design** — clean numbered list per category, tap any headline to open the original article directly
- **7-day rolling archive** — automatically keeps the last 7 days of digests in browser storage; older entries rotate out
- **Four coverage categories** — Model Releases & Updates, Research & Papers, Tools & Apps, and Tutorials & How-Tos
- **Broad source coverage** — Anthropic, OpenAI, Google DeepMind, open source AI (Meta, Mistral, Hugging Face), and AI startups
- **Fully client-side** — no backend, no data leaves your browser except the API call to Anthropic
- **Mobile PWA-ready** — add to home screen on iOS or Android for a native app experience
- **Dark mode UI** — purpose-built dark theme with animated ambient background

---

## Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML, CSS, JavaScript |
| AI / Search | Anthropic Claude API (`claude-sonnet-4`) with `web_search` tool |
| Storage | Browser `localStorage` |
| Fonts | Syne (display) + DM Mono (body) via Google Fonts |
| Hosting | Any static host — GitHub Pages, Netlify, or local file |

No frameworks. No build step. No dependencies to install.

---

## How It Works

1. On first load, the app prompts you to enter your Anthropic API key. The key is stored only in your browser's `localStorage` and is never sent anywhere except directly to the Anthropic API.
2. When you tap **⚡ Fetch Today's Digest**, the app sends a structured prompt to Claude asking it to search the web and return today's top AI news in a strict JSON format.
3. Claude performs multiple live web searches, then returns a structured response with headlines, summaries, and source URLs organized by category.
4. The app parses the response (with a multi-stage JSON repair fallback for malformed output), renders it as a tappable headline list, and saves the entry to your local archive.
5. Each headline links directly to the original article or source.

---

## Getting Started

### Run locally

1. Download `ai_digest_app.html`
2. Open it in any modern browser
3. Enter your Anthropic API key when prompted (get one at [console.anthropic.com](https://console.anthropic.com))
4. Tap **⚡ Fetch Today's Digest**

### Host on GitHub Pages (recommended)

1. Create a new GitHub repository (private recommended)
2. Upload `ai_digest_app.html` and rename it to `index.html`
3. Go to **Settings → Pages → Source** and select the main branch
4. Your app will be live at `https://yourusername.github.io/your-repo-name`

### Add to your phone home screen

- **iOS Safari:** tap the Share icon → Add to Home Screen
- **Android Chrome:** tap the menu (⋮) → Add to Home Screen

---

## Configuration

The only required configuration is your Anthropic API key, entered in the app UI on first use.

To change which topics are covered or adjust the number of headlines per section, edit the `prompt` variable inside the `fetchDigest()` function in the HTML file.

---

## Privacy

- Your API key is stored only in your own browser's `localStorage`
- Digest data (headlines, summaries, links) is stored only in your own browser's `localStorage`
- No analytics, no tracking, no external requests except the Anthropic API call you initiate

---

## Cost

Each digest fetch makes one API call to Claude with web search enabled. At current Anthropic pricing this costs approximately **$0.01–$0.03 per fetch** depending on how much web search is performed. Fetching once per day costs well under $1/month.

---

## Project Context

This app was built through an iterative, conversational design process — starting from a simple idea (a daily AI news email) and evolving through several formats (email digest → Notion integration → standalone web app) before landing on this minimal, fully client-side approach. The final design prioritizes speed, simplicity, and privacy over features.

---

## License

MIT — do whatever you want with it.
