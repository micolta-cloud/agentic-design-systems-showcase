# ComponentName

**Figma source:** [Figma Node Link](https://www.figma.com/design/...)
**Node:** `0:0`

### 1. Title and Description

# ComponentName

High-level summary of the component and its role within the design system.

---

### 1b. Variants & Component Parameters

| Variant | Type | Values | Default | Visible when |
|---|---|---|---|---|
| `variantName` | VARIANT | `Value 1` · `Value 2` | `Value 1` | always |

---

### 1c. AI Usage Guidance & Anti-Patterns

#### Primary Use Cases
- Scenario 1 where this component should be selected.
- Scenario 2 where this component should be selected.

#### Anti-Patterns (What NOT to do)
| Scenario | Why it's wrong | Alternative |
|---|---|---|
| Incorrect usage pattern | Breaks design system hierarchy | Recommended alternative pattern |

#### AI Selection Hints
- **Priority**: `high` | `medium` | `low`
- **Keywords**: `keyword1`, `keyword2`
- **Context**: When to choose this component over similar components.

---

### 2. Visual Design & Design Tokens

#### Typography (Tokens Only)
- **Role Label:** `sys.typescale.label-medium` (`FontFamily` / Size: 14dp / Weight: 500 / `font-variation-settings`)

#### Colors (Design Tokens Only)
| Component Role | Design Token | Token Variable | Applied CSS Rule |
|---|---|---|---|
| Role Name | `sys.color.token-name` | `var(--sys-token-var)` | `background-color` / `color` |

#### Layout & Spacing Architecture (Bound to `spacing.json` Tokens)
| Layout Property | Spacing Token | CSS Token Variable | Token Value | Applied Geometry Rule |
|---|---|---|---|---|
| Corner Radius | `spacing.16` | `var(--spacing-16)` | `16px` | Applied geometry rule |

---

### 2b. Nested Component Composition Tree

#### Nested Sub-Component: `SubComponentName`
- **Base Component Atom Spec**: [`.base/AtomName.md`](.base/AtomName.md)
- **Role**: Purpose within parent component.
- **Properties**: `selected` (`true`/`false`), `state` (`hover`, `pressed`).
- **Geometry**: Radius `var(--spacing-6)` inner, `var(--spacing-16)` outer.
- **Token Bindings**: `var(--sys-surface-container)` fill.

---

### 3. Behavior & States

- **Interactive Rules**: Hover, focus, pressed, and selected behaviors.
- **State Transitions**: Geometry or color morphing rules.

---

### 4. Motion & Accessibility

- **Motion**: Durations and easing curves.
- **Accessibility**: ARIA roles, keyboard focus management.

---

### 8. Metadata

- **Figma Source**: [Figma Node Link](https://www.figma.com/design/...)
- **Last Updated**: YYYY-MM-DD
