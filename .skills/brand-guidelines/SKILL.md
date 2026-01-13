---
name: brand-guidelines
description: Template brand identity - Customizable neutral theme for project template
---

# Template Brand Guidelines

## Brand Identity

**Product:** Project Template — Reusable project structure template
**Mood:** Neutral, professional, customizable
**Theme:** Placeholder/Customizable design tokens

## Color Palette

### Primary Colors (Customizable)
| Name | HEX | Usage | Note |
|------|-----|-------|------|
| primary-50 | #EFF6FF | Light backgrounds | Replace with brand |
| primary-100 | #DBEAFE | Hover backgrounds | Replace with brand |
| primary-500 | #3B82F6 | **Primary DEFAULT** | Replace with brand |
| primary-600 | #2563EB | Hover states | Replace with brand |
| primary-700 | #1D4ED8 | Active states | Replace with brand |

### Secondary Colors (Customizable)
| Name | HEX | Usage | Note |
|------|-----|-------|------|
| secondary-500 | #8B5CF6 | Secondary accent | Replace with brand |
| secondary-600 | #7C3AED | Secondary hover | Replace with brand |

### Semantic Colors (Standard)
| Name | HEX | Usage |
|------|-----|-------|
| success | #10B981 | Success states |
| warning | #F59E0B | Warnings |
| error | #EF4444 | Errors |
| info | #3B82F6 | Information |

### Neutral Colors (Standard)
| Name | HEX | Usage |
|------|-----|-------|
| gray-50 | #F9FAFB | Backgrounds |
| gray-100 | #F3F4F6 | Cards |
| gray-200 | #E5E7EB | Borders |
| gray-300 | #D1D5DB | Disabled |
| gray-400 | #9CA3AF | Placeholders |
| gray-500 | #6B7280 | Muted text |
| gray-600 | #4B5563 | Secondary text |
| gray-700 | #374151 | Primary text |
| gray-800 | #1F2937 | Headings |
| gray-900 | #111827 | Darkest |

## Typography

| Element | Font | Fallback | Note |
|---------|------|----------|------|
| Headings | System | sans-serif | Replace with brand font |
| Body | System | sans-serif | Replace with brand font |
| Code | System mono | monospace | Usually keep as-is |

## How to Customize

### 1. Replace Primary Colors
```css
/* Find and replace these values */
--primary-500: #YOUR_BRAND_COLOR;
--primary-600: /* darker shade */;
--primary-700: /* darkest shade */;
```

### 2. Update Typography
```css
/* Add your brand fonts */
--font-heading: 'Your Heading Font', sans-serif;
--font-body: 'Your Body Font', sans-serif;
```

### 3. Customize Border Radius
```css
/* Adjust for your brand feel */
--radius-sm: 0.25rem;  /* Sharp: 0, Rounded: 0.5rem */
--radius-md: 0.5rem;
--radius-lg: 1rem;
```

## Default Button Styles

| Type | Background | Text | Border |
|------|------------|------|--------|
| Primary | primary-500 | white | none |
| Secondary | gray-100 | gray-700 | gray-200 |
| Outline | transparent | primary-500 | primary-500 |
| Ghost | transparent | gray-600 | none |
| Success | success | white | none |
| Danger | error | white | none |

## Default Card Styles

```css
/* Standard card */
background: white;
border-radius: 0.5rem;
border: 1px solid #E5E7EB;
box-shadow: 0 1px 3px rgba(0,0,0,0.1);

/* Elevated card */
background: white;
border-radius: 0.75rem;
box-shadow: 0 4px 6px rgba(0,0,0,0.1);
```

## Usage Rules

1. **Customize everything marked "Replace"**
2. **Keep semantic colors standard** — Users expect green=success, red=error
3. **Test dark mode** — If supporting dark mode, test all custom colors
4. **Document your changes** — Update this file with your brand
5. **Use CSS variables** — Makes theming easier

## Checklist for Customization

- [ ] Replace primary color palette
- [ ] Replace secondary color palette (if needed)
- [ ] Add brand fonts
- [ ] Update border radius if needed
- [ ] Test all button states
- [ ] Test form inputs
- [ ] Verify contrast ratios (WCAG AA)
- [ ] Update this documentation
