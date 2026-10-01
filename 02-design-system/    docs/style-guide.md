# Everyday Eats — Visual Foundation & Style Guide

Version 3 · updated 1 Oct 2026 · replaces version 2 (29 Sep 2026)

This guide is the single source of truth for the visual foundation. The final high-fidelity screens are the reference for how it is applied; [components.md](components.md) describes every component and [tokens.json](../tokens.json) holds the values. If a later decision contradicts this guide, update the guide first, then the screens.

---

## 1. Brand

**What it is.** A calm kitchen companion with two jobs: tell me what's in this dish or product, and help me find something good to cook. It looks and reads like a modern cookbook: warm cream paper, near-black ink, terracotta for action, and a softened herb green as an accent.

**Personality.** A friend who cooks well and knows nutrition: knowledgeable, warm, honest, unfussy, grown-up.

| Everyday Eats is | Everyday Eats is not |
|---|---|
| Warm, generous, editorial | Rustic, farmhouse, overly earthy |
| Calm, precise, trustworthy | Clinical, medical, preachy |
| Curious about flavour | Focused on restriction or "good vs bad" food |
| Plain-spoken and practical | Techy, jargon-heavy, "AI-powered" |
| Restrained and considered | Cute, bubbly or trend-chasing |

**Voice.** Short sentences, everyday words. No exclamation marks in system messages, no emoji in UI copy. Numbers are stated as facts, never as warnings.

- Say: "412 kcal per serving." Not: "Warning: high calorie meal!"
- Say: "No saved recipes match 'stew'. Try a simpler name." Not: "Error: no results found."
- Cut any copy that repeats what the UI already says. A helper line earns its place only if it adds information the label doesn't (for example "Optional", or the reason a button is disabled).

**What the app is not.** No food logging, daily totals, calorie budgets, diary, streaks, social features or profile photo. Saving keeps a recipe or a dish to come back to; it never counts towards anything.

**Design principles**

1. **Food first, numbers second.** The dish is the hero; nutrition is the precise caption.
2. **Inform, don't judge.** No red/green verdicts on food, no shaming language.
3. **Fastest path to an answer.** Every flow reaches a useful result in as few steps as possible.
4. **Calm over clever.** One clear focus per screen.
5. **Warm, but restrained.** Colour and texture are used sparingly so they stay special. Nothing is decorative: an icon, chip or colour must carry meaning.

---

## 2. Colour

Palette: "Clean warm". Warm cream, ink, terracotta, herb and honey tones, with the brown-grey cast taken out of the accents and neutrals so they read clean rather than muddy. Restrained: roughly 85% of a screen is neutral, 10% terracotta, 5% everything else.

**Semantic use (one colour, one purpose):** Terracotta 500 = actions, links, active tab, selected and saved states, and the two group labels on nutrition search · Terracotta 50/700 = selected chip, Saved state of the save control, cooking-style tag · Herb 50/700 = diet tags · Oat = sunken surfaces, placeholders, disabled buttons, empty-state circle · Card = raised surfaces: sheets, snackbars, inputs, bars, panels · Hairline = outlines and dividers · Stone = input/outlined-button/radio borders, placeholder text and icons · Walnut = secondary text · Ink = primary text, numbers and the focus outline · Berry/Blue/Amber = protein/carbs/fat data only.

### Neutrals

| Token | Hex | Use | Contrast on Cream |
|---|---|---|---|
| Cream | `#FAF6EF` | Page background; recipe cards and option cards sit directly on it | — |
| Card | `#FFFCF7` | Raised surfaces: tab bar, action bar, sheets, inputs, nutrition panel, bookmark circle | — |
| Oat | `#F3EEE7` | Sunken surfaces: search field, info note, photo placeholders, disabled button, empty-state icon circle, Home action-row icon circle | — |
| Hairline | `#E7E0D6` | Card outlines, dividers, filter chip borders, top bar and tab bar edges | 1.3:1 |
| Stone | `#8C817A` | Input and outlined-button borders, radio rings, placeholder text and icons, disabled text | 3.5:1 |
| Walnut | `#675D57` | Secondary text, units, inactive tab, list carets | 5.9:1 |
| Ink | `#221B17` | Primary text, headings, all numbers, primary icons, focus outline | 15.8:1 |

