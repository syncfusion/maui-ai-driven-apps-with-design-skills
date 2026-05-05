# Adaptive Screen Variations

Define explicit screen variants so the same app feels native on phone, tablet, and desktop.

## Breakpoint Strategy

Use width-based layout states:

1. Compact: < 600 dp (phone portrait)
2. Medium: 600 to 1023 dp (tablet portrait, phone landscape)
3. Expanded: >= 1024 dp (tablet landscape, desktop)

## Recommended Variations

### Compact

1. Single-column layout.
2. Bottom navigation preferred.
3. Prioritize primary actions in thumb reach areas.

### Medium

1. Two-column sections where useful (cards/forms).
2. Keep primary navigation simple; avoid deep flyouts.
3. Show optional metadata that is hidden on compact.

### Expanded

1. Multi-column layout with persistent side navigation.
2. Show list-detail side by side.
3. Surface secondary panels (filters, summaries, inspectors).

## MAUI Implementation Guidance

1. Use `OnIdiom` for phone/tablet defaults.
2. Use `DeviceDisplay.MainDisplayInfo` to compute width-aware states.
3. Use `VisualStateManager` to switch layout properties per state.
4. Keep one view model and vary only presentation/layout where possible.

## Typical Property Variations

1. `Grid.ColumnDefinitions`: 1 column on compact, 2 to 3 on larger layouts.
2. `CollectionView` item span: 1 on compact, 2 to 4 on larger layouts.
3. `Margin` and `Padding`: reduced on compact, increased on expanded.
4. `FontSize`: keep readable but avoid oversized headings on compact.

## Validation Checklist

1. Every primary screen works at compact, medium, and expanded widths.
2. No clipped text or overlapping controls in landscape modes.
3. Navigation remains discoverable on all form factors.
4. Keyboard and mouse interactions are supported on desktop targets.
