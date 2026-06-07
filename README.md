# Space Translate

**Live captions + translation, right in your browser. No install, no API key for the basics.**

Capture the audio of any tab (X Spaces, YouTube, talks…) and get a live, time-stamped
transcript with side-by-side translation — and optionally let an AI rewrite the
fragments into clean, readable prose or a short summary.

It's a single self-contained HTML page. Everything runs client-side.

---

## ✨ Features

- 🎧 **Captures system/tab audio** via screen-share — works even with headphones on.
- 📝 **In-browser speech-to-text** with **OpenAI's open-source Whisper** model — downloaded once
  from **[Hugging Face](https://huggingface.co/)** (the standard public AI-model hub) and cached.
  Audio never leaves your device.
- 🌐 **Free translation** (Lingva → MyMemory fallback). No API key required.
- 📋 **AI "refine / summarize"** (optional): turn choppy captions into readable text, or summarize.
  Bring your own key — Gemini / Groq / OpenRouter / Claude / Grok — or just copy the captions
  into your usual AI.
- 🪟 **Stays on the page while sharing** (uses `CaptureController.setFocusBehavior`).

## 🗂 Files

| File | What it is |
|------|------------|
| `index.html` | Marketing landing page |
| `app.html`   | The tool — left = intro/shared video, right = live caption feed |
| `torijima.html` | Alternate concept/promo page |

## ▶️ Run it

Screen capture (`getDisplayMedia`) requires a **secure context**, so open it over
`localhost` or `https` (not a raw file path or LAN IP).

```bash
# from this folder
npx http-server . -p 8000 -c-1
#   or
python -m http.server 8000
```

Then open **http://localhost:8000/app.html** in **desktop Chrome / Edge**.

1. Open the page you want to translate in **another tab**.
2. Press **▶ START**. On the **first run** it safely downloads the open-source Whisper model
   (a few tens of MB, from Hugging Face) and caches it — no re-download after that.
3. Pick that tab and **tick “Also share tab audio.”**

> macOS only allows **tab** audio (no full-system audio). Chrome / Edge desktop recommended.

## 🔒 Privacy

- **Speech-to-text** runs **locally in your browser**; audio is not uploaded.
- **Translation** sends the transcribed text to a free public translation service.
- **AI refine/summarize** sends text to the provider you choose, using a key **you** enter.
  Keys are stored only in your browser's `localStorage` — never in this code.

## 🛠 Tech

Vanilla HTML/CSS/JS · [🤗 Transformers.js](https://github.com/huggingface/transformers.js) (Whisper) ·
Lingva / MyMemory translation · optional LLM APIs.

---

*Prototype. Built for fun.*
