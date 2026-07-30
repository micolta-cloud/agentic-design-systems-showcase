# Skill: Figma File Parser & Enterprise Dual-Node Inspector

## Purpose
Navigates enterprise Figma files, resolves **Master Core Component Nodes** (`COMPONENT_SET` under Admin/System pages) and **Component Variations Gallery Nodes** (Showcase/Product pages), builds a **Bottom-Up Component Dependency Tree**, and propagates specifications into composite parent components.

---

## 1. Enterprise Dual-Node Master + Variations Strategy

> **ENTERPRISE FIGMA ARCHITECTURE:** Large design systems often split components across two locations:
> 1. **Master Core Node (`COMPONENT_SET`):** Defines canonical tokens, layout engine, and base slot parameters (e.g. Node `36283:13592`).
> 2. **Variations Gallery Node (`FRAME` / `SECTION`):** Displays all real-world permutations (Radio, Checkbox, Avatar, Chevron, Switch, Inset Dividers) (e.g. Node `40052:3031`).

```text
Master Core Node (Admin Page)        +    Variations Gallery Node (Showcase Page)
Node 36283:13592                           Node 40052:3031
  ├── Core Tokens                            ├── Radio Button / Checkbox Leading
  ├── Slot Architecture                      ├── Chevron / Switch / Text Trailing
  └── Auths Property Definitions             └── Inset & Full Dividers
                  │                                     │
                  └──────────────────┬──────────────────┘
                                     ▼
                     Complete Component Package Spec
```

### Dual-Node Resolution Protocol:
1. **Master Node Inspection:** Read canonical structure, slot geometry, and token bindings from the master `COMPONENT_SET` node payload.
2. **Variations Gallery Inspection:** Scan product showcase frames to collect all real-world leading/trailing/divider variant options.
3. **Comprehensive Variant Union:** Merge master properties with showcase variations into Section 1b of `<Component>.md` and the properties panel of `<Component>_Preview.html`.

---

## 2. Bottom-Up Component Dependency Tree Strategy

```text
Level 0: Design System Tokens (Light, Dark, Spacing JSONs)
   │
   ▼
Level 1: Base Components (Atoms) in .base/
   ├── SwitchToggle.md  (Trailing switch atom)
   └── IconBase.md      (Leading avatar atom)
   │
   ▼
Level 2: Composite Components (Molecules & Organisms)
   └── ListItems.md     (Composes SwitchToggle + IconBase)
```
