# claude-sandbox-env

> 🇷🇺 [Читать на русском](README_RU.md)

A full snapshot of the isolated Linux execution environment that Claude (Anthropic) uses when processing requests with the "computer use" / tool-execution feature. Exported from a live container and published for reference, research, and reproducibility.

---

## What's inside

### System
| Parameter | Value |
|-----------|-------|
| OS | Ubuntu 24.04.4 LTS (Noble Numbat) |
| Kernel | Linux 4.4.0 (runsc / gVisor) |
| CPU | Intel Xeon Skylake-SP, 2 vCPUs @ 2800 MHz, AVX-512 |
| RAM | 9.0 GiB total, ~8.8 GiB available |
| Root disk | 9.9 GB (259 MB used) |
| Scratch mounts | `/mnt/user-data/uploads`, `/mnt/user-data/outputs`, `/mnt/transcripts` |

### Python packages (`pip_packages.txt`)
Over 50 pre-installed libraries, including:
- **Data / ML**: `pandas`, `numpy`, `scikit-learn`, `tensorflow`, `flatbuffers`
- **Document processing**: `python-docx`, `openpyxl`, `pypdf`, `camelot-py`, `img2pdf`, `markitdown`, `beautifulsoup4`, `lxml`
- **Image / Video**: `Pillow`, `imageio`, `imageio-ffmpeg`, `sharp` (npm)
- **Web / Network**: `Flask`, `requests`, `httplib2`, `cryptography`
- **Utilities**: `click`, `Jinja2`, `magika`, `graphviz`, `grip`

### Node.js / npm packages (`npm_packages.txt`)
- `playwright` — headless browser automation
- `pptxgenjs` — PowerPoint generation
- `@mermaid-js/mermaid-cli` — diagram rendering
- `react` + `react-dom` — UI component rendering
- `typescript`, `ts-node`, `tsx` — TypeScript toolchain
- `docx`, `pdf-lib`, `pdfjs-dist` — document/PDF manipulation
- `marked`, `markdown-pdf`, `markdownlint-cli2` — Markdown tooling
- `sharp` — high-performance image processing

### Skills (`/mnt/skills/`)
Skills are structured instruction sets that tell Claude how to perform specific tasks reliably.

**Public skills** (`skills/public/`):
| Skill | Purpose |
|-------|---------|
| `docx` | Create and edit Word documents via `python-docx` |
| `xlsx` | Create and edit Excel spreadsheets via `openpyxl` |
| `pptx` | Create and edit PowerPoint presentations via `pptxgenjs` |
| `pdf` | Create, merge, split, fill PDF forms via `pypdf` / `pdf-lib` |
| `pdf-reading` | Extract and analyze content from PDFs |
| `file-reading` | Smart dispatcher — correct reading strategy per file type |
| `frontend-design` | Build polished UI components (React, HTML/CSS, Tailwind) |
| `product-self-knowledge` | Up-to-date facts about Claude and Anthropic products |

**Example skills** (`skills/examples/`):
`skill-creator`, `mcp-builder`, `canvas-design`, `algorithmic-art`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `doc-coauthoring`, `internal-comms`, `event-planning`, `meal-delivery`, `grocery-shopping`, `return-refund`, `cancel-unsubscribe`, `hire-help`, `prescription-refill`, `file-expenses`, `benepass-reimbursement`, `financial-calculator`, `brand-guidelines`, `file-form`, `call-to-book`

### Environment variables (`env_vars.txt`)
Key runtime variables: `HOME=/root`, `PATH` includes `/home/claude/.npm-global/bin`, `/usr/local/sbin`, standard Ubuntu paths. No user-identifying secrets are present.

### Process snapshot (`processes.txt`)
At export time, the container had one primary supervisor process (`process_api`) plus a Python script that generated the export itself.

### File tree (`full_file_tree.txt`)
A complete recursive listing of all files accessible in the container at export time (~16 MB uncompressed).

---

## Repository name ideas

| Name | Style |
|------|-------|
| `claude-sandbox-env` | Clean, descriptive |
| `claude-container-snapshot` | Explicit |
| `anthropic-execution-env` | Formal |
| `claude-tool-env` | Short |
| `inside-claude-box` | Catchy |

---

## About (for GitHub)

> A complete snapshot of Claude's isolated Linux execution environment — OS, CPU/RAM specs, all pre-installed Python and Node.js packages, Skills (structured instruction sets), environment variables, running processes, and full file tree. Useful for anyone building on top of Claude's tool-use / computer-use capabilities.

**Topics / tags:**
`claude` `anthropic` `ai` `llm` `sandbox` `container` `ubuntu` `python` `nodejs` `skills` `computer-use` `tool-use` `environment` `snapshot` `gvisor`

---

## License

This export is provided as-is for educational and research purposes.
