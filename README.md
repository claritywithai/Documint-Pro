# DocuMint Pro 🟢

**A free, 100% offline-first PDF & productivity toolkit — 68+ tools in a single HTML file. No backend, no uploads, no signups.**

Live demo: *add your GitHub Pages / hosting link here*

---

## ✨ What is DocuMint Pro?

DocuMint Pro is a self-contained, single-page web app that bundles dozens of everyday document and productivity tools — PDF editing, image processing, calculators, QR codes, and text utilities — into one privacy-first toolkit. Every operation runs **entirely in the browser** using client-side JavaScript libraries (pdf-lib, PDF.js, Tesseract.js, JSZip, SheetJS, etc.). No file is ever uploaded to a server.

## 🧰 Tools Included (68+)

### PDF — Organize
Merge PDF · Split PDF · Remove Pages · Extract Pages · Reorder Pages · Reverse Order · Insert Blank Pages · Scan to PDF

### PDF — Optimize
Compress PDF · Repair PDF · OCR PDF · Sanitize PDF · Redact PDF

### Convert to PDF
Image → PDF · Markdown → PDF · HTML → PDF · DOCX → PDF · XLSX → PDF · URL → PDF

### Convert from PDF
PDF → Images · PDF → Text · PDF → DOCX · PDF → Grayscale · PDF → Excel · PDF → CSV

### PDF — Edit
Watermark · Page Numbers · Rotate Pages · Metadata Editor · Digital Signature · Headers & Footers

### PDF — Security
Password Protect · Unlock PDF

### Calculators
Scientific Calculator · Currency Converter · Unit Converter · BMI Calculator · Tip Calculator · Loan/EMI Calculator · Age & Date Calculator · Percentage Calculator · Password Generator

### QR Codes
QR Generator · QR Scanner · Batch QR

### Audio
Text to Speech · Speech to Text · Audio Recorder

### Images
Compress Image *(Squoosh-style: JPEG/PNG/WebP/AVIF, Fast or Advanced MozJPEG/OxiPNG engine, live before/after preview)* · **Resize Image** *(now with AVIF)* · Convert Image · Image Editor · Meme Generator

### Productivity
Notepad + Markdown · To-Do/Checklist · Text Diff Checker · ZIP Tool · Clipboard Manager · Secure Vault

### AI-Adjacent Text Tools
Text Summarizer · Grammar & Readability Checker · PDF Keyword Search · Keyword Extractor · Contract Templates

### Business
CSV Visualizer · Invoice Generator · Resume Builder · Expense Tracker · Meeting Notes · Business Card OCR

### Developer / Misc
Font Inspector · Steganography · Color Palette Picker · Regex Tester

## 🗜️ Image Compression Engines

