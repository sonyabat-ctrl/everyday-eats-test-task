# Everyday Eats — Components

Version 3 · updated 1 Oct 2026

Every screen is built from these components, and the component sheets in [../sheets](../sheets) show each one with its states. The same interaction always uses the same component; don't create variants. Token names refer to [tokens.json](../tokens.json) and the [style guide](style-guide.md).

Contents: [Navigation](#navigation) · [Actions](#actions) · [Inputs and selection](#inputs-and-selection) · [Content](#content) · [Empty state](#empty-state) · [Nutrition](#nutrition) · [Feedback and overlays](#feedback-and-overlays) · [Icons](#icons) · [Where each component is used](#where-each-component-is-used)

---

## Navigation

### Top bar
Back navigation on every screen below a tab.

- 56px tall, Cream background, `border.subtle` along the bottom, 8px side padding.
- Left: the back arrow alone (20px ArrowLeft, Ink) in a 44px target. No text beside it: the previous screen is what the user just saw.
- Its accessible name says where it goes: "Back to search results", "Back to Profile", "Back to Check nutrition".
- No centred title. The screen title is a Heading 1 in the content, 16–24px below the bar. Nothing else goes in the bar.
- **Back follows where the user came from:**

| Screen | Back goes to |
|---|---|
| Recipe search | Home or Recipes, whichever opened it |
| Dinner collection | Home or Recipes |
| Recipe detail | Where it was opened: search results, the collection, Recipes, Home or Saved recipes; search results and the collection then lead back to Home or Recipes, whichever opened them |
| Saved recipes, My dishes, Settings | Profile |
| Nutrition search | Check nutrition |
| Dish result, product result | Search results, or My dishes when opened from there; a product opened by Scan barcode goes back to Check nutrition |
| Scan barcode | Check nutrition |
| Build a dish | Check nutrition |
| Custom dish result | Build a dish, or My dishes when opened from there |
| Edit dish | The saved dish it edits |

Each screen is designed once; only where its back arrow leads changes with the way it was opened.

### Bottom tab bar
Four tabs: **Home, Eat, Recipes, Profile**.

- 84px tall including 24px for the home indicator. Card background, `border.subtle` top edge, `elevation.1` cast upwards.
- Each tab: 24px icon (House, Leaf, BookOpen, User) over a Label small caption, 4px gap.
- Inactive: Regular icon, Walnut, weight 500. Active: Fill icon, Terracotta 500, weight 600, `aria-current="page"`.
- Screens under a tab keep it active: recipe search and the Dinner collection keep Recipes active even when opened from Home; Saved recipes, My dishes and Settings keep Profile active.

### Sticky action bar
Holds a screen's main action.

- Pinned to the bottom, Card background, `border.subtle` top edge, `elevation.1` upwards, padding 12 / 20 / 32.
- One primary button, or a pair at equal widths with a 12px gap: Adjust portion + Save (searched dish), Edit dish + Save (built dish), Cancel + Save changes (Edit dish).
- Optional hint line above the button (Body small, Walnut, centred), used only to explain a disabled state.

---

## Actions

### Primary button
- 52px tall, radius md, Terracotta 500 fill, white Label text (5.0:1).
- One per screen.
- **Disabled:** Oat fill, Stone text, `disabled`, with the reason in the action bar hint, linked by `aria-describedby`.
- Pressed: Terracotta 700. Loading keeps its size with a spinner and a present-tense label ("Saving…").
- Focus: the shared 2px Ink outline, 2px outside the button.

### Outlined button
- 52px tall, radius md, Card fill, 1px Stone border, Ink Label text.
- Secondary actions next to a primary ("Edit dish", "Adjust portion", "Cancel"), or the standalone "+ Add ingredient" (20px Plus icon).
- Pressed: Ink 10% overlay.

### Bookmark button
The compact save control and the only way to save a recipe.

- 44px tap target holding a 36px Card circle with a 20px bookmark.
- Not saved: outline (Regular) bookmark in Ink, `aria-pressed="false"`, label "Save {recipe}".
- Saved: Fill bookmark in Terracotta 500, `aria-pressed="true"`, label "Remove {recipe} from Saved recipes".
- **On recipe cards:** top right, the target 4px in, so the circle sits 8px from the card edges.
- **On Recipe detail:** top right of the photo, the target 8px in (the circle 12px in), with `elevation.1` on the circle so it reads over any image. No label and no terracotta fill: it stays secondary to the food.
- **In My dishes rows:** the filled bookmark in Terracotta 500 (no circle) removes the dish.
- Every tap shows the snackbar with Undo.

### Save control
The labelled save toggle for dishes: both dish results, in the action bar, paired with Adjust portion or Edit dish.

- **Not saved:** primary style with a 20px outline bookmark and "Save".
- **Saved:** the selected style (`component.button.selected`: Terracotta 50 fill, 1px Terracotta 500 border, Terracotta 700 text) with a 20px Fill bookmark and "Saved". The label and icon carry the state, so it never relies on colour alone.
- `aria-pressed`; each tap shows "Saved to My dishes" or "Removed from My dishes" with Undo.
- Saving a searched dish keeps it, at the portion shown, in Profile › My dishes. It never makes it editable: only its portion can change.

### Text link
- Label style, Terracotta 500, in a 44px tap area.
- "See all" carries a 16px caret after the label, except on Home, where it is plain text so "Quick weeknight dinners" fits on one line. Other text links have no icon ("Build your own", "Scan barcode").

### Spinner and skeleton
- Spinner: a quarter arc on a faint track, inside a control that keeps its size ("Saving…").
- Skeleton: Oat blocks in the content's own shape (the recipe card's frame, the nutrition panel). Never a full-screen spinner.

