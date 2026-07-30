# Skill: Figma Metadata Extractor (Dependency Tree & Token Resolution)

## Purpose
Queries Figma API / MCP for individual `COMPONENT_SET` nodes, resolves bound variable IDs against local **Design System Token Files** (`Light.tokens.json`, `Dark.tokens.json`, `spacing.json`), and executes a **Bottom-Up Dependency Resolution Protocol** (Base Components $\rightarrow$ Composite Components).

---

## 1. Bottom-Up Dependency Resolution Protocol

```text
1. Extract Base Components (Atoms)    ---> Saved in 2 Component Spec Schema/.base/
2. Link Base Components to Parents   ---> Propagates properties, radii, and tokens
3. Compile Composite Components      ---> Clean 100% token-bound parent specs
```

### Execution Rules:
1. **Base Component Registration:**
   - When extracting an atom (e.g. `Icon Button`, `Segment State`), register its properties (`shape`, `size`, `corner-radius`, `fill-tokens`) in the manifest registry.
2. **Propagated Sub-Component Linking:**
   - When extracting a molecule/organism (e.g. `TimeNavigation`, `TimescaleNav`), link nested sub-component instances directly to their base component specs.

---

## 2. Automated Extraction Algorithms

1. **Spatial Bounding-Box Sorting (`x`, `y` coordinates):**
   - Sort child nodes by `absoluteBoundingBox.x` for horizontal layouts and `absoluteBoundingBox.y` for vertical layouts.
   - Guarantees visual 1:1 order (`left` $\rightarrow$ `right`, `top` $\rightarrow$ `bottom`) without raw z-stack array index bugs.

2. **Authoritative `componentPropertyDefinitions` Extraction:**
   - Query `componentPropertyDefinitions` payload sitting on `COMPONENT_SET` nodes to pull exact variant property keys (`Action`, `Timeframe`) and option lists (`Default`, `Inactive left`, `Inactive right`, `N/A`) directly from Figma.

3. **Per-Component Typography Isolation:**
   - Read `fontFamily` and `fontVariationSettings` per text node individually. Apply `'ROND' 100` ONLY to components whose text nodes explicitly define `ROND: 100` in Figma.
