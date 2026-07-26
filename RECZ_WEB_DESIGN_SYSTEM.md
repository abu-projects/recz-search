# Recz Web Design System

> Source of truth for building the Recz web experience, especially Search & Discovery, while preserving the visual language of the supplied dark and light interfaces.

## 1. Design Direction

Recz uses a **premium social-discovery aesthetic** built around:

- Apple-inspired liquid glass surfaces
- Soft atmospheric gradients and blurred color orbs
- A rose-to-pink brand accent
- Large rounded geometry
- Lightweight typography with compact labels
- Image-led content cards
- Clear separation between content, controls, and ambient decoration
- Identical component behavior in light and dark modes, with theme-specific material values

The web product must feel like a wider, more spacious continuation of the mobile app—not a separate dashboard product.

### Visual keywords

`Liquid glass` · `Social discovery` · `Editorial imagery` · `Soft depth` · `Modern` · `Premium` · `Friendly` · `Personalized`

---

## 2. Core Principles

### 2.1 Preserve the Recz identity

Do not replace the rose/pink identity with generic blue, purple, or SaaS-style colors. The primary Recz gradient is always:

```css
linear-gradient(135deg, #f43f5e 0%, #db2777 100%)
```

### 2.2 Use glass selectively

Glass is the material language, but not every element needs maximum blur. Use three levels:

1. **Primary Glass** — cards, modals, important panels
2. **Light Glass** — compact controls, icon buttons, secondary cards
3. **Inset Surface** — search fields, text inputs, selects

### 2.3 Content stays dominant

Photography, recommendations, people, ratings, and result titles must remain visually stronger than decoration. Ambient gradients should support depth, never reduce readability.

### 2.4 Light and dark modes share structure

Spacing, radius, component size, hierarchy, states, and motion stay identical. Only semantic color and material values change.

### 2.5 Web is responsive, not enlarged mobile

Use the same design language, but adapt composition:

- Mobile: single-column feed
- Tablet: two-column content where useful
- Desktop: search workspace with sidebar filters and multi-column results
- Wide desktop: constrained centered layout; never stretch content endlessly

---

## 3. Typography

### Font family

```css
font-family: "Poppins", sans-serif;
```

Use Poppins across the product. Outfit may be used only for selected editorial or media modules already styled that way; do not mix fonts inside one component.

### Font weights

| Purpose | Weight |
|---|---:|
| Page title / hero | 300–400 |
| Section title | 400–500 |
| Card title | 500–600 |
| Body | 300–400 |
| Labels / metadata | 400–500 |
| Buttons | 500–600 |

### Web type scale

| Token | Size / Line height | Usage |
|---|---|---|
| `display-lg` | 48 / 56 | Large landing or search discovery hero |
| `display-md` | 36 / 44 | Main web page title |
| `heading-xl` | 28 / 36 | Major section heading |
| `heading-lg` | 22 / 30 | Result group / panel title |
| `heading-md` | 18 / 26 | Card title |
| `body-lg` | 16 / 26 | Primary body |
| `body-md` | 14 / 22 | Default interface copy |
| `body-sm` | 12 / 18 | Metadata and supporting text |
| `label-xs` | 10 / 14 | Uppercase eyebrow / compact nav label |

### Typography behavior

- Main headings: `letter-spacing: -0.02em`
- Eyebrows: uppercase with `0.12em–0.16em` tracking
- Do not use heavy 700–800 weights for page headings
- Card titles may be semibold when readability requires it
- Avoid low-contrast gray body text in light mode

---

## 4. Color System

## 4.1 Brand colors

```css
--brand-rose: #f43f5e;
--brand-pink: #db2777;
--brand-purple: #a855f7;
--brand-orange: #fb923c;
--brand-gradient: linear-gradient(135deg, #f43f5e 0%, #db2777 100%);
--brand-text-gradient: linear-gradient(135deg, #f43f5e 0%, #fb923c 100%);
```

## 4.2 Dark theme

```css
[data-theme="dark"] {
  --bg-canvas: #050505;
  --bg-canvas-alt: #09080b;
  --text-primary: #ffffff;
  --text-secondary: #d4d4d8;
  --text-tertiary: #a1a1aa;
  --text-muted: #71717a;
  --border-subtle: rgba(255, 255, 255, 0.05);
  --border-strong: rgba(255, 255, 255, 0.10);
  --surface-glass: rgba(255, 255, 255, 0.045);
  --surface-glass-light: rgba(255, 255, 255, 0.035);
  --surface-input: rgba(255, 255, 255, 0.03);
  --surface-hover: rgba(255, 255, 255, 0.055);
  --surface-selected: #ffffff;
  --text-on-selected: #000000;
  --shadow-color: rgba(0, 0, 0, 0.48);
}
```

