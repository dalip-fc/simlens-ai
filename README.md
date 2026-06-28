# SimLens — AI-Powered Document Intelligence Terminal

> A single-file, browser-native AI research assistant for simulation engineers.  
> Upload technical papers → extract insights → explore knowledge graphs → generate slides → export to PowerPoint.

Powered by **Google Gemini 2.5 Flash** · Runs entirely in your browser · No backend · No server

---

## Live Demo

🔗 **[Try SimLens →](https://simlens-ai.vercel.app)**

---

## What is SimLens?

SimLens is an AI agent for simulation document intelligence. Upload up to 5 technical papers and instantly extract insights, visualise concept relationships, compare methodologies, and generate presentation-ready slides — all without leaving your browser.

The entire application is a **single `index.html` file**.

---

## Features

### 📄 Lens View
- **Full PDF View** — renders any PDF page at full fidelity with zoom, navigation, and Fit-to-window
- **Quick Insight** — AI automatically extracts the paper title, authors, summary, tools used, topics, and key conclusions on upload

### 🧠 Neural Map
- D3.js force-directed knowledge graph built from the document's concepts, processes, inputs, outputs, and results
- Zoom, pan, drag nodes to explore — Regenerate or Fit-to-window with one click

### ⚖ Compare
- Side-by-side AI comparison of two documents across Summary · Tools Used · Methodology · Key Findings · Conclusions
- AI Recommendation highlights the best-match document for your search query

### 📊 AI Slides
- Auto-generates a presentation slide per document with Objective, Solution / Approach, and Key Findings
- Right side shows three actual figure snapshots pulled directly from the PDF pages
- Footer displays the extracted paper title and authors
- Prev / Next navigation across all active documents
- Slides are cached — switching tabs never re-generates (no wasted API tokens)
- One-click export to **.pptx** (PowerPoint compatible)

### 💬 AI Assistant
- Persistent chat panel available on every tab
- Answers questions grounded in your uploaded documents
- One-tap prompt shortcuts: Quick Summary · Tools Used · Topics Covered · References · Key Conclusions

---

## Getting Started

### 1. Get a Gemini API Key
Create a free key at [Google AI Studio](https://aistudio.google.com/app/apikey).

### 2. Open the App
Use the [live deployment](https://simlens-ai.vercel.app) or open `index.html` directly in your browser — no installation required.

### 3. Add Your API Key
Click the pill in the top-right corner and paste your Gemini API key. It is stored only in your browser's `localStorage` and is never sent anywhere except Google's Gemini API.

### 4. Upload Documents
Drag and drop up to **5 documents** (PDF, TXT, or MD) into the left panel. Extraction starts automatically.

### 5. Explore
Switch between tabs — Lens View, Neural Map, Compare, Slides — and use the AI Assistant chat panel on the right at any time.

---

## Tech Stack

| Layer | Technology |
|---|---|
| UI Framework | React 18 (UMD, no build step) |
| Styling | Tailwind CSS |
| AI / LLM | Google Gemini 2.5 Flash |
| PDF Rendering | PDF.js 3.11 |
| Knowledge Graph | D3.js v7 |
| PPTX Export | PptxGenJS 3.12 |
| Binary Storage | IndexedDB (PDF binaries, no size limit) |
| Metadata Storage | localStorage (text, extracted insights) |

---

## Architecture

```
┌─────────────────────────────────────────────────────┐
│                   index.html                        │
│                                                     │
│  ┌─────────────┐  ┌──────────────┐  ┌───────────┐  │
│  │  Lens View  │  │  Neural Map  │  │  Compare  │  │
│  │  Full PDF   │  │  D3 Graph    │  │  AI Table │  │
│  │  Quick AI   │  │              │  │           │  │
│  └─────────────┘  └──────────────┘  └───────────┘  │
│                                                     │
│  ┌─────────────┐  ┌──────────────────────────────┐  │
│  │   Slides    │  │       AI Assistant Chat       │  │
│  │  AI + PDF   │  │  (persistent across all tabs) │  │
│  │  PPTX Out   │  │                              │  │
│  └─────────────┘  └──────────────────────────────┘  │
│                                                     │
│  ┌─────────────────────────────────────────────┐    │
│  │        Google Gemini 2.5 Flash              │    │
│  │  Structured JSON extraction · Q&A · Slides  │    │
│  └─────────────────────────────────────────────┘    │
│                                                     │
│  IndexedDB (PDF binaries)  ·  localStorage (meta)   │
└─────────────────────────────────────────────────────┘
```

### Agentic Workflow

```
Upload → Auto-Extract (title, authors, insights)
       → Neural Map (concept graph)
       → Compare (multi-doc AI analysis)
       → Q&A (document-grounded chat)
       → Slides (AI content + PDF figure capture)
       → PPTX Export
```

---

## Privacy & Security

- Your API key lives in `localStorage` only — never hardcoded, never logged, never sent to any server other than Google's Gemini API endpoint
- PDF binary data is stored in **IndexedDB** locally in your browser — persists across page refreshes without size limits
- No analytics, no telemetry, no cookies, no tracking of any kind
- All processing happens client-side in your browser

---

## Running Locally

No build step needed:

```bash
# Clone the repo
git clone https://github.com/dalip-fc/simlens-ai.git
cd simlens-ai

# Open directly in browser
open index.html          # macOS
start index.html         # Windows
xdg-open index.html      # Linux
```

Or serve it for a cleaner experience:

```bash
npx serve .
# Open http://localhost:3000
```

---

## Project Structure

```
simlens-ai/
├── index.html          # The entire application
├── generate-pitch.html # Pitch deck generator (open in browser → downloads PPTX)
└── README.md
```

---

## License

MIT — free to use, modify, and distribute.