### Brand

| Token | Hex | Use |
|---|---|---|
| Terracotta 50 | `#FDEAE2` | Selected chip fill, Saved state of the save control, cooking-style tag ("One pot") |
| Terracotta 100 | `#F9CDBC` | Reserved |
| Terracotta 500 | `#CA3E1C` | Primary buttons, text links, active tab, selected chip border, saved bookmark, selected radio, Home action-row arrow. 4.6:1 on Cream, white text on it 5.0:1. Do not make it brighter or more saturated. |
| Terracotta 600 | `#AE3417` | Hover (desktop only, reserved) |
| Terracotta 700 | `#8C2E16` | Pressed; text on Terracotta 50 |
| Herb 50 | `#E9F2DE` | Diet tags |
| Herb 500 | `#4C7A33` | Reserved accent; not used for icons |
| Herb 700 | `#3A5E27` | Text on Herb 50 |

### Nutrition data

Macro colours label data; they never signal good or bad. They appear only as dots and bar segments on Card surfaces. Values are always Ink.

| Macro | Fill | Tint |
|---|---|---|
| Protein (Berry) | `#B23C6E` | `#F8E6EE` |
| Carbs (Blue) | `#3783AB` | `#E4F0F6` |
| Fat (Amber) | `#C78500` | `#FCF0CC` |
| Calories | Ink | — |

Nutrition colours are a separate set from the brand palette: clean and distinct from each other so the macro bar reads at a glance, while the brand accents stay restrained. Contrast on Card: Berry 5.5:1, Blue 4.1:1, Amber 3.0:1. Amber is exactly at the graphics minimum, so it never carries text and must not get lighter. Berry is kept towards plum so it is never mistaken for error red.

### Feedback

| Role | Hex | Tint | Use |
|---|---|---|---|
| Error | `#A12C3B` | `#F8E6E8` | Failed actions and invalid input only, always with an icon and message |
| Warning | `#8A5A12` | `#F7EDD9` | Reserved. The tint (Ochre 50) is also the search-match highlight |
| Success | `#3A5E27` | `#E9F2DE` | Reserved |
| Info | Ink | Oat | Neutral notes |

### Colour rules

- **Terracotta means "act" or "this is on".** Primary actions, links, the active tab, selected and saved states. One exception: the "Dishes" and "Packaged products" labels on nutrition search, so the two result groups don't blend into the rows. Never decorative: the empty-state icon sits on Oat, and the bookmark over a photo is a Card circle, not a terracotta fill.
- **Error red is reserved for errors.** Nothing else on any screen may use it or a strong red that could be read as an error.
- **One terracotta primary button per screen.** Secondary actions are outlined or text-only.
- **Herb is an accent, not a second primary.** No herb buttons or large herb surfaces.
- **Snackbars are neutral**, whether something was saved or removed: a Card fill with a 1px Hairline edge and a clearer shadow (elevation.1 + elevation.2), so they stand off the Cream page and off cards. Message and bookmark stay Ink; only Undo is Terracotta 500, so that is what draws the eye. Never a terracotta snackbar. Messages: "Saved to Saved recipes", "Removed from Saved recipes", "Saved to My dishes", "Removed from My dishes".
- Never colour a food, dish or calorie value red, green or amber to imply a judgement.
- All numbers are Ink. Colour sits beside a number (dot, bar), never on it.
- No gradients. Photography brings the richness; the UI stays flat.
- Dark mode is out of scope for v1.

---

## 3. Typography

One typeface: **Schibsted Grotesk** (Google Fonts, weights 400, 500 and 600) for headings, body, interface and every number. It is a warm, editorial grotesque with enough character for titles and the clarity numbers need. Hierarchy comes from size, weight and tracking, never from a second family.