---

## Inputs and selection

### Search field
- 48px tall, radius md, Oat fill, no border. 20px search icon in Walnut, 12px gap, 15px text; placeholder in Stone.
- Once there's text, the clear button appears on the right: a 28px Hairline circle with a 16px X, in a 44px target. It is the only clear control: the browser's own search clear button is hidden.
- Focus: the 2px Ink outline around the whole field while typing.
- Never shows an error state; an empty result shows the empty state instead.
- Used on Find a recipe (opens recipe search), recipe search, Check nutrition (opens nutrition search), nutrition search, Saved recipes and the Add ingredient sheet.

### Text field
- Label above (Label style), field 48px, radius md, Card fill, 1px Stone border, 16px side padding.
- Helper text below only when it adds information ("Optional").
- Focus: the 2px Ink outline, 2px outside. Error: Error colour, an Info icon and a plain message ("Enter a number, like 250").

### Filter chip
- 36px tall inside a 44px tap area (the hit area extends 4px above and below), at least 44px wide, radius sm, Label small, 8px side padding, 4px between chips.
- Default: transparent, 1px Hairline border, Ink text.
- Selected: Terracotta 50 fill, 1px Terracotta 500 border, Terracotta 700 text and a **12px check** before the label, `aria-pressed="true"`.
- In a row, chips share the full width. The row scrolls sideways only when a selected chip needs more room. Labels are never shortened.
- Sets in use: Under 30 min / Vegetarian / Vegan / Gluten-free (Recipes, recipe search, the Dinner collection); Breakfast / Lunch / Dinner (Saved recipes).

### Single-choice chips
The same chip as a radio group (`role="radio"`), with the same selected style and 12px check.

- Units in the amount field (48px tall there, see Amount field); Per 100 g / Per serving (200 g) on a product result; Units (Metric (g, ml) / Imperial (oz, cups)) and Energy (kcal / kJ) in Settings, each group under a Label.
- Settings choices apply as soon as they're chosen; there is no save button.

### Amount field (amount + unit)
Used in the ingredient sheet and the Adjust portion sheet.

