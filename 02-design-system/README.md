# Everyday Eats — Design system

The final design system of Everyday Eats, a mobile food and nutrition app. It reads like a modern cookbook: warm cream paper, near-black ink, terracotta for action and a softened herb green as an accent. One typeface, a 4px spacing grid, flat surfaces with hairline outlines, and one component for each interaction.

![Foundations](sheets/00-foundations.png)

## Contents

| File | What it is |
| --- | --- |
| `everyday-eats-design-system.pdf` | The whole system in one PDF (9 pages, bookmarked): foundations, then the eight component sheets |
| `tokens.json` | Design tokens v3.0 in the W3C Design Tokens format: the source of truth for every value |
| `docs/style-guide.md` | Visual foundation and style guide: brand, colour, typography, spacing, radii, borders, elevation, layout, imagery, icons, content rules, accessibility and app structure |
| `docs/components.md` | Every component: anatomy, sizes, states, behaviour and where it is used |
| `sheets/00-foundations.png` | Colour, typography, spacing, radius, borders, focus, elevation, sizes and motion, read from `tokens.json` |
| `sheets/01-buttons-and-actions.png` | Primary and outlined buttons, save control, text link, bookmark button, Home action row |
| `sheets/02-fields.png` | Search field, text field, amount field, settings fields, option rows |
| `sheets/03-chips-and-tags.png` | Filter chips, single-choice chips and tags |
| `sheets/04-icons.png` | The icon set, fill weight and icon colour |
| `sheets/05-content.png` | Recipe cards, search match, featured card, Today's pick, option cards, section headers, list rows and empty states |
| `sheets/06-nutrition.png` | The nutrition summary panel, macro colours and loading |
| `sheets/07-navigation.png` | Top bar, tab bar and sticky action bar |
| `sheets/08-feedback-and-overlays.png` | Snackbars, bottom sheet, info note, errors and loading |

The sheets are 2× PNGs; the PDF has vector text.

## Principles

1. **Food first, numbers second.** The dish is the hero; nutrition is the precise caption.
2. **Inform, don't judge.** No red/green verdicts on food, no shaming language.
3. **Fastest path to an answer.** Every flow reaches a useful result in as few steps as possible.
4. **Calm over clever.** One clear focus per screen.
5. **Warm, but restrained.** Colour and texture are used sparingly so they stay special. Nothing is decorative.

## Foundations at a glance

**Colour — "Clean warm".** About 85% of a screen is neutral, 10% terracotta, 5% everything else.

| Neutral | Hex | | Accent | Hex |
| --- | --- | --- | --- | --- |
| Cream | `#FAF6EF` | | Terracotta 500 | `#CA3E1C` |
| Card | `#FFFCF7` | | Terracotta 50 | `#FDEAE2` |
| Oat | `#F3EEE7` | | Terracotta 700 | `#8C2E16` |
| Hairline | `#E7E0D6` | | Herb 50 | `#E9F2DE` |
| Stone | `#8C817A` | | Herb 500 | `#4C7A33` |
| Walnut | `#675D57` | | Herb 700 | `#3A5E27` |
| Ink | `#221B17` | | | |

Nutrition colours are a separate, functional set that labels data only: Protein `#B23C6E` (Berry), Carbs `#3783AB` (Blue), Fat `#C78500` (Amber). Calorie values are always Ink.

**Typography.** Schibsted Grotesk only, weights 400, 500 and 600, for headings, body, interface and every number. Scale: Display 40, Heading 1 32, Heading 2 24, Heading 3 20, Title 17, Body large 17, Body 15, Body small 13, Label 15, Label small 13, Overline 12, Number XL 44, Number M 17. Numbers use tabular figures; units sit beside them in Walnut.

**Spacing.** 4px base, 8px rhythm: 4, 8, 12, 16, 20, 24, 32, 40, 48, 64. Screen margin 20px; recipe grid 8px from the edge and 8px apart.

**Shape and depth.** Radius 4 / 8 / 12 / 16 / 24 / full. 1px borders (Hairline, Stone, or Terracotta when selected). One focus style: a 2px Ink outline 2px outside the element. Two shadows: elevation 1 for bars and the bookmark over a photo, elevation 2 for sheets; snackbars stack both and add a Hairline edge, so they stand off the Cream page. No gradients.

**Icons.** Phosphor Regular at 16, 20 and 24px with the same visible 1.5px stroke; Fill weight only for active or selected states.

**Accessibility.** WCAG 2.2 AA. Text contrast at least 4.5:1, touch targets at least 44 × 44px, colour never the only signal, visible keyboard focus.

## Tokens

`tokens.json` has three tiers:

- **Primitives:** the raw palette (`color.neutral.*`, `color.terracotta.*`, `color.herb.*` …), `space.1`–`space.16`, `radius.*`, font weights.
- **Semantic tokens:** what a value is for (`color.text.secondary`, `color.surface.sunken`, `color.border.focus`, `color.nutrition.protein`, `space.stack.section` …). Screens use semantic or component tokens only.
- **Component tokens:** sizes and styles for each component (`component.button`, `component.card`, `component.empty-state`, `component.snackbar` …).

References use the `{group.token}` syntax, so a value is changed once at the primitive and flows through.

## Typeface

[Schibsted Grotesk](https://fonts.google.com/specimen/Schibsted+Grotesk), SIL Open Font License, via Google Fonts.