| Style | Size / line | Weight | Tracking | Use |
|---|---|---|---|---|
| Display | 40 / 44 | 400 | −0.02em | Reserved (onboarding is out of v1) |
| Heading 1 | 32 / 38 | 500 | −0.015em | Screen titles (including "Everyday Eats" on Home), recipe name on detail |
| Heading 2 | 24 / 30 | 500 | −0.01em | Section titles, featured card title, "Ingredients" and "What's in it" |
| Heading 3 | 20 / 26 | 500 | 0 | Option card and sheet titles, the empty-state title when nothing is saved yet, recipe name in Today's pick |
| Card title (component) | 18 / 24 | 500 | 0 | Recipe card titles in the two-column grid (`component.card.title`) |
| Title | 17 / 24 | 600 | 0 | Home action-row titles, the empty-state title for no results and the empty builder |
| Body large | 17 / 26 | 400 | 0 | Home tagline (Walnut), recipe description |
| Body | 15 / 22 | 400 | 0 | Default text, list rows |
| Body small | 13 / 18 | 400 | 0 | Metadata, helper text, kcal line on cards |
| Label | 15 / 20 | 500 | 0 | Buttons, links, field labels; snackbar message at 600 |
| Label small | 13 / 16 | 500 | 0 | Chips, tags, tab labels (600 when active) |
| Overline | 12 / 16 | 600 | 0.06em, uppercase | Category above a recipe title ("Dinner · 30 min"), section labels ("Start checking", "Saved", "App", "Account"), in Walnut. On nutrition search, the group labels "Dishes" and "Packaged products" are Terracotta 500 so the two groups stand out. Never on a result itself: the dish name comes first. |
| Number XL | 44 / 48 | 600 | −0.02em, tabular | Hero calorie value |
| Number M | 17 / 24 | 600 | tabular | Macro values |
| Number S | 13 / 16 | 500 | tabular | Values in chips and compact labels |
| Unit | 13 / 16 | 500 | 0 | The unit beside a number ("18 **g**", "194 **kcal**"), Walnut (`typography.unit`). Its own 16px line box, so the number's line height holds: macro rows are 24px, list values 22px |
| List value (component) | 15 / 22 | 600 | tabular | Calories in breakdown rows, search results and My dishes (`component.list-row.value`) |
| Card calories (component) | 13 / 18 | 500 | tabular | The number in "412 kcal per serving" on recipe cards and Today's pick (`component.card.kcal`) |

**Rules**

- One family everywhere; only weights 400, 500 and 600.
- Headings balance their lines when they wrap (`text-wrap: balance`), so a long title never leaves one word on its own line.
- A heading beside a small label ("Ingredients" · "For 4 servings") aligns on the baseline; the row keeps the heading's line height.
- Numbers use tabular figures.
- Units sit next to numbers in Walnut at a smaller size: **412** kcal, **18** g.
- Minimum text size 12px; body text 15px or larger.
- Sentence case everywhere; uppercase only for Overline.
- Text colours: Ink for primary, Walnut for secondary, Stone only for placeholder and disabled text.

---

## 4. Spacing

4px base, 8px rhythm. No custom values outside the scale.

| Token | Value | Typical use |
|---|---|---|
| space.1 | 4 | Icon to label, gap between chips, overline to card title, bookmark target inset on cards |
| space.2 | 8 | Between tags, title to meta, tag to kcal line, recipe grid gap and outer inset, top bar side padding |
| space.3 | 12 | List row padding, card text padding, section header to its grid, between Home action rows |
| space.4 | 16 | Option card gap, empty-state circle to title, title to card content |
| space.5 | 20 | Screen side margin, option card padding |
| space.6 | 24 | Between content blocks inside a screen, empty-state text to its button |
| space.8 | 32 | Between sections |
| space.10 | 40 | Before a major section |
| space.12 | 48 | Before Home's Quick weeknight dinners |

Space grows with the level of grouping: tight inside a component, wider between components, widest between sections.

**Every spacing value is a multiple of 4** — padding, margins, gaps, offsets and component sizes (tab bar 84, top bar 56, buttons 52, fields 48, chips 36, tags 20, touch targets 44). No 2, 6, 10 or other off-grid values. The only exception is the device frame width itself (390). Borders (1px) and type metrics (line heights) are not spacing.

---

## 5. Radii, borders, elevation

