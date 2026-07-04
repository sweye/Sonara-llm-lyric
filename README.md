# Sonara Lyrics Dataset Pipeline

An automated, robust Python pipeline built to compile high-quality song lyrics across multiple musical pillars (Rap, R&B, Pop, Country, Rock) for LLM fine-tuning and text generation tasks. 

This pipeline combines the official **Genius API** for hyper-accurate metadata extraction with an open-source, multi-provider engine (**syncedlyrics**) to bypass aggressive web-scraping restrictions and Cloudflare walls.

---

##  Key Features

* **Anti-Block Architecture**: Completely avoids web scraping (`beautifulsoup4`, `curl_cffi`, or `cloudscraper`) on high-security domains.
* **Smart Provider Filtering**: Explicitly isolates high-availability, open-source lyric databases (`Lrclib`, `NetEase`, `Megalobiz`) to completely eliminate `401 Unauthorized` token errors caused by restrictive platforms like Musixmatch.
* **Automatic LRC Cleansing**: Integrated regex engine strips away synchronized media timestamps (e.g., `[01:23.45]`) instantly, leaving behind pure text paragraphs.
* **State Preservation & Resumability**: Tracks progress at the artist level and caches intermediate saves to `/content/sonara_lyrics_dataset.json` inside Google Colab, ensuring zero data loss if a network timeout occurs.
* **Muted Error Logging**: Suppresses unnecessary background library warnings to provide a clean, accurate progress indicator via `tqdm`.

---

## 📦 Core Architecture

The dataset generation is executed through a structured cell-based pipeline:

1. **Cell 1**: Environmental configuration and dependencies setup.
2. **Cell 2 (The Run Engine)**: Resolves your curated artist matrix, queries metadata via Genius, safely extracts plain-text lyrics using alternative pipelines, and builds structural instructional prompts.
3. **Cell 3**: Model initialization, tokenization, and Parameter-Efficient Fine-Tuning (PEFT/LoRA) setup.
4. **Cell 4**: SFT Training execution featuring crash-safe checkpointing to Google Drive every 50 steps.
5. **Cell 5**: Manual weight exporting and merging.
6. **Cell 6**: Gradio-powered Private Lyrics Dashboard for testing and inference.

---

## 🛠️ Installation & Setup

Before initializing the runtime engine in **Cell 2**, remove old browser-impersonating scraping scrap and install the modern processing libraries:

```bash
# Install the core extraction library
pip install syncedlyrics tqdm requests

# Remove obsolete, blocked scraping dependencies
pip uninstall cloudscraper curl_cffi beautifulsoup4
