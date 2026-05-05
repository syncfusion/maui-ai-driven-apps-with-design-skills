# MAUI Token Architecture

Use a three-layer token system in ResourceDictionary files.

## Layer Model

1. Primitive tokens: raw values (color ramp, spacing values, radius, font sizes)
2. Semantic tokens: meaning-based aliases (Action/Primary, Text/Muted, Surface/Card)
3. Component tokens: per-component bindings (KpiCard.Background, Grid.Header.Text)

## Suggested File Split

- Resources/Styles/Tokens.Primitive.xaml
- Resources/Styles/Tokens.Semantic.xaml
- Resources/Styles/Tokens.Component.xaml
- Resources/Styles/Theme.Light.xaml
- Resources/Styles/Theme.Dark.xaml

## Primitive Scales

### Color Ramp (example)

- Blue 100..900
- Gray 50..900
- Green 500 (success)
- Amber 500 (warning)
- Red 500 (danger)

### Spacing Scale

- Space.0 = 0
- Space.1 = 4
- Space.2 = 8
- Space.3 = 12
- Space.4 = 16
- Space.5 = 20
- Space.6 = 24
- Space.8 = 32

### Typography Scale

- Font.Size.XS = 12
- Font.Size.SM = 14
- Font.Size.MD = 16
- Font.Size.LG = 20
- Font.Size.XL = 24
- Font.Weight.Regular = 400
- Font.Weight.SemiBold = 600
- Font.Weight.Bold = 700

## Example XAML

```xaml
<ResourceDictionary>
    <!-- Primitive -->
    <Color x:Key="Color.Blue.600">#2563EB</Color>
    <x:Double x:Key="Space.4">16</x:Double>

    <!-- Semantic -->
    <Color x:Key="Color.Action.Primary">{StaticResource Color.Blue.600}</Color>
    <Color x:Key="Color.Text.Primary">#111827</Color>

    <!-- Component -->
    <Color x:Key="KpiCard.Background">{StaticResource Color.Surface.Card}</Color>
    <Color x:Key="KpiCard.Value.Foreground">{StaticResource Color.Text.Primary}</Color>
</ResourceDictionary>
```

## Theme Strategy

- Keep primitive layer mostly stable across themes
- Switch semantic mappings in light vs dark dictionaries
- Leave component tokens unchanged where possible
- Resolve theme differences through semantic aliases only