### Dark canvas background

```css
background-color: #050505;
background-image:
  radial-gradient(circle at 12% 22%, rgba(244, 63, 94, 0.12), transparent 28%),
  radial-gradient(circle at 86% 18%, rgba(168, 85, 247, 0.12), transparent 30%),
  radial-gradient(circle at 52% 84%, rgba(236, 72, 153, 0.06), transparent 36%),
  linear-gradient(180deg, #050505 0%, #09080b 52%, #050505 100%);
```

## 4.3 Light theme

```css
[data-theme="light"] {
  --bg-canvas: #f3f3f3;
  --bg-canvas-alt: #ffffff;
  --text-primary: #171717;
  --text-secondary: #404040;
  --text-tertiary: #737373;
  --text-muted: #a3a3a3;
  --border-subtle: rgba(0, 0, 0, 0.07);
  --border-strong: rgba(0, 0, 0, 0.12);
  --surface-glass: rgba(255, 255, 255, 0.72);
  --surface-glass-light: rgba(255, 255, 255, 0.50);
  --surface-input: rgba(255, 255, 255, 0.60);
  --surface-hover: rgba(255, 255, 255, 0.80);
  --surface-selected: #171717;
  --text-on-selected: #ffffff;
  --shadow-color: rgba(0, 0, 0, 0.12);
}
```

### Light noise texture

Use a very subtle monochrome noise texture over `#f3f3f3` and white glass surfaces. Opacity should remain approximately `0.06–0.08`.

## 4.4 Semantic colors

| Meaning | Color |
|---|---|
| Success / Solid Rec | `#34d399` |
| Warning / Hyped | `#fbbf24` |
| Craving | `#fde047` |
| Information / Curious | `#60a5fa` |
| Not My Vibe | `#c084fc` |
| Error | `#ef4444` |
| Rating accent | brand rose / soft rose surface |

Do not use semantic colors as large backgrounds unless they communicate a real status.

---

## 5. Spacing and Layout

### Base spacing scale

```css
--space-1: 4px;
--space-2: 8px;
--space-3: 12px;
--space-4: 16px;
--space-5: 20px;
--space-6: 24px;
--space-8: 32px;
--space-10: 40px;
--space-12: 48px;
--space-16: 64px;
--space-20: 80px;
```

### Web containers

```css
--container-sm: 720px;
--container-md: 1040px;
--container-lg: 1280px;
--container-xl: 1440px;
```

- Default desktop page max width: `1280px`
- Search/discovery workspace max width: `1440px`
- Horizontal page padding:
  - Mobile: `16px`
  - Tablet: `24px`
  - Desktop: `32px`
  - Wide desktop: `40px`

### Search page desktop grid

```css
grid-template-columns: 280px minmax(0, 1fr);
gap: 32px;
```

Optional right context panel:

```css
grid-template-columns: 260px minmax(0, 1fr) 320px;
```

Use the three-column version only when the right panel contains useful live context such as map, saved list, or Rexy assistant—not empty decoration.

### Result grids

- People cards: 3–5 columns based on width
- Recommendation cards: 2–3 columns
- Photo content: responsive masonry or 3-column grid
- Rollz/video: 3–4 portrait cards
- Lists: 2–3 columns

---

## 6. Radius System

```css
--radius-sm: 10px;
--radius-md: 14px;
--radius-lg: 16px;
--radius-xl: 20px;
--radius-2xl: 24px;
--radius-3xl: 32px;
--radius-pill: 999px;
```

Rules:

- Search input: `16–20px`
- Standard card: `20–24px`
- Large feature card / modal: `28–32px`
- Chips and compact tabs: pill radius
- Icon-only controls: circle or `12–16px`
- Avoid sharp rectangles

---

## 7. Elevation and Glass Materials

## 7.1 Dark primary glass

```css
.glass-primary {
  background: rgba(255, 255, 255, 0.045);
  backdrop-filter: blur(28px) brightness(1.1) saturate(195%);
  -webkit-backdrop-filter: blur(28px) brightness(1.1) saturate(195%);
  border: 1px solid rgba(255, 255, 255, 0.055);
  box-shadow:
    0 14px 44px rgba(0, 0, 0, 0.48),
    inset 0 1px 0 rgba(255, 255, 255, 0.12),
    inset 0 -1px 0 rgba(255, 255, 255, 0.04);
}
```