- Two labelled parts side by side, 16px apart, as one control family: "Amount", the number input (Text field style, `inputmode="decimal"`), which takes the rest of the row and is always the wider part, and "Unit", the unit chips at their natural width. The unit chips take the input's height (48px) and radius (12) and sit on the same line (`component.field.amount-unit-height`, `amount-gap`). The same layout in the ingredient sheet and both Adjust portion sheets.
- The units come from the ingredient, never a universal list. **Only units with a defined nutrition conversion for that ingredient are shown**, and grams is always available:
  - Weighed ingredients (blueberries): **g** · tbsp · cup. Grams is the default.
  - Counted ingredients (apple): **apple** · slice · g (1 apple = 182 g). The piece is the default.
  - Spoon measures (honey): tsp · tbsp · g.
  - Portions: **bowl** · g on a dish, **serving** · g on a product.
- Helper line (Body small, Walnut, linked by `aria-describedby`) shows what the calculation uses: "80 g · 48 kcal", "1 apple = 182 g · 95 kcal", "2 bowls = 482 g · 780 kcal".
- In lists and results the row keeps the unit the user chose, followed by grams when they differ: "1 apple · 182 g", "1 tsp · 7 g", "80 g".

### Option row (radio)
Matching ingredients in the Add ingredient sheet.

- Full-width row: name (Body; 600 when selected) and "per 100 g" (Body small, Walnut) on the left, kcal on the right, then the marker.
- Unselected marker: 20px ring, 1px Stone. Selected: 20px Fill check circle in Terracotta 500.
- Hairline divider between rows, none after the last. In Edit ingredient only the chosen match is shown.
- **Several options at once.** A search usually returns several matches, and an ingredient usually has several units. The sheet shows them all with exactly one of each selected: "blueberries" lists Blueberries, fresh (selected) · frozen · dried, with the units **g** · tbsp · cup; "apple" lists Apple, raw (selected) · dried · stewed, with **apple** · slice · g. Unselected matches keep the Stone ring and the Body weight; unselected unit chips keep the Hairline border with no fill and no check.

---

## Content

### Recipe card
Two-column grid card; the whole card opens the recipe.

- **One frame, no nested padding.** Transparent on Cream, radius lg, with the hairline as an inside stroke (outline, offset −1px) that takes no space.
- Image: 3:2, full card width, clipped by the card's top corners. No photo → photo placeholder.
- Text block, 12px padding on every side:
  1. Overline: "{Meal} · {n} min"
  2. Title: `component.card.title` (18/24, 500, balanced), 4px below the overline
  3. Bottom group, pushed to the bottom of the card, at least 12px below the title:
     - **Tag (optional, max one):** the recipe's first tag, 8px above the kcal line. No tag → nothing rendered, no reserved space.
     - **kcal line (always last):** "**412** kcal per serving": the number uses `component.card.kcal` (13/18 500, tabular, Ink), the words are Body small in Walnut.
- Bookmark button top right.
- Cards in a row stretch to equal height, so kcal lines always line up.
- **Grid:** two columns, 8px from the screen edge and 8px apart (`component.recipe-grid`), 183px wide on a 390px screen. Text inside a card lands on the 20px text line (8 + 12).
- **In search results:** every occurrence of the term in the title is highlighted (`component.search-match`: Ochre 50 background, 1px underline). A recipe that matches by an ingredient names it in Body small, Walnut, 4px under the title ("With **lemon** zest").

### Featured recipe card
The same card at the full grid width (374px, on the 8px edge) with a Heading 2 title. Used once ("This week's pick" on Find a recipe).

### Photo placeholder
Oat tile at the image's ratio with one 48px Dish icon in Stone, centred, `role="img"` and a label ("Photo to come: {dish}").

### Tag
One component everywhere (cards, Saved recipes, recipe detail): `component.tag` in the tokens.

- Radius xs, 20px tall (Label small at a 20px line height), 8px side padding, no vertical padding.
- Colour variants: diet (Vegetarian, Vegan, Gluten-free) Herb 50 / Herb 700; cooking style (One pot) Terracotta 50 / Terracotta 700.
- Static label, never a button.
- **Rule:** only when it applies, never to fill space. Recipe cards show 0 or 1 tag (the most useful); no tag means no chip and no empty space. Recipe detail shows every applicable tag, 8px apart.

