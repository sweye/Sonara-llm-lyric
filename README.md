# Sonara AI: Multi-Genre Lyric Generation Pipeline 🎤⚡

Sonara is an end-to-end automated data engineering and fine-tuning pipeline designed to train Large Language Models (LLMs) on high-fidelity, multi-genre lyric generation. 

The framework handles everything from dynamic chart-based data ingestion and automated regex feature-stripping to mathematically balanced dataset compilation and fast Supervised Fine-Tuning (SFT) via Unsloth.

---

## 🚀 Key Features

* **Dynamic Chart Scraping:** Directly interfaces with the Genius API to automatically discover and extract catalogs from top-charting global artists across major musical movements.
* **Regex Feature Eraser:** A specialized text-processing engine that strips out guest features (e.g., blocks owned by `[Verse 2: Guest Artist]`) while preserving the main artist's target style and neutral structural markers (`[Chorus]`, `[Bridge]`).
* **Mathematically Balanced Ingestion:** Prevents dataset "style bias" by enforcing an even 5,000-song split across 5 major parent music pillars, compiling a massive 25,000-track training matrix (~12.5M tokens).
* **Unsloth & HuggingFace Native:** Formats outputs into clean instruction-response pairs perfectly optimized for accelerated PEFT/LoRA fine-tuning.

---

## 📊 Dataset Matrix (25,000 Tracks)

To capture granular regional movements and sub-genres (like Rage Rap, Philly Drill, Dark Toronto R&B, and Americana) without chart limitations, the pipeline scales across 250 unique artists:

| Parent Tag | Covered Soundscapes | Target Artists | Max Tracks/Artist | Total Songs |
| :--- | :--- | :---: | :---: | :---: |
| **`rap`** | Rage, Drill, Jerk, Plugg, Trap, Boom-Bap | 50 | 100 | **5,000** |
| **`rb`** | Dark Alt-R&B, Trapsoul, Neo-Soul | 50 | 100 | **5,000** |
| **`pop`** | Synth-Pop, Dance-Pop, Indie Crossovers | 50 | 100 | **5,000** |
| **`country`**| Arena Country, Americana, Outlaw Country | 50 | 100 | **5,000** |
| **`rock`** | Emo-Rap, Alt-Rock, Grunge, Modern Punk | 50 | 100 | **5,000** |

---

## 🛠️ Installation & Setup

1. Clone the repository:
```bash
git clone [https://github.com/YOUR_USERNAME/sonara-ai.git](https://github.com/YOUR_USERNAME/sonara-ai.git)
cd sonara-ai
