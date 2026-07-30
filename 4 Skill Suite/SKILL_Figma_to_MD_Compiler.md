# Skill: Figma to MD Compiler (Tool-Agnostic Spec Generator)

## Purpose
Compiles extracted Figma node metadata, nested component trees, design token variables, and AI usage guidance into a pure, tool-agnostic Markdown component specification (`<Component>.md`).

---

## 1. Specification Section Schema

Every generated `<Component>.md` MUST contain the following sections:

### 1. Title and Description
- Title (`# <ComponentName>`)
- Figma Source Link & Node ID
- Brief high-level summary.

### 1b. Variants & Component Parameters
- Table of top-level variant properties (`segments`, `activeSegment`, `headlineType`, `secondaryRowType`).

### 1c. AI Usage Guidance & Anti-Patterns
- **Use Cases**: Clear scenarios when to select this component.
- **Anti-Patterns**: What NOT to do (e.g. "Do not wrap in artificial card containers", "Do not add drop shadows").
- **AI Selection Hints**: Keywords and contextual selection priority.

### 2. Visual Design & Token Binding
- **Typography Table**: Exact font family (`Google Sans Text` vs `Google Sans Flex`), font weights, and `fontVariationSettings` (`ROND: 100` if present).
- **Color Token Table**: Pure semantic token custom properties (`var(--sys-*)`). ZERO hardcoded HEX values inside component rules.
- **Layout & Geometry Table**: Bounds all padding, gaps, and corner radii to `spacing.json` tokens (`var(--spacing-4)` through `var(--spacing-40)`).

### 2b. Nested Component Composition Tree
- Detailed breakdown of sub-components (`Segment State`, `Badge Metric`, `Action Pill`, `Dismiss Button`).
- Sub-component variant properties, padding, per-corner radii, and token bindings.

### 3. Behavior & States
- Interactive state transitions (`hover`, `pressed`, `selected`, `disabled`).

### 4. Motion & Accessibility
- Easing curves, transition durations, ARIA roles, keyboard focus rules.

---

## 2. STRICT COMPILER RULES

1. **ZERO Hardcoded HEX / Values:** Component CSS and code blocks MUST use semantic token custom properties (`var(--sys-*)`, `var(--spacing-*)`) ONLY.
2. **Tool-Agnostic Markdown:** Omit UI dashboard harness controls or tool-specific code wrappers. Keep specs pure and portable across any AI model.
