# claude-sandbox-env

> 🇬🇧 [Read in English](README.md)

Полный снимок изолированной Linux-среды исполнения, которую использует Claude (Anthropic) при обработке запросов с функцией «computer use» / выполнения инструментов. Экспортировано из живого контейнера и опубликовано для справки, исследований и воспроизводимости.

---

## Что внутри

### Система
| Параметр | Значение |
|----------|----------|
| ОС | Ubuntu 24.04.4 LTS (Noble Numbat) |
| Ядро | Linux 4.4.0 (runsc / gVisor) |
| CPU | Intel Xeon Skylake-SP, 2 vCPU @ 2800 МГц, AVX-512 |
| ОЗУ | 9,0 ГБ всего, ~8,8 ГБ свободно |
| Корневой диск | 9,9 ГБ (занято 259 МБ) |
| Монтируемые разделы | `/mnt/user-data/uploads`, `/mnt/user-data/outputs`, `/mnt/transcripts` |

### Python-пакеты (`pip_packages.txt`)
Более 50 предустановленных библиотек, в том числе:
- **Данные / ML**: `pandas`, `numpy`, `scikit-learn`, `tensorflow`, `flatbuffers`
- **Работа с документами**: `python-docx`, `openpyxl`, `pypdf`, `camelot-py`, `img2pdf`, `markitdown`, `beautifulsoup4`, `lxml`
- **Изображения / Видео**: `Pillow`, `imageio`, `imageio-ffmpeg`
- **Веб / Сеть**: `Flask`, `requests`, `httplib2`, `cryptography`
- **Утилиты**: `click`, `Jinja2`, `magika`, `graphviz`, `grip`

### Node.js / npm-пакеты (`npm_packages.txt`)
- `playwright` — автоматизация браузера без графического интерфейса
- `pptxgenjs` — генерация PowerPoint-презентаций
- `@mermaid-js/mermaid-cli` — рендеринг диаграмм
- `react` + `react-dom` — рендеринг UI-компонентов
- `typescript`, `ts-node`, `tsx` — инструментарий TypeScript
- `docx`, `pdf-lib`, `pdfjs-dist` — работа с документами и PDF
- `marked`, `markdown-pdf`, `markdownlint-cli2` — инструменты Markdown
- `sharp` — высокопроизводительная обработка изображений

### Навыки (`/mnt/skills/`)
Навыки (Skills) — это структурированные наборы инструкций, которые сообщают Claude, как надёжно выполнять конкретные задачи.

**Публичные навыки** (`skills/public/`):
| Навык | Назначение |
|-------|-----------|
| `docx` | Создание и редактирование Word-документов через `python-docx` |
| `xlsx` | Создание и редактирование Excel-таблиц через `openpyxl` |
| `pptx` | Создание и редактирование PowerPoint-презентаций через `pptxgenjs` |
| `pdf` | Создание, объединение, разбиение, заполнение PDF через `pypdf` / `pdf-lib` |
| `pdf-reading` | Извлечение и анализ содержимого PDF |
| `file-reading` | Умный диспетчер — правильная стратегия чтения для каждого типа файлов |
| `frontend-design` | Создание красивых UI-компонентов (React, HTML/CSS, Tailwind) |
| `product-self-knowledge` | Актуальные факты о Claude и продуктах Anthropic |

**Примеры навыков** (`skills/examples/`):
`skill-creator`, `mcp-builder`, `canvas-design`, `algorithmic-art`, `slack-gif-creator`, `theme-factory`, `web-artifacts-builder`, `doc-coauthoring`, `internal-comms`, `event-planning`, `meal-delivery`, `grocery-shopping`, `return-refund`, `cancel-unsubscribe`, `hire-help`, `prescription-refill`, `file-expenses`, `benepass-reimbursement`, `financial-calculator`, `brand-guidelines`, `file-form`, `call-to-book`

### Переменные окружения (`env_vars.txt`)
Ключевые переменные: `HOME=/root`, `PATH` включает `/home/claude/.npm-global/bin`, стандартные пути Ubuntu. Никаких пользовательских секретов нет.

### Снимок процессов (`processes.txt`)
На момент экспорта в контейнере работал один основной процесс-супервизор (`process_api`) и Python-скрипт, генерировавший сам экспорт.

### Дерево файлов (`full_file_tree.txt`)
Полный рекурсивный список всех файлов, доступных в контейнере на момент экспорта (~16 МБ в несжатом виде).

---

## Лицензия

Этот экспорт предоставляется как есть для образовательных и исследовательских целей.

