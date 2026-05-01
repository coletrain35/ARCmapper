# ARC Mapper
### *Alignment, Responsibility, & Clarity*

A single-file process mapping tool for documenting workflows, assigning ownership, and visualizing how work actually moves through a team — no setup, no server, no account required.

---

## What it does

ARC Mapper lets you build living process documents that go beyond a simple flowchart. Each document combines four views of the same process:

| Tab | What you get |
|---|---|
| **Document** | Step-by-step editor with descriptions, owners, durations, tags, and risks |
| **Flowchart** | Interactive visual canvas — nodes, branches, swimlanes |
| **Ownership** | Per-owner perspective lens and threaded journey view |
| **RACI** | Contextual timeline showing who is Responsible, Accountable, Consulted, and Informed at every step |

---

## Getting started

No install needed. Just open the file:

```bash
# Windows
start process-mapping-v8.html

# macOS / Linux
open process-mapping-v8.html
```

Or serve locally if you prefer:

```bash
python -m http.server 8000
# then visit http://localhost:8000/process-mapping-v8.html
```

Your documents auto-save to your browser's `localStorage`. Nothing leaves your machine.

---

## Step types

| Type | Shape | When to use |
|---|---|---|
| **Start / End** | Pill | Entry and exit points of the process |
| **Task** | Rectangle | A concrete action performed by a person or system |
| **Decision** | Diamond | A branching point — supports up to 5 named paths |
| **Handoff** | Rectangle with divider | Responsibility transfers to a different owner |
| **Subprocess** | Rectangle with accent | A step that links out to another saved process document |

---

## Key features

### Editor
- Rich description field with a formatting toolbar (bold, italic, lists, blockquotes, inline code)
- Markdown-style shortcuts (`**bold**`, `- bullet`, etc.) and keyboard shortcuts (`Ctrl+B`, `Ctrl+I`)
- Per-step risk tracking with severity levels (High / Medium / Low) and mitigations
- Tags for filtering and categorization
- Compact and detail view modes

### Branching
- Decision steps support **1–5 named branches**, each with its own label and target
- Branch paths are shown in a tabbed interface with color-coded step counts
- Add steps directly inside a branch tab without losing context
- Nested decisions (decisions within branch paths) are fully supported

### Flowchart
- **Top-to-Bottom** layout with orthogonal connectors and branch labels
- **Swimlane** layout organized by step owner, with horizontal scroll
- Hover any node to trace its connections — incoming and outgoing edges highlight, everything else dims
- Click any node to open a detail panel (description, RACI assignments, risks)
- Zoom controls and drag-to-pan canvas
- Heat map overlay to surface high-risk steps at a glance

### Ownership views
- **Perspective Lens** — filter the entire process from one owner's point of view, with context cards showing handoffs in and out
- **Threaded Journey** — all owners shown simultaneously as parallel vertical threads

### RACI
- Assign R / A / C / I roles to any owner at any step via dropdown
- Inline editing directly on the timeline cards

---

## Exporting

From the toolbar in any view:

| Export | Format | Notes |
|---|---|---|
| **Document** | `.html` | Standalone file; can be re-imported |
| **Flowchart SVG** | `.svg` | Raw vector file |
| **Flowchart PDF** | Print dialog | Landscape, print-optimized |
| **Interactive HTML** | `.html` | Clickable flowchart — nodes open modals with full step details, keyboard nav |
| **RACI Matrix** | Print dialog | Printable grid of all owners vs. all steps |

---

## Document management

- **My Documents** panel lists all saved processes sorted by last modified
- Create, duplicate, rename, and delete documents from the sidebar
- Import a previously exported `.html` document to restore it
- Command palette (`Ctrl+K`) for quick navigation between documents and actions

---

## Data & privacy

All data is stored in your browser's `localStorage` under the key prefix `pm-doc-*`. Nothing is sent to any server. Clearing your browser storage will erase your documents — export regularly if you want backups.

---

## File structure

```
process-mapping-v8.html       # The app — open this
```

---

## Tech notes

- Pure vanilla HTML, CSS, and JavaScript — zero dependencies, zero build step
- Rendering: `innerHTML`-based DOM manipulation, no virtual DOM
- State: global `steps[]`, `risks[]`, `raciData{}` objects, persisted via `localStorage`
- Fonts: Nunito (UI), Montserrat (header title), Caveat (header subtitle) via Google Fonts CDN