## 7.2 Dark secondary glass

```css
.glass-secondary {
  background: rgba(255, 255, 255, 0.035);
  backdrop-filter: blur(18px) brightness(1.08) saturate(180%);
  -webkit-backdrop-filter: blur(18px) brightness(1.08) saturate(180%);
  border: 1px solid rgba(255, 255, 255, 0.045);
  box-shadow:
    0 10px 32px rgba(0, 0, 0, 0.36),
    inset 0 1px 0 rgba(255, 255, 255, 0.09),
    inset 0 -1px 0 rgba(255, 255, 255, 0.03);
}
```

## 7.3 Light primary glass

```css
.glass-primary {
  background:
    var(--noise-bg),
    linear-gradient(135deg, rgba(255, 255, 255, 0.72), rgba(255, 255, 255, 0.45));
  backdrop-filter: blur(40px) saturate(200%);
  -webkit-backdrop-filter: blur(40px) saturate(200%);
  border: 1px solid rgba(255, 255, 255, 0.55);
  border-top-color: rgba(255, 255, 255, 0.85);
  border-left-color: rgba(255, 255, 255, 0.65);
  box-shadow:
    0 24px 48px -12px rgba(0, 0, 0, 0.12),
    inset 0 1px 0 rgba(255, 255, 255, 0.95),
    inset 0 -1px 0 rgba(0, 0, 0, 0.04),
    0 8px 32px rgba(244, 63, 94, 0.06);
}
```

## 7.4 Light secondary glass

```css
.glass-secondary {
  background-color: rgba(255, 255, 255, 0.5);
  background-image: var(--noise-bg);
  backdrop-filter: blur(24px);
  -webkit-backdrop-filter: blur(24px);
  border: 1px solid rgba(255, 255, 255, 0.7);
  border-top-color: rgba(255, 255, 255, 0.9);
  box-shadow:
    0 8px 24px rgba(0, 0, 0, 0.08),
    inset 0 1px 0 rgba(255, 255, 255, 0.9);
}
```

### Fallback

When `backdrop-filter` is unsupported, use a nearly opaque theme surface and preserve border/shadow hierarchy.

---

## 8. Search Experience

## 8.1 Search page anatomy

The primary Recz web search screen should contain:

1. Global top navigation
2. Search hero / query area
3. Search input with Rexy action
4. Search category tabs
5. Filter controls
6. Suggested or recent searches before typing
7. Grouped results after typing
8. Empty, loading, no-results, and error states

### Desktop composition

```text
┌─────────────────────────────────────────────────────────────┐
│ Global navigation                                           │
├─────────────────────────────────────────────────────────────┤
│ Search title + supporting text                              │
│ [ Search input................................ ] [Rexy]     │
│ All  Recz  People  Rollz  Lists  Events  Threads            │
├───────────────┬─────────────────────────────────────────────┤
│ Filters       │ Result summary / sort                       │
│ Category      │                                             │
│ Location      │ Result groups or responsive grid            │
│ Vibe          │                                             │
│ Budget        │                                             │
│ Circle        │                                             │
└───────────────┴─────────────────────────────────────────────┘
```

On mobile, filters open in a bottom sheet or full-screen panel.

## 8.2 Main search field

### Size

- Desktop height: `56px`
- Mobile height: `48–52px`
- Horizontal padding: `16px`
- Radius: `18–20px`
- Search icon: `18–20px`
- Text: `14–16px`

### Dark search field

```css
.search-field {
  background: rgba(255, 255, 255, 0.04);
  border: 1px solid rgba(255, 255, 255, 0.05);
  box-shadow:
    inset 0 1px 0 rgba(255, 255, 255, 0.04),
    0 8px 28px rgba(0, 0, 0, 0.20);
}
```

Focused:

```css
.search-field:focus-within {
  background: rgba(255, 255, 255, 0.055);
  border-color: rgba(244, 63, 94, 0.18);
  box-shadow:
    0 0 0 3px rgba(244, 63, 94, 0.10),
    0 0 28px rgba(244, 63, 94, 0.14);
}
```

### Light search field

```css
.search-field {
  background: #ffffff;
  border: 1px solid rgba(0, 0, 0, 0.07);
  box-shadow:
    inset 0 2px 6px rgba(0, 0, 0, 0.06),
    0 1px 3px rgba(0, 0, 0, 0.04);
}
```

Focused:

```css
.search-field:focus-within {
  border-color: rgba(244, 63, 94, 0.40);
  box-shadow:
    inset 0 2px 8px rgba(0, 0, 0, 0.06),
    0 0 0 3px rgba(244, 63, 94, 0.12);
}
```

### Search actions

The right side may include:

- Clear button when a query exists
- Voice input, when supported
- Rexy button using the magic-stick icon

Rexy action style:

```css
width: 32px;
height: 32px;
border-radius: 999px;
background: rgba(244, 63, 94, 0.15);
border: 1px solid rgba(244, 63, 94, 0.20);
color: #fda4af;
```

The button should open contextual AI search, not silently replace normal search behavior.

## 8.3 Search tabs

Suggested categories:

- All
- Recz
- People
- Rollz
- Lists
- Events
- Threads

Tabs use compact icon + label on large screens and horizontally scroll on mobile.

Active tab options:

- Dark mode: white foreground surface with black text
- Light mode: dark foreground surface with white text
- Brand-active variation: rose translucent surface with rose text

Choose one active treatment consistently across the page. The default Recz pattern uses strong high-contrast active chips.

## 8.4 Filter chips

```css
.filter-chip {
  min-height: 34px;
  padding: 8px 14px;
  border-radius: 999px;
  font-size: 12px;
  font-weight: 500;
  white-space: nowrap;
  transition: 150ms ease;
}
```

Possible quick filters:

- Friends
- Near me
- Tonight
- Trending
- Hidden gems
- Open now
- Budget
- Saved by circle

## 8.5 Filter sidebar

Use a sticky glass panel on desktop.

Sections:

- Content type
- Category
- Location / distance
- Vibe
- Occasion
- Budget
- Rating
- Circle / people
- Date / time

Rules:

- Do not show all advanced controls by default
- Use collapsible sections
- Show active filter count
- Provide Clear All
- Keep the primary Apply action sticky on mobile only

## 8.6 Autocomplete panel

The dropdown should align exactly with the search field width and use primary glass.

Groups:

- Recent searches
- Suggested queries
- People
- Places / recommendations
- Categories
- Ask Rexy suggestion

Each row:

- Minimum height: `48px`
- Leading icon/avatar: `32–40px`
- Title: `14px / 500`
- Supporting text: `12px`
- Hover background: subtle theme surface
- Keyboard-selected row: rose-tinted surface + visible focus indicator

## 8.7 Search results hierarchy

### All results

Use grouped sections, not one undifferentiated grid:

- Popular with your circle
- Recommendations
- People
- Rollz
- Lists
- Events
- Threads

Each section gets:

- Section title
- Optional result count
- “View all” action
- Contextual layout suited to the content type

### Single-category results

Use a full responsive grid or list with sorting and filters.

### Result card minimum data

Recommendation card:

- Cover image
- Name
- Category and location
- Rating
- Social proof
- Save action
- Optional Rexy action

People card:

- Avatar
- Name / handle
- Match percentage or shared interests
- Short context
- Follow / connect action

Rollz card:

- Portrait media
- Play indicator
- Creator
- View count

List card:

- Cover collage
- List title
- Creator
- Number of items
- Save/follow action

---

## 9. Cards

### Standard card

- Radius: `20–24px`
- Use primary or secondary glass
- Image clipped to card radius
- Content padding: `16px`
- Internal gap: `8–12px`
- Hover: lift by `1–2px`, slightly stronger border and shadow

### Image behavior

```css
object-fit: cover;
transition: transform 700ms cubic-bezier(0.22, 1, 0.36, 1);
```

Hover scale should not exceed `1.06–1.08`.

### Rating badge

```css
background: rgba(244, 63, 94, 0.15);
border: 1px solid rgba(244, 63, 94, 0.20);
color: #fda4af;
border-radius: 999px;
```

Light mode may use darker rose text for contrast.

### Social proof

Examples:

- `3 Buddies saved this`
- `94% match`
- `Popular with your circle`
- `Lina rated this`

Use avatar stacks or one avatar plus text. Keep it compact and supportive.

---

## 10. Navigation

## 10.1 Desktop top navigation

Recommended structure:

- Recz logo
- Home
- Explore
- Search
- Rollz
- Events
- Messages
- Spacer
- Rexy shortcut
- Notifications
- Profile
- Theme toggle

Height: `72–80px`

The navigation may be sticky with a glass background. Avoid a heavy opaque navbar.

## 10.2 Mobile navigation

