# Skill: Visualizer Manifest Sync & Pure Component Generator

## Purpose
Scans `2 Component Spec Schema/` and updates `3 DS Manifest/ds.config.json`. Automatically generates pure component HTML files (`<Component>_Preview.html`) containing **ONLY THE PURE COMPONENT MARKUP ITSELF** without any artificial test panels, extra control bars, or extra wrapper UI.

---

## 1. Execution Protocol

1. **Manifest Sync:**
   - Read `3 DS Manifest/ds.config.json`.
   - Scan all `<Component>.md` files in `2 Component Spec Schema/`.
   - Update `components` map and `categories` list in `ds.config.json`.

2. **Pure Component Generation Rule (STRICT HYGIENE):**
   - For each component, parse variant properties and tokens from `<Component>.md`.
   - Generate a pure component HTML file (`<Component>_Preview.html`).
   - **STRICT RULE:** The HTML file must contain **ONLY THE PURE COMPONENT MARKUP ITSELF**.
   - Do NOT add artificial test panels, extra control dropdown boxes, or non-component wrapper containers.
