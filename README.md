# 📚 Codex Deck — Interactive Cheat Sheets for HTML, CSS, JavaScript & Python

A self-contained learning toolkit that turns the MDN documentation (plus a full Python reference) into something you can **search, copy, run and track** — all from a single HTML file, with no build step and no server.

**636 reference entries · 61 sections · 4 languages · 3 live code runtimes**

---

## 📦 What's in this project

| File | What it is | Best for |
|---|---|---|
| `react-cheatsheet.html` | **Codex Deck** — the React build with progress tracking, animated visualizations and the code playground | Daily driver ✅ |
| `frontend-cheatsheet.html` | The original vanilla JS build — same content, lighter, fewer dependencies | Offline use, low-end devices |
| `javascript-cheatsheet.md` | JavaScript-only reference in Markdown (34 sections, basics → advanced) | Reading end-to-end, printing, GitHub |

All three are standalone. Nothing depends on anything else.

---

## 🚀 Getting started

**Just double-click the HTML file.** It opens in your browser and works immediately.

```
# or serve it locally if you prefer
python3 -m http.server 8000
# then open http://localhost:8000/react-cheatsheet.html
```

No `npm install`. No bundler. No API keys.

### Internet requirements

| Feature | Needs internet? |
|---|---|
| Cheat sheets, search, copy | Only for web fonts (works fine without — falls back to system fonts) |
| JavaScript playground | ❌ No |
| HTML + CSS live preview | ❌ No |
| Python playground | ✅ Yes, on first run (downloads the ~10 MB runtime once) |
| React build (`react-cheatsheet.html`) | ✅ Yes, loads React + Babel from CDN |

> 💡 If you'll be offline a lot, use `frontend-cheatsheet.html` — it only needs the network for Python.

---

## ✨ Features

### 📖 Reference
- **Four languages** in one interface — HTML, CSS, JavaScript, Python
- **Instant search** across syntax *and* descriptions, with matches highlighted inline
- **Collapsible sections** with expand-all / collapse-all
- **Click to copy** any snippet straight to your clipboard
- Crisp one-line explanations — no walls of text

### ▶️ Playground
A drawer at the bottom of the page with a live editor and output panel:

| Mode | What happens |
|---|---|
| **JavaScript** | Runs in the browser; `console.log` output and errors stream into the panel |
| **Python** | Runs real Python via [Pyodide](https://pyodide.org) — `print()`, tracebacks, and the standard library (`math`, `json`, `collections`…) |
| **HTML + CSS** | Renders live in a sandboxed preview pane |

- Press **Ctrl/Cmd + Enter** to run
- **Tab** inserts a proper 4-space indent
- Each mode keeps its own buffer — switching tabs never loses your code
- **`run` on any card** drops that snippet into the editor, ready to execute

### 📊 Progress tracking *(React build only)*
- Mark any entry **learned** → an animated ring fills in the sidebar
- Per-section progress bars and per-language completion percentages
- Saved to `localStorage`, so it survives closing the tab
- One-click reset

### 🎨 Interface
- Theme shifts with the language — orange (HTML), blue (CSS), yellow (JS), green (Python)
- Animated aurora backdrop, staggered card reveals, typewriter heading, spring accordions
- Fully responsive; card actions stay tappable on touch devices
- Keyboard accessible, with visible focus rings
- Respects `prefers-reduced-motion`

### ⌨️ Keyboard shortcuts

| Key | Action |
|---|---|
| `/` | Jump to search |
| `Esc` | Clear search, or close the playground |
| `Ctrl` / `Cmd` + `Enter` | Run code in the playground |
| `Tab` | Indent inside the editor |

---

## 📑 Content coverage

| Language | Sections | Entries | Covers |
|---|---:|---:|---|
| **HTML** | 10 | 124 | Document structure, text, links, media, lists, tables, forms & attributes, semantic layout, global attributes, entities |
| **CSS** | 15 | 171 | Selectors, pseudo-classes/elements, colors & units, box model, typography, backgrounds, positioning, flexbox, grid, transitions, animations, transforms, media queries, variables, functions |
| **JavaScript** | 21 | 188 | Variables, types, operators, control flow, functions, strings, arrays, objects, destructuring, scope, closures, `this`, classes, prototypes, errors, promises, async/await, fetch, DOM, events, storage, modules, Map/Set, generators, regex, dates |
| **Python** | 15 | 153 | Syntax, types, strings, lists, tuples, sets, dicts, control flow, functions, comprehensions, classes & OOP, exceptions, files, modules, generators, decorators |

---

## 🗺️ Suggested learning path

1. **Structure** → HTML sheet, sections 1–10
2. **Style** → CSS sheet; spend real time on the box model, flexbox and grid
3. **Logic** → JavaScript sheet, sections 1–13 (syntax) then 14–21 (closures, `this`, async)
4. **Python** → in parallel or after; the concepts transfer both ways

**Practice as you go.** Read a card → hit `run` → change a value → run again. Small projects to aim for: calculator → todo list → quiz app → weather app (fetch) → notes app (localStorage).

---

## 🛠️ Tech

| Build | Stack |
|---|---|
| `react-cheatsheet.html` | React 18 (UMD) · Babel Standalone for in-browser JSX · hand-written CSS · Pyodide |
| `frontend-cheatsheet.html` | Vanilla JavaScript · hand-written CSS · Pyodide |

**Architecture note:** the reference content lives in a single `DATA` object keyed by language, where each entry is a `[syntax, description]` pair. The UI is rendered entirely from that object — so adding a language or a section means editing data, not markup.

```js
// shape of the data
DATA.python.sections[0] = {
  t: "Basics & print",
  items: [
    ["print(\"Hello\")", "Print to the screen"],
    // …
  ]
};
```

### Extending it

**Add an entry** — drop a `[syntax, description]` pair into the relevant section's `items` array.

**Add a section** — append `{ t: "Section name", items: [...] }` to that language's `sections`.

**Add a language** — add a key to `DATA`, then in the React build add an entry to the `LANGS` array, a line to `LEDE`, and a `[data-lang="…"]` color block in the CSS. Everything else follows automatically.

---

## ⚠️ Known limitations

- Python needs a network connection on first run; the runtime is cached by the browser afterwards
- Pyodide runs in the browser sandbox — no file system access, no `pip install` of arbitrary packages
- The JavaScript playground shares the page's environment, so an infinite loop will freeze the tab (just reload)
- The React build compiles JSX at load time via Babel, which adds ~1s to first paint — fine for a learning tool, not what you'd ship to production
- Progress tracking is per-browser and per-device; it doesn't sync

---

## 📄 Credits & license

Reference content is distilled from the [MDN Web Docs](https://developer.mozilla.org/) (HTML, CSS, JavaScript) and the [official Python documentation](https://docs.python.org/3/). MDN content is available under [CC-BY-SA 2.5](https://creativecommons.org/licenses/by-sa/2.5/).

Python execution is powered by [Pyodide](https://pyodide.org/), which runs CPython compiled to WebAssembly.

Built as a personal learning tool — use it, fork it, extend it. 🚀