Retain the floating pill navigation style from the mobile design. On web mobile, it may become fixed to the bottom with safe-area spacing.

## 10.3 Active navigation

- High contrast icon and label
- Optional subtle rose glow
- No oversized underline

---

## 11. Buttons

### Primary button

```css
background: linear-gradient(135deg, #f43f5e 0%, #db2777 100%);
color: #ffffff;
border-radius: 16px;
box-shadow:
  0 12px 34px rgba(244, 63, 94, 0.36),
  0 0 34px rgba(219, 39, 119, 0.22);
```

- Height: `44–48px`
- Horizontal padding: `18–24px`
- Font: `14px / 600`

### Secondary button

Use secondary glass, neutral text, and a subtle border.

### Tertiary button

Text/icon only. Use for “View all,” “Clear,” or small inline actions.

### Icon button

- Small: `32px`
- Default: `40px`
- Large: `48px`
- Radius: circle or `12–16px`

### Destructive button

Do not use the Recz brand gradient for destructive actions. Use semantic red with restrained styling.

---

## 12. Forms and Controls

### Inputs

- Height: `48–56px`
- Radius: `16px`
- Label above field, not placeholder-only for important forms
- Focus ring: rose translucent ring
- Error text: below field, 12px
- Disabled: reduced contrast, no glow

### Select and combobox

Match input material and size. Dropdowns use glass panels with strong readable contrast.

### Checkbox / radio

Selected state uses brand rose. Keep controls at least `20px` with a `44px` interactive target.

### Toggle

- Off: neutral translucent track
- On: rose-to-pink gradient
- Knob: white

---

## 13. States

## 13.1 Search idle

Show a curated starting point:

- Recent searches
- Trending searches
- Popular with your circle
- Quick category cards
- Rexy suggestion prompt

## 13.2 Loading

Use skeletons matching real card geometry. Avoid generic centered spinners for the full page.

## 13.3 No results

Structure:

- Simple icon or small illustration
- “No results for ‘query’”
- One line of guidance
- Suggested filter removal
- Ask Rexy action

Do not blame the user or show a dead end.

## 13.4 Empty category

Use contextual copy such as:

- “No saved lists yet”
- “No Rollz match these filters”
- “Try expanding the distance”

## 13.5 Error

Explain that results could not be loaded and provide Retry. Preserve the current query and filters.

## 13.6 Offline

Show cached or recent results when available, clearly labeled.

---

## 14. Motion

### Timing

```css
--duration-fast: 150ms;
--duration-normal: 220ms;
--duration-slow: 320ms;
--ease-standard: cubic-bezier(0.4, 0, 0.2, 1);
--ease-spring: cubic-bezier(0.16, 1, 0.3, 1);
```

### Approved motion

- Hover lift: `translateY(-1px)`
- Button press: `scale(0.98)`
- Card image hover: `scale(1.04–1.08)`
- Dropdown: fade + `translateY(6px)`
- Page section reveal: subtle fade-up
- Reaction icon: small micro-bounce

### Avoid

- Constant floating animations
- Large parallax movement
- Slow glass warping during normal navigation
- Excessive glowing pulses

Respect `prefers-reduced-motion`.

---

## 15. Icons and Imagery

### Icon system

Use Solar icons through Iconify where possible.

Recommended style:

- Linear icons for neutral/default actions
- Bold icons for selected or emphasized actions
- Keep one icon family per component

Typical sizes:

- Metadata: `14–16px`
- Controls: `18–20px`
- Navigation: `20–22px`
- Feature icon: `24–32px`

### Imagery

- Use high-quality lifestyle photography
- Favor authentic social content over stock-heavy corporate imagery
- Apply subtle contrast/saturation treatment only
- Preserve natural skin tones
- Always define `object-position` where the crop matters

---

## 16. Accessibility

- Minimum normal text contrast: WCAG AA
- Do not use placeholder text as the only label in forms
- Every icon button needs an accessible name
- Keyboard focus must be visible
- Search autocomplete must support arrow keys, Enter, and Escape
- Tabs must use correct tab semantics
- Filter drawer must trap focus while open
- Minimum interactive target: `44 × 44px`
- Do not communicate selected, error, or status states through color alone
- Support `prefers-reduced-motion`
- Use `aria-live` for changing search result counts

Blurred glass must never reduce text contrast below readable levels.

---

## 17. Responsive Behavior

### Mobile: `< 640px`

- Single-column results
- Horizontal tab and chip scrolling
- Filters in bottom sheet/full-screen panel
- Sticky search header
- Bottom navigation

