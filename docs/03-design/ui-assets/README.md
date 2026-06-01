# UI Assets

> Icons, images, illustrations, dan aset visual lainnya.

## Folder Structure

```
ui-assets/
├── icons/          # SVG icons
├── images/         # Product images, banners
├── illustrations/  # Custom illustrations
├── logos/          # Brand logos (various formats)
└── animations/    # Lottie/JSON animations
```

## Naming Convention

- Icons: `icon-[name]-[size].svg` (e.g., `icon-search-24.svg`)
- Images: `img-[context]-[variant].webp` (e.g., `img-hero-desktop.webp`)
- Logos: `logo-[variant]-[color].svg` (e.g., `logo-full-dark.svg`)

## Export Guidelines

| Type | Format | Sizes |
|------|--------|-------|
| Icons | SVG | 16, 20, 24, 32 |
| Photos | WebP (fallback PNG) | 1x, 2x, 3x |
| Illustrations | SVG or PNG | As needed |
| Logos | SVG + PNG | Multiple sizes |
| Animations | Lottie JSON | As needed |

## Optimization

- SVGs: Run through SVGO
- Images: Compress with quality 80-85%
- Max file size: 200KB per asset
- Use lazy loading for below-the-fold images