### Today's pick
Home's focal point. Used only on Home.

- Overline "Today's pick", then 12px below a row: a 4:3 photo at 160 × 120 (radius lg, no text on it) and, 16px to its right and vertically centred, the recipe name in Heading 3 over one meta line (Body small, Walnut), 4px apart: time, servings and calories per serving. The calorie phrase never breaks across lines.
- The whole block is one link to the recipe's detail. No button, arrow or border, so it reads as inspiration.
- Always a recipe from the app's content, and never the same dish as the cards below it.

### Home action row
Home's two main actions. Used only on Home.

- Full width, stacked 12px apart. Transparent on Cream, 1px Hairline border, radius lg, 16px padding. The whole row is the link.
- Left: a 40px Oat circle with the 20px icon of the tab the job belongs to, in Ink (Leaf for Check nutrition, Book for Find a recipe).
- Then: Title (17/24 600, Ink) over one Body line in Walnut, 4px apart, 16px from the icon.
- Right: a 20px ArrowRight in Terracotta 500, the only colour in the row.
- Destinations: Check nutrition → Check nutrition. Find a recipe → recipe search (back to Home).

### Option card
Explains a type of check on Check nutrition.

- Transparent, 1px Hairline border, radius lg, 20px padding.
- Heading 3 title, Body description in Walnut, then at most one text link: "Build your own" on A dish, and "Scan barcode" on A packaged product. Both are plain text links, secondary shortcuts beside the main search; the cards have no icons.

