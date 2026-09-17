# Handoff: Presentation Overhaul — Claude Code Power User Playbook

---

## Phase 1 — Slide Content Rewrite ✅ COMPLETE

All 22 slides written and confirmed. Deck covers the full power-user sequence:
Title → Core Constraint → CLAUDE.md setup/content → Verification Loops → Power Workflow →
Prompting → Advanced Prompts → Parallelism → Git Worktrees → Hooks →
Token Efficiency → Custom Skills → Subagents → MCP Servers →
MEMORY.md → Headless/CI → Power User Mindset → Resources → Thank You

Active file: `index.html` (single-file HTML presentation)
Live URL: https://booya1986.github.io/Claude-Code-tips/

---

## Phase 2 — Ojemba Brand Redesign 🔄 IN PROGRESS

### What Changed & Why
User provided brand assets (`color-pallet.png`, `fonts.png`) from the Ojemba Visual Identity Guideline.
Goal: Replace the generic dark-on-black monospace look with Ojemba's brand system + add dark/light mode toggle.

### Brand Tokens Applied
| Token | Value | Role |
|-------|-------|------|
| Ojemba Blue | `#001342` | Dark mode background, light mode text |
| Ojemba Green | `#8ACC50` | Primary accent (bullets, highlights, command names) |
| Ojemba Forest Green | `#116355` | Light mode accent, secondary surfaces |
| Ojemba Space Grey | `#384051` | Muted text, secondary UI |

**Font:** `Plus Jakarta Sans` (Google Fonts — closest free match to GT Flexa which is the brand font).
JetBrains Mono retained for all code blocks.

### CSS Architecture
All colors are CSS custom properties. Dark mode is the default (`:root`). Light mode is `body.light-mode`.
Body has `transition: background 0.35s ease, color 0.35s ease` for smooth switching.

Key variables:
```
--bg, --bg-depth          background layers
--surface, --surface-hover   card/panel fills
--border, --border-hover     borders
--text-primary/secondary/muted   typography hierarchy
--accent, --accent-2          brand green (dark) / forest green (light)
--code-bg, --code-border, --code-text   code block theming
--section-rule               heading underline rule colour
--pie-inner-bg, --counter-color, --card-num, --li-bullet  misc
```

---

## CSS Sections Written So Far

| # | Rule(s) | Status |
|---|---------|--------|
| 1 | `:root` — dark mode brand tokens | ✅ |
| 2 | `body.light-mode` — light mode overrides | ✅ |
| 3 | `*` reset | ✅ |
| 4 | `body` — Plus Jakarta Sans, CSS var background + transition | ✅ |
| 5 | `body::before` — dot pattern using `var(--dot-color)` | ✅ |
| 6 | `.slideshow-container` | ✅ |
| 7 | `.slide` + `.slide.active` | ✅ |
| 8 | `@keyframes fadeIn` | ✅ |
| 9 | `h1 / h2 / h3` — all colors via vars | ✅ |
| 10 | `p / li / ul / li::before / .subtitle` — `var(--li-bullet)` for arrows | ✅ |
| 11 | `.slide-counter` | ✅ |
| 12 | `.code-block` — green-tinted bg/border in dark, teal in light | ✅ |
| 13 | `.highlight` + `.slide code` (global inline code rule) + `.center` | ✅ |
| 14 | `.export-btn` + `.theme-toggle` (NEW — positioned left of export) | ✅ |
| 15 | `.author-info / .author-line / .profile-pic / .pixel-avatar / .dates-info` | ✅ |
| 16 | `@media print` — locked to Ojemba Blue bg, green highlights | ✅ |
| 17 | `body.printing` helper | ✅ |
| 18 | `@media (max-width: 768px)` — theme toggle at `right: 128px` | ✅ |
| 19 | `@media (max-width: 480px)` — theme toggle at `right: 108px` | ✅ |
| 20 | `@media landscape` — theme toggle at `right: 118px` | ✅ |
| 21 | `.chart-container / .pie-chart-wrapper / .pie-chart-outer` | ✅ |
| 22 | `.pie-segment` base + `@keyframes segmentGrow` | ✅ |
| 23 | `.segment-1` through `.segment-7` — Ojemba brand palette | ✅ |
| 24 | `.pie-chart-inner` + `.chart-total` + `.chart-label` | ✅ |
| 25 | `.chart-legend / .legend-item / .legend-color / .legend-text / .legend-label / .legend-percentage / .chart-stats` | ✅ |
| 26 | `.commands-container` | ✅ |
| 27 | `.command-section` + `.command-section h3` | ✅ |
| 28 | `.command-grid` | ✅ |
| 29 | `.command-item` + hover | ✅ |
| 30 | `.command-name` + `.command-desc` + all command breakpoints | ✅ |
| 31 | `.installation-steps` | ✅ |
| 32 | `.install-section h3` + `::before` arrow — `var(--accent)` | ✅ |
| 33 | `.practice-container` | ✅ |
| 34 | `.practice-section` + hover + heading | ✅ |
| 35 | `.practice-step / .step-number / .step-desc` + breakpoints | ✅ |
| 36 | `.troubleshoot-container` | ✅ |
| 37 | `.issue-item` + hover | ✅ |
| 38 | `.issue-title / .issue-solution / .issue-solution code` | ✅ |
| 39 | `.resources-container` | ✅ |
| 40 | `.resource-section` + hover + heading + li + all breakpoints | ✅ |

---

## CSS Sections Still To Write

| # | Rule(s) | Notes |
|---|---------|-------|
| 41 | Height-based queries — `max-height: 700px / 600px / 500px` | Currently still old values |
| 42 | Combined width+height — `(max-width: 768px) and (max-height: 500px)` | Currently still old values |
| 43 | Mobile scrolling blocks — `(max-width: 768px) and (max-height: 800px)` + `(max-width: 480px)` scrolling | Currently still old values |
| 44 | Portrait orientation fix — `(max-width: 480px) and (orientation: portrait) and (max-height: 700px)` | Currently still old values |
| 45 | `z-index` overrides for `.export-btn` + `.slide-counter` at bottom of CSS | Remove these — already handled in rules 11 & 14 |

---

## HTML Still To Do (after CSS complete)

- [ ] Add `<button class="theme-toggle" id="theme-toggle">☀️</button>` to body (next to `.export-btn`)
- [ ] Update `exportToPDF()` alert to mention `.theme-toggle` is hidden in print
- [ ] Add `toggleTheme()` JS function + `localStorage` persistence to `<script>` block
- [ ] Update inline `style="color: #666/999/ccc"` attributes in slide HTML to use `color: var(--counter-color)` etc.
- [ ] Strip `style="background:rgba(255,255,255,0.08)..."` from inline `<code>` tags — now covered by `.slide code` rule (rule 13)
- [ ] Update agenda slide number chips: `style="color: #555"` → `style="color: var(--card-num)"`

---

## Protocol for Resuming
- User reviews and approves 5 CSS rules at a time, then says "go ahead"
- After all CSS is done, do the HTML wiring (button + JS) as one step
- No changes to slide content — Phase 1 is locked