**Radius:** xs 4 (tags, macro bar, search-match highlight) · sm 8 (chips) · md 12 (buttons, inputs, search field, snackbar) · lg 16 (recipe and option cards, action rows, nutrition panel, Today's pick photo) · xl 24 (sheet top corners) · full (bookmark circle, radios, empty-state circle, action-row icon circle).

A recipe card clips its image to its own radius: the image has no radius of its own and no padding around it.

**Borders**

| Token | Value | Use |
|---|---|---|
| border.subtle | 1px Hairline | Recipe cards (an inside stroke that takes no space), option cards, nutrition panel, list dividers, filter chips, top bar and tab bar edges |
| border.default | 1px Stone | Text inputs, outlined buttons, unselected radio ring |
| border.selected | 1px Terracotta 500 | Selected chip, Saved state of the save control |
| focus | 2px Ink outline, 2px outside the element | Keyboard focus, and the field being typed in |

Filter chips use the hairline because their text label identifies them; the 3:1 boundary rule applies to inputs, outlined buttons and radios. No other border styles exist.

**Focus.** One focus style everywhere, including the primary button: a 2px Ink outline drawn 2px outside the element's edge. It appears for keyboard focus (`:focus-visible`) and on a field while typing (search fields show it around the whole field); it never appears after tapping a button.

**Elevation**

| Token | Value | Use |
|---|---|---|
| elevation.0 | none + border.subtle | Cards and lists |
| elevation.1 | 0 2px 8px rgba(34,27,23,0.06) | Tab bar and action bar (cast upwards), bookmark circle over a photo |
| elevation.2 | 0 8px 24px rgba(34,27,23,0.10) | Bottom sheets |
| elevation.1 + elevation.2 | both shadows stacked | Snackbars, with a Hairline edge (`component.snackbar.shadow`) |

Scrim behind sheets: Ink at 40%.

---

## 6. Layout

- Mobile-first at 390px wide, single column, 20px side margins.
- **Two lines on every screen with recipe cards.** The box line, 8px from the screen edge, holds the recipe grid and the search field and filter chips above it, so whatever filters the cards lines up with them. The text line, 20px from the edge, holds titles, intro and count lines, section headers and the text inside each card (8px grid inset + 12px card padding).
- Recipe grids: 2 columns, 8px from the screen edge and 8px apart (183px cards on a 390px screen). The featured card spans the grid at the same 8px edge.
- Screens with a top bar start content 16–24px below it.
- The tab bar is 84px including the 24px home-indicator area; scrolling content keeps 104px of bottom padding.
- Screens use the standard 390 × 844 frame. Content that doesn't fit scrolls below the fold behind the tab bar. Only Find a recipe, Recipe detail and the custom dish result are drawn at full length, so every section shows.
- A screen's main action sits in the sticky action bar at the bottom (12px top padding, 32px bottom).
- Snackbars always float near the bottom of the screen, 16px above whatever is there: the tab bar (100px from the bottom), the action bar (112px), or the 24px safe area on Recipe detail (40px above the bottom of the drawn page, below the ingredients). Never over the main action.
- A screen's states (saved, removed, empty, filtered, adjusted, sheet open, editing) are states of that one screen, never separate screens.
- Touch targets are at least 44 × 44px, even when the visible element is smaller.
- **Empty states** are centred in the content area between the 56px top bar and the 84px tab bar, not the whole phone screen. The empty builder is the exception: it sits in the builder's flow.

---

## 7. Imagery and icons

**Photography:** natural light, real food, calm composition; warm-neutral grading; plain light surfaces; the dish plus at most 2–3 props. Avoid measuring tapes, scales, before/after bodies, glossy 3D food and visibly AI-generated images. Photos never have UI baked into them; the only control over a photo is the bookmark on Recipe detail and on cards, a small Card circle that stays secondary to the food.

**Crops**

| Ratio | Use |
|---|---|
| 4:3, radius 16 | Today's pick on Home, 160 × 120 beside its text |
| 4:5 crop, shown full width at 390 × 320 | Recipe hero under the top bar: clearly larger than Today's pick, but the title, meta, nutrition summary and the start of the ingredients come into view soon |
| 3:2 | Recipe and editorial cards, including the featured card |
| 1:1 | Reserved for ingredient and product thumbnails |

**Missing photo:** an Oat tile at the image's ratio with one 48px Stone Dish icon centred in it. Never a broken-image icon.

**Icons**

- Phosphor, Regular weight, round caps and joins. Every icon has the same visible 1.5px stroke at every size (on the 256 grid: 16 at 24px, 19.2 at 20px, 24 at 16px). Fill weight only for selected or active states (saved bookmark, active tab, selected radio).
- Sizes: 16, 20, 24. Two exceptions: the check inside a selected chip is 12px, and the photo placeholder's Dish icon is 48px.
- Icon colour follows text colour: Ink by default, Walnut secondary, Stone for placeholders, Terracotta 500 only when active or selected.
- Each icon has one meaning: X clears a search field (16px, in a 28px Hairline circle; the browser's own clear button is hidden, so a field never shows two) or closes a sheet (20px, no circle), Trash removes an ingredient, the filled bookmark removes something saved.
- Use an icon only where it communicates an action or state (search, back, bookmark, remove, add, clear, open). No decorative icons, and no icon next to a text action whose label already explains it. One exception: Home's two action rows carry the 20px icon of the tab each job belongs to (Leaf, Book) in Ink on a 40px Oat circle, so the two jobs are recognisable at a glance.
- No sparkle, wand or robot icons.

---

## 8. Content rules

**Nutrition**

- Labels are always Calories, Protein, Carbs and Fat; units kcal and g.
- Every nutrition figure says what it's for, with the weight whenever the data has one: "per 100 g", "per serving (200 g)", "per bowl (241 g)", "for 2 bowls (482 g)". Lists lead with it ("Per bowl (241 g)", "Per 100 g · 500 g pot"). Recipes say "per serving", next to "Serves 4". Meta lines under a title keep the portion itself ("1 bowl · 241 g").
- A breakdown includes every ingredient in the dish, and its calories and weights add up to the totals.
- Macro grams agree with the calorie total (protein and carbs × 4, fat × 9).
- **Amounts are shown exactly as entered or calculated** ("1 bowl · 241 g"). No "about", "approximately" or estimated-value notes.
- Ingredients can be entered in the unit that suits them (g, ml, tsp, tbsp, cup, or pieces like "apple"). Each ingredient offers only units that have a defined nutrition conversion for it in the database, with grams always available. Rows show the chosen unit followed by grams: "1 apple · 182 g".
- An ingredient with no nutrition data is named and marked "No data", never counted as 0, with one line above the list saying which.
- Recipe and dish names use "and", never "&".

**Saving**

- A recipe is saved with its bookmark, on a card or on Recipe detail, and appears in Profile › Saved recipes.
- A dish, built or searched, is saved with the Save control on its result and appears in Profile › My dishes. A saved searched dish is never editable; only its portion can change. Edit dish exists only for dishes built with Build your own.
- Every save and removal is confirmed with a snackbar with Undo on the same screen.

**Tags**

This is an intentional rule, not a gap in the content:

- A tag appears only when it truly applies. Tags are never added to fill space.
- **Recipe cards: 0 or 1 tag.** The most useful one, listed first: diet first (Vegetarian, Vegan, Gluten-free), then cooking style (One pot).
- **No empty tag space.** A recipe with no relevant tag shows no chip and reserves no space.
- **Recipe detail: every applicable tag**, 8px apart.
- Every tag is the same component (radius xs, 20px tall, 8px side padding, Label small). Only its colour variant changes with the kind of tag: diet tags use Herb 50/700; cooking-style tags use Terracotta 50/700.

**Search results**

- Recipe search matches names and ingredients. Every occurrence of the term in the results is highlighted with an Ochre 50 background and a 1px underline, so the match never relies on colour alone.
- A recipe that matches by an ingredient names it under the title ("With lemon zest"), with the term highlighted, so every result says why it's there.

**Examples:** keep the visible recipes varied (meat, fish, vegetarian, vegan) so the app never looks diet-specific.

---

## 9. Accessibility

WCAG 2.2 AA on every screen.

- Text contrast at least 4.5:1 (3:1 at 24px and above). Inputs, outlined buttons and radios have boundaries of 3:1 or more.
- Colour is never the only signal: selected chips carry a check, the active tab uses the filled icon, a saved bookmark is filled, the Saved control says "Saved", errors carry an icon and message.
- Toggles (bookmark, save control, filter chips) use `aria-pressed`; single choices use `role="radio"`. Icon-only buttons have an accessible name that says what they do ("Save Roasted tomato and white bean stew", "Back to search results").
- Disabled buttons state why ("Add at least one ingredient to calculate nutrition") and point to that text with `aria-describedby`.
- Keyboard focus is always visible (section 5).
- Text scales to 200% without breaking layouts.
- Motion 150–250ms ease-out and respects reduce-motion. Snackbars stay 4 seconds and always offer Undo.
- Every image has alt text describing the dish.

---

## 10. App structure

Four tabs: **Home · Eat · Recipes · Profile**.

| Tab | Job |
|---|---|
| Home | Calm starting point: intro, Today's pick, the two main actions and a small recipe preview (section 11) |
| Eat | Check nutrition: search a dish or product, scan a packaged product's barcode, or build your own dish |
| Recipes | Find something to cook: search, filters, this week's pick, meal sections and collections |
| Profile | The user's own area: **Saved** (Saved recipes, My dishes) and **App** (Settings) |

- **Saved recipes:** saved recipe cards with search and a Breakfast / Lunch / Dinner filter; the filled bookmark removes a recipe, with Undo.
- **My dishes:** saved dishes, built or searched; each opens its own result, and the filled bookmark removes it, with Undo.
- **Settings:** units (Metric or Imperial) and energy (kcal or kJ), applied as soon as they're chosen, plus a read-only Account section (name and email).
- Every screen below a tab has the top bar with a back arrow that returns to where the user came from; the tab it belongs to stays active.

---

## 11. Home

Home is a calm starting point, not a second Eat or Recipes screen. Top to bottom:

1. **"Everyday Eats"** (Heading 1) and the tagline **"Understand what you eat. Enjoy what you make."** (Body large, Walnut). The intro starts 32px below the top of the screen.
2. **Today's pick**, 24px below the tagline: a compact editorial recommendation that never dominates the screen. An Overline label ("Today's pick"), then a row: a 4:3 photo at 160 × 120 (radius lg, no text on it) with the recipe name (Heading 3) and one meta line beside it, 16px apart. Meta line: "30 min · Serves 4 · 465 kcal per serving" (Body small, Walnut). The whole block is one link to that recipe's detail, with no button or arrow.
3. **Two main actions**, 32px below, as restrained action rows (transparent on Cream, hairline border, a 40px Oat circle with the tab's icon on the left, terracotta arrow on the right), full width and stacked, 12px apart:
   - Check nutrition (Leaf): "Search a dish or product, or build your own." Opens Check nutrition.
   - Find a recipe (Book): "Find recipes by meal, time or dietary preference." Opens recipe search; back returns to Home.
4. **Quick weeknight dinners**, 48px below the actions: a section header with "See all", which opens the Dinner collection (back returns to Home), and two recipe cards with real photos (gnocchi and pasta, so Today's pick isn't repeated). This section sits below the fold and scrolls into view.

Nothing else. The dish and packaged-product explanations belong in Check nutrition, not on Home.

---

## 12. Open decisions

- **Wordmark.** Not locked yet; Home sets "Everyday Eats" as a Heading 1.
- **Photos.** Several recipes still use the photo placeholder; real photos should follow the photography rules above.
- **Not designed yet:** the "suitable for me" preferences step.
- **Dark mode.** Out of scope for v1.

---

## Changes in version 3

| Area | Now |
|---|---|
| Typeface | One family, Schibsted Grotesk, for headings, body, UI and numbers. Sizes, weights and line heights unchanged |
| App structure | Home · Eat · Recipes · Profile. Saved recipes, My dishes and Settings live under Profile |
| Back navigation | A back arrow alone in a 44px target; its accessible name says where it goes |
| Saving recipes | The compact bookmark button on cards and on the Recipe detail photo |
| Saving dishes | The labelled save control on both dish results (Save / Saved) |
| Recipe cards | One frame with no nested padding: inside-stroke hairline, image to the card's edges, 12px text padding; 8px grid inset and gap |
| Empty states | One component, centred in the content area between the top bar and the tab bar, with a terracotta primary button; the empty builder sits in its flow |
| Focus | 2px Ink outline, 2px outside the element, keyboard only (and the field being typed in) |
| Icons | The same visible 1.5px stroke at every size |
| Snackbar messages | "Saved to Saved recipes", "Removed from Saved recipes", "Saved to My dishes", "Removed from My dishes" |