### Tablet: `640–1023px`

- Two-column recommendation grid
- Optional compact filter drawer
- Desktop-style top navigation may replace bottom navigation at larger tablet widths

### Desktop: `1024–1439px`

- Sticky left filter panel
- Two- or three-column result grid
- Search field centered within main content

### Wide desktop: `≥ 1440px`

- Maximum container `1440px`
- More breathing room, not oversized type
- Three-column result grids where card width remains comfortable

---

## 18. Theme Implementation

Use semantic CSS variables and switch themes through `data-theme`.

```html
<html data-theme="dark">
```

```js
document.documentElement.dataset.theme = selectedTheme;
```

Theme options:

- `light`
- `dark`
- `system`

For `system`, resolve with:

```js
window.matchMedia('(prefers-color-scheme: dark)').matches
```

Persist the user choice locally and sync it to the account when authentication is available.

Do not duplicate complete component CSS for each theme. Components should consume semantic tokens.

---

## 19. Recommended Token Starter

```css
:root {
  --font-sans: "Poppins", sans-serif;

  --brand-rose: #f43f5e;
  --brand-pink: #db2777;
  --brand-purple: #a855f7;
  --brand-gradient: linear-gradient(135deg, #f43f5e 0%, #db2777 100%);

  --radius-sm: 10px;
  --radius-md: 14px;
  --radius-lg: 16px;
  --radius-xl: 20px;
  --radius-2xl: 24px;
  --radius-3xl: 32px;
  --radius-pill: 999px;

  --space-1: 4px;
  --space-2: 8px;
  --space-3: 12px;
  --space-4: 16px;
  --space-5: 20px;
  --space-6: 24px;
  --space-8: 32px;
  --space-10: 40px;
  --space-12: 48px;
  --space-16: 64px;

  --duration-fast: 150ms;
  --duration-normal: 220ms;
  --duration-slow: 320ms;
  --ease-standard: cubic-bezier(0.4, 0, 0.2, 1);
  --ease-spring: cubic-bezier(0.16, 1, 0.3, 1);
}
```

---

## 20. Search Component Inventory

Build these reusable components before assembling the page:

1. `AppShell`
2. `TopNavigation`
3. `ThemeToggle`
4. `GlobalSearchField`
5. `RexySearchAction`
6. `SearchTabs`
7. `QuickFilterChip`
8. `FilterSidebar`
9. `FilterDrawer`
10. `AutocompletePanel`
11. `SearchResultSection`
12. `RecommendationCard`
13. `PersonCard`
14. `RollzCard`
15. `ListCard`
16. `EventCard`
17. `ThreadCard`
18. `ResultSkeleton`
19. `SearchEmptyState`
20. `SearchErrorState`
21. `Pagination` or `InfiniteScrollSentinel`

Every component must support both themes without separate markup.

---

## 21. Search Page Acceptance Criteria

The implementation is visually correct only when:

- Poppins is loaded and used consistently
- The exact rose-to-pink accent gradient is retained
- Light mode uses `#f3f3f3`, white glass, subtle noise, and neutral dark text
- Dark mode uses `#050505`, ambient rose/purple gradients, white text, and translucent glass
- Search field, cards, chips, and navigation share one radius and spacing system
- Desktop does not look like a stretched phone screen
- Mobile remains visually consistent with the supplied app screens
- Focus, hover, selected, loading, empty, and error states are designed
- Search categories and filters work across keyboard, touch, and mouse
- Glass effects have readable fallbacks
- The user can switch between light, dark, and system themes

---

## 22. Design Guardrails

### Do

- Use atmosphere behind content
- Keep surfaces translucent and layered
- Use compact, useful metadata
- Maintain strong image hierarchy
- Keep the brand gradient for primary actions and highlights
- Use pill chips and rounded search controls
- Make Rexy visible but secondary to normal search

### Do not

- Turn the interface into a generic admin dashboard
- Use pure white cards everywhere in light mode without glass/noise depth
- Use solid gray cards everywhere in dark mode
- Introduce a new primary color
- Overuse heavy font weights
- Put glows behind every element
- Use excessive borders
- Hide essential labels inside placeholders
- Make every result card the same layout regardless of content type

---

## 23. Final Visual Summary

The Recz web search experience should feel like a **wide-screen continuation of the mobile Recz world**: a soft dark or bright textured canvas, translucent liquid-glass panels, strong lifestyle imagery, compact social context, and a clear rose/pink identity. It must remain useful first, atmospheric second.