### Section header
Heading 2 on the left, optional "See all ›" text link on the right. 32px above (48px before Home's Quick weeknight dinners), 12px to the content below.

- At least 16px between the title and "See all" (`component.section-header.gap`). A title that doesn't fit wraps (balanced) instead of crowding the link; "See all" never shrinks.
- A header with a small label on the right instead of a link ("Ingredients" · "For 4 servings", "Ingredients" · "5 ingredients") aligns the two on the baseline.

### List rows
All lists: Hairline divider between rows and **none after the last row**.

- **Breakdown row (nutrition results):** name (Body) over amount (Body small, Walnut); kcal on the right (`component.list-row.value`: 15/22 600, tabular; unit in Walnut, `typography.unit`). An ingredient with no nutrition data shows a "No data" label (Oat, Info icon) instead of kcal, never 0, with one line above the list saying which.
- **Link row:** the breakdown row as a whole-row link. Nutrition search results, grouped under the Dishes and Packaged products overlines, which are Terracotta 500 (not Walnut) so the two groups stand out from the rows. Each row starts with what its number is per: "Per bowl (241 g)" for a dish, "Per 100 g · 500 g pot" for a product.
- **Saved dish row (My dishes):** the link row, plus the filled bookmark on the right, which removes the dish with Undo.
- **Editable ingredient row (Build a dish):** tapping the row opens Edit ingredient; a 20px Trash button (44px target, Walnut, label "Remove {name}") removes it.
- **Recipe ingredient row (Recipe detail):** amount (80px column, Ink 500) then name, with any preparation note in Walnut (", drained").
- **Navigation row (Profile):** title (Body) over one Walnut line ("6 recipes", "Units, energy and account") and a 20px caret in Walnut; at least 64px tall. Rows are grouped under an Overline (Saved, App).
- **Value row (Settings › Account):** read-only label (Body) and value (Body, Walnut) on the right; at least 48px tall.

---

## Empty state

One component (`component.empty-state` in the tokens).

- Always: a neutral Oat circle with a 24px Ink icon (never terracotta), the title 16px below it, one Body line in Walnut (max 300px), all centred, and one action: the terracotta primary button (52px, radius 12, 0 24px padding) 24px below the text. The component draws the button itself, so no screen can style it differently.
- **Placement:** when a screen or a search has nothing to show, the whole group is centred in the content area between the 56px top bar and the 84px tab bar, not the whole phone screen, whatever sits above it (title, search field, filter chips). The group keeps its own spacing.
- Only the icon, copy and destination change, and the weight of the circle and title follows the situation:

| Situation | Circle and title | Where | Action |
|---|---|---|---|
| Nothing saved yet | 64px circle, Heading 3, text 8px below | Saved recipes ("No saved recipes yet", bookmark), My dishes ("No saved dishes yet", Dish) | Find a recipe · Check nutrition |
| No results | 48px circle, Title, text 4px below | Recipe search (search icon), nutrition search, Saved recipes search | Clear search · Build your own · Clear search |
| Nothing added yet | 48px circle, Title, text 4px below | Build a dish ("No ingredients yet", Dish) | None: the outlined Add ingredient button follows it |

- The empty builder is the one exception to the placement rule: it sits in the builder's flow, 24px below the Ingredients heading.

---

## Nutrition

### Nutrition summary panel
The same component everywhere a total is shown: dish results, custom dish results, product results and recipe detail.

- Card fill, 1px Hairline border, radius lg, 24px padding, 16px gap.
- Headline: Number XL value + what it is for, in Walnut, always with the weight when the data has one: "kcal per 100 g", "kcal per serving (200 g)", "kcal per bowl (241 g)", "kcal for 2 bowls (482 g)". A recipe shows "kcal per serving" (its servings have no weight in the data; the meta line says "Serves 4").
- Macro bar: three segments (Protein, Carbs, Fat) with a 4px gap, 8px tall, radius xs; widths follow the grams. Decorative (`aria-hidden`).
- Legend: 8px dot, name (Body), value (Number M) with the unit in Walnut (`typography.unit`). Each row is 24px.
- Stays on the Card surface because the macro colours are contrast-checked there.

---

## Feedback and overlays

### Snackbar
The only way to confirm saving or removing, for recipes (bookmark) and dishes (save control, My dishes bookmark). It appears on the same screen; there's no separate confirmation screen.

- Full width minus the 20px side margins, min 52px, radius md, `role="status"`.
- Card fill with a 1px Hairline inside stroke (no change in size) and elevation.1 + elevation.2 stacked (`component.snackbar.background`, `.border`, `.shadow`), so it stands clearly off the Cream page and off cards beneath it. Never terracotta.
- 20px bookmark icon in Ink (Fill after saving, Regular after removing), message in Label 600 in Ink, "Undo" text button in Terracotta 500 on the right: the one accent.
- Messages: "Saved to Saved recipes" · "Removed from Saved recipes" · "Saved to My dishes" · "Removed from My dishes".
- Floats 16px above whatever is at the bottom of the screen: the tab bar (bottom 100px), the action bar on results (bottom 112px), or the 24px safe area on Recipe detail (40px above the bottom of the drawn page, below the ingredients). Never over the main action.
- Stays for 4 seconds. Undo reverses the action.

### Info note
Oat fill, radius md, 20px Info icon, bold title and a short message. Kept for neutral notices, **not used on any current screen**.

### Bottom sheet
Adjust portion (dish and product results) and the ingredient sheet (Add ingredient, Edit ingredient) in Build a dish.

- Radius xl on the top corners, Card fill, `elevation.2`, over an Ink 40% scrim.
- 36 × 4px Hairline grabber, Heading 3 title with a Close button (20px X in a 44px target), content, then one primary button (Update, Add). Padding 8 / 20 / 32.
- Close and a tap on the scrim leave without changes.
- `role="dialog"`, `aria-modal="true"`, labelled by its title.

---

## Icons

Phosphor Regular, round caps and joins, the same visible 1.5px stroke at every size. Fill weight only for selected or active states. Each icon has one meaning.

| Icon | Phosphor name | Sizes | Used for |
|---|---|---|---|
| House, Leaf, BookOpen, User | House, Leaf, BookOpen, User | 24 | Tab bar (Fill when active) |
| Leaf, BookOpen | Leaf, BookOpen | 20 | Home action rows, Ink on a 40px Oat circle |
| Back | ArrowLeft | 20 | Top bar |
| Caret | CaretRight | 16, 20 | "See all" (16), Profile navigation rows (20) |
| Forward | ArrowRight | 20 | Home action rows |
| Search | MagnifyingGlass | 20, 24 | Search field (20), no-results empty state (24) |
| Bookmark | BookmarkSimple | 20, 24 | Bookmark button, save control, snackbar (20), Saved recipes empty state (24) |
| Plus | Plus | 20 | Add ingredient |
| X | X | 16, 20 | Clear a search field (16, in a 28px circle), close a sheet (20) |
| Trash | Trash | 20 | Remove an ingredient |
| Check | Check | 12 | Selected chip only |
| Check circle | CheckCircle (Fill) | 20 | Selected option row |
| Info | Info | 16, 20 | No data label, error message (16), info note (20) |
| Dish | BowlFood | 24, 48 | Empty states (24), photo placeholder (48) |

---

## Where each component is used

| Screen | Components |
|---|---|
| Home | H1 "Everyday Eats", tagline (Body large), Today's pick, Home action rows ×2, section header (Quick weeknight dinners + See all), 2 recipe cards, snackbar, tab bar (Home) |
| Find a recipe | H1, search field (opens recipe search), filter chips, featured card, section headers (See all on Dinner), recipe cards, snackbar, tab bar (Recipes) |
| Recipe search | Top bar, search field with text, filter chips, count line, recipe cards with matches highlighted, empty state (no results), snackbar, tab bar (Recipes) |
| Dinner collection | Top bar, H1, count line, filter chips (Vegetarian state), recipe cards, snackbar, tab bar (Recipes) |
| Recipe detail | Top bar, hero photo (4:5 crop at 390 × 320), bookmark button on the photo, overline, H1, meta, description, tags, nutrition panel, section header (Ingredients · For 4 servings), recipe ingredient rows, snackbar |
| Profile | H1, overlines (Saved, App), navigation rows (Saved recipes, My dishes, Settings), tab bar (Profile) |
| Saved recipes | Top bar, H1, count line, search field, filter chips (Breakfast / Lunch / Dinner), recipe cards (saved), empty states (nothing saved, no results), snackbar, tab bar (Profile) |
| My dishes | Top bar, H1, count line, saved dish rows, empty state, snackbar, tab bar (Profile) |
| Settings | Top bar, H1, single-choice chips (Units, Energy), overline (Account), value rows, tab bar (Profile) |
| Check nutrition | H1, intro, search field (opens nutrition search), overline, option cards ×2 with text links (Build your own, Scan barcode), tab bar (Eat) |
| Scan barcode | Top bar, H1, intro, camera view with a barcode frame (opens the product result once it reads the code), one Body small line in Walnut, tab bar (Eat) |
| Nutrition search | Top bar, search field with text, overlines in Terracotta 500 (Dishes, Packaged products), link rows, empty state (no match, Build your own), tab bar (Eat) |
| Dish result | Top bar, H1, meta, nutrition panel, breakdown rows, action bar (Adjust portion + save control), bottom sheet with amount field, snackbar |
| Product result | Top bar, H1, meta, single-choice chips (Per 100 g / Per serving (200 g)), nutrition panel, note, action bar (Adjust portion), bottom sheet with amount field |
| Build a dish | Top bar, H1 (Build a dish or Edit dish), text field (Dish name), section header with count, editable ingredient rows, empty state (no ingredients), outlined button (+ Add ingredient), action bar (Calculate nutrition, disabled with hint when empty; Cancel + Save changes in edit mode), bottom sheet (search field, option rows, amount field) |
| Custom dish result | Top bar, H1, meta, nutrition panel, breakdown rows (No data state), action bar (Edit dish + save control), snackbar |
