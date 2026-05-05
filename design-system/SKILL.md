---
name: design-system
description: 'Generic design system workflow for .NET MAUI apps. Use for token architecture (primitive -> semantic -> component), ResourceDictionary styling, typography/spacing scales, common UI patterns, and adaptive mobile/desktop screen variations.'
argument-hint: '[component or token]'
user-invocable: true
---

# Design System

Design system workflow for reusable, consistent .NET MAUI applications across mobile and desktop.

## When to Use

- Design token definition for MAUI apps
- ResourceDictionary architecture
- Component state and variant rules
- Common screen structure and layout rhythm
- Mobile/desktop adaptive screen behavior
- Design-to-code handoff for XAML screens

## Token Architecture

Load: [references/token-architecture-maui.md](./references/token-architecture-maui.md)

### Three-Layer Structure

```
Primitive (raw values)
       ->
Semantic (purpose aliases)
       ->
Component (per-control tokens)
```

### Example Mapping (MAUI)

```xaml
<!-- Primitive -->
<Color x:Key="Color.Blue.600">#2563EB</Color>

<!-- Semantic -->
<Color x:Key="Color.Action.Primary">{StaticResource Color.Blue.600}</Color>

<!-- Component -->
<Color x:Key="PrimaryButton.Background">{StaticResource Color.Action.Primary}</Color>
```

## Quick Start

### 1) Create Token Dictionaries

- Start from [assets/design-tokens-starter.xaml](./assets/design-tokens-starter.xaml)
- Split into primitive, semantic, and component dictionaries as the app grows

### 2) Merge Dictionaries in App.xaml

Load token dictionaries in App resources and keep app-wide styles centralized.

### 3) Apply Shared Styles

- Define shared styles for common controls (Label, Button, Entry, Border, CollectionView templates)
- Use component tokens in these styles to avoid hardcoded values

### 4) Implement Adaptive Screens

Load: [references/adaptive-screen-variations.md](./references/adaptive-screen-variations.md)

## References

| Topic | File |
|------|------|
| MAUI Token Architecture | [references/token-architecture-maui.md](./references/token-architecture-maui.md) |
| Common MAUI UI Patterns | [references/common-ui-patterns-maui.md](./references/common-ui-patterns-maui.md) |
| Mobile/Desktop Variations | [references/adaptive-screen-variations.md](./references/adaptive-screen-variations.md) |

## Component Spec Pattern

Use this pattern for every component (buttons, cards, forms, lists, nav bars, dialogs):

| Property | Default | Hover/Focus | Active | Disabled |
|------|------|------|------|------|
| Background | Surface/Card | Surface/CardHover | Action/Primary | Surface/Muted |
| Text | Text/Primary | Text/Primary | Text/OnPrimary | Text/Muted |
| Border | Border/Subtle | Border/Strong | Action/Primary | Border/Subtle |
| Elevation | 1 | 2 | 1 | 0 |
| Radius | 12 | 12 | 12 | 12 |

## App Screen Contract

For most MAUI screens, target this structure:

1. Top region: app bar or page header (title + primary action)
2. Main content: list, cards, form, or content grid
3. Secondary content: filters, summaries, or supporting details
4. Bottom region: navigation or key actions where needed

## Cross-App Usage Rules

1. Always bind colors, fonts, spacing, and stroke widths through tokens
2. Avoid hardcoded styling values in XAML views and templates
3. Keep semantic color intent stable across all screens (success, warning, danger, info)
4. Map density to spacing tokens for compact and comfortable modes
5. Use one interaction language across controls (focus, pressed, selected, disabled)

## Validation Checklist

- No hardcoded hex in component XAML
- Font sizes come from typography scale tokens
- Spacing uses scale tokens (no arbitrary values)
- Reusable controls and templates inherit tokenized styles
- Light and dark themes resolve through semantic layer only
- Mobile and desktop layouts are both defined for critical screens

## Best Practices

1. Primitive tokens should be brand-agnostic enough to support future rebrands
2. Semantic tokens represent intent (success, warning, info), not color names
3. Component tokens isolate local UI changes without breaking global semantics
4. Lists, cards, forms, and dialogs should share consistent spacing and typography rhythm
5. Keep accessibility visible: contrast, hit targets, and keyboard focus states