The Compress Image tool now offers two engines, similar to [Squoosh](https://squoosh.app):

- **⚡ Fast (Browser native)** — Uses the browser's built-in Canvas API. Fully offline, works instantly, supports JPEG/PNG/WebP/AVIF.
- **🎯 Advanced (MozJPEG / OxiPNG)** — Loads [jSquash](https://github.com/jamsinclair/jSquash) WASM codecs from a CDN on first use for noticeably smaller file sizes at the same visual quality. Requires an internet connection the first time it's used per session; falls back automatically to the Fast engine if it can't load (e.g. offline).

A live before/after preview with file-size comparison updates as you change format, engine, or quality.

## 🗂️ Sidebar Navigation

Tools are grouped into 15 collapsible categories (PDF Organize, PDF Optimize, Convert to/from PDF, Edit PDF, Security, Calculators, QR & Barcode, Speech Tools, Image Tools, Utilities, Vault, Smart Tools, Data & Docs, Creator Tools). Click a category title to expand/collapse its tools — only the first category is open by default, keeping the sidebar compact. Searching automatically expands any category with a match.

## ⚡ Performance: Lazy Loading

To keep first-load fast (especially on slow connections), only the libraries needed by nearly every tool — pdf-lib, PDF.js, JSZip, FileSaver — load eagerly (with `defer` so they don't block rendering). Heavier, single-purpose libraries load **on demand**:

| Library | Used by | Loads when |
|---|---|---|
| Tesseract.js | OCR PDF, Business Card OCR | Tool opened / OCR run |
| Mammoth.js | DOCX → PDF | Tool opened / conversion run |
| SheetJS (xlsx) | XLSX → PDF, PDF → Excel, PDF → CSV, CSV Visualizer | Tool opened / file processed |
| Chart.js | CSV Visualizer | Chart rendered |
| ZXing | QR Scanner | Scan started |
| QRCode.js | QR Generator, Batch QR | Code generated |
| markdown-it + highlight.js | Markdown → PDF, Notepad | Tool opened / preview typed |
| math.js | Scientific Calculator | `=` pressed |
| html2pdf.js | All "export to PDF" tools (notepad, invoices, contracts, etc.) | Export triggered |

Each lazy load is cached after first use, and falls back gracefully with an on-screen error if the library can't be fetched (e.g. no internet) instead of crashing.

## 🔒 Privacy by Design

- All file processing happens **locally in your browser** (client-side JS only)
- No files are uploaded, stored, or transmitted to any server
- Preferences (theme, language) are saved only in `localStorage`
- Full privacy policy, terms, disclaimer, and accessibility statement are built into the app (see footer modals)

## 🛠️ Tech Stack

Vanilla HTML / CSS / JavaScript — no build step, no framework, no bundler. Single `.html` file.

**Libraries (via CDN):**
- [pdf-lib](https://pdf-lib.js.org/) — PDF creation/editing
- [pdf.js](https://mozilla.github.io/pdf.js/) — PDF rendering
- [Tesseract.js](https://tesseract.projectnaptha.com/) — OCR
- [QRCode.js](https://davidshimjs.github.io/qrcodejs/) & [ZXing](https://github.com/zxing-js/library) — QR generation/scanning
- [JSZip](https://stuk.github.io/jszip/) + [FileSaver.js](https://github.com/eligrey/FileSaver.js/) — archiving & downloads
- [math.js](https://mathjs.org/) — calculator engine
- [mammoth.js](https://github.com/mwilliamson/mammoth.js) — DOCX parsing
- [SheetJS (xlsx)](https://sheetjs.com/) — spreadsheet conversion
- [markdown-it](https://github.com/markdown-it/markdown-it) — Markdown rendering
- [Chart.js](https://www.chartjs.org/) — data visualization
- [highlight.js](https://highlightjs.org/) — code syntax highlighting
- [html2pdf.js](https://github.com/eKoopmans/html2pdf.js) — HTML to PDF export

## 🚀 Usage

No installation or build process required.

1. Clone or download this repo
2. Open `documint_pro.html` directly in any modern browser, **or**
3. Deploy it as a static site (GitHub Pages, Netlify, Vercel, Cloudflare Pages, etc.)

```bash
git clone https://github.com/<your-username>/documint-pro.git
cd documint-pro
# just open the file
open documint_pro.html   # macOS
# or double-click it in your file explorer
```

### Deploying to GitHub Pages

1. Push this repo to GitHub
2. Go to **Settings → Pages**
3. Set source to your default branch, root folder
4. Your toolkit will be live at `https://<your-username>.github.io/<repo-name>/`

## ✅ Quality Checks Performed

- HTML structure validated (all tags balanced)
- CSS validated (all rule blocks balanced)
- JavaScript validated with `node --check` (no syntax errors)
- All sidebar navigation items confirmed to map to a working tool section
- SEO essentials added: meta description, Open Graph, Twitter Card, canonical tag, and JSON-LD structured data for better discoverability by search engines and AI/LLM-based answer engines

## 📈 SEO / GEO Notes

This build includes:
- Descriptive `<title>` and `<meta description>` tuned for search intent
- Open Graph & Twitter Card tags for clean social link previews
- `SoftwareApplication` JSON-LD schema so search engines and AI assistants can correctly describe the tool
- A "Resources & Guides" section with relevant outbound links for additional context

> ⚠️ Before deploying, update the `canonical`, `og:url`, and contact email placeholders in the `<head>` and footer to match your actual domain.

## 📄 License

Add your preferred license here (MIT recommended for open-source toolkits).

## 🤝 Contributing

Issues and pull requests are welcome. If you spot a bug in any tool, please include the browser/OS and steps to reproduce.

---

Made with 🟢 — works entirely offline, your files never leave your device.
