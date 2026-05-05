# Common MAUI UI Patterns

Use these patterns as reusable building blocks in any .NET MAUI application.

## Navigation Patterns

1. Shell tabs: use for 3 to 5 top-level app areas.
2. Flyout + detail: use for content-heavy apps with many destinations.
3. Nested stack navigation: use for drill-down flows inside one section.
4. Modal pages: use for focused tasks (confirm, create, edit) and dismiss safely.

## Layout Patterns

1. List-detail (master-detail): list on the left and detail on the right for desktop/tablet; stacked for phone.
2. Card grid: use for dashboards, catalogs, and status overviews.
3. Form + summary: left side form and right side live summary on larger screens.
4. Empty/loading/error states: define all three for every data-driven screen.

## Form Patterns

1. Group related fields with section headers.
2. Show helper text and validation near each field.
3. Keep one clear primary action per form.
4. Use progressive disclosure for advanced fields.

## List and Search Patterns

1. Search bar + filter chips above the list.
2. Sticky filter or sort controls where long lists are expected.
3. Use item templates with clear hierarchy: title, subtitle, status, action.
4. Include pull-to-refresh (mobile) and explicit refresh action (desktop).

## Feedback Patterns

1. Inline validation for forms.
2. Toast/snackbar for low-priority messages.
3. Dialog for destructive actions or irreversible operations.
4. Busy indicators for async actions over 300ms.

## Accessibility Patterns

1. Minimum touch target: 44x44 dp.
2. Ensure semantic labels for icons and non-text controls.
3. Maintain visible focus states for keyboard users.
4. Do not rely on color only for status or error communication.

## Styling Rules

1. All spacing must map to spacing tokens.
2. All text styles must map to typography tokens.
3. Border radius and elevation should come from component tokens.
4. Keep state styles explicit: default, focused, pressed, disabled.
