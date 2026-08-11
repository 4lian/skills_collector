---
name: galaxy
description: A massive, ready-to-use collection of 3000+ hand-crafted UI elements (buttons, cards, checkboxes, inputs, forms, toggles, loaders, tooltips, notifications, patterns) sourced from Uiverse.io. Each element is a single self-contained HTML file with inline CSS/JS. Use when you need a copy-paste UI component, want inspiration for a control's look, or are asked for "button", "card", "toggle", "loader", "input", "checkbox", "form" implementations.
---

# Galaxy — Uiverse.io UI Element Collection

A vendored copy of [uiverse-io/galaxy](https://github.com/uiverse-io/galaxy): 3000+ unique UI elements curated from [Uiverse.io](https://uiverse.io/). Every element is a single self-contained `.html` file (HTML + inline CSS, sometimes inline JS) you can open, preview, and lift into any project.

## Categories

| Category | Dir | Count |
|---|---|---|
| Buttons | `ui/galaxy/Buttons/` | 1231 |
| Cards | `ui/galaxy/Cards/` | 726 |
| Loaders | `ui/galaxy/loaders/` | 718 |
| Toggle switches | `ui/galaxy/Toggle-switches/` | 260 |
| Inputs | `ui/galaxy/Inputs/` | 226 |
| Forms | `ui/galaxy/Forms/` | 180 |
| Checkboxes | `ui/galaxy/Checkboxes/` | 171 |
| Patterns | `ui/galaxy/Patterns/` | 103 |
| Radio buttons | `ui/galaxy/Radio-buttons/` | 102 |
| Tooltips | `ui/galaxy/Tooltips/` | 62 |
| Notifications | `ui/galaxy/Notifications/` | 23 |

(Exact counts may drift as upstream adds elements; see `CATALOG.md` for the full index.)

## How to use

1. **Find a component.** Browse `CATALOG.md` (searchable index of all elements), or list a category dir directly:
   - `ls ui/galaxy/Buttons/`
   - Grep by author/name: `grep -l "hungry penguin" ui/galaxy/Buttons/*.html` or just scan filenames (`author_component-name-id.html`).
2. **Read it.** Open the `.html` file. It is fully self-contained — styles live in a `<style>` block, behavior (if any) in `<script>`. No build step, no dependencies.
3. **Reuse it.** Copy the markup + the relevant CSS (and JS) into your project. Tweak colors, sizes, and copy to match the surrounding design system.
4. **Adapt, don't worship.** These are starting points. Strip Uiverse-specific chrome, rename classes to your convention, and make sure it meets your accessibility and responsive requirements before shipping.

## Best practices

- Treat each file as a **reference snippet**, not a drop-in module. Inline styles are great for preview, poor for maintenance — extract to your stylesheet.
- Honor **`prefers-reduced-motion`** if the element animates; many of these do not, so add it yourself.
- Check contrast and focus states; community submissions vary in a11y quality.
- Keep it lightweight: prefer `transform`/`opacity` for motion, avoid layout-thrashing animations.

## Licensing & attribution

All elements are **MIT Licensed** (see `ui/galaxy/LICENSE`). You are free to use, modify, and distribute them. Attribution is not mandatory but appreciated — credit the original creator (encoded in the filename as `author_`) and [Uiverse.io](https://uiverse.io/).

## Notes for this vendored copy

- This directory is refreshed from upstream `uiverse-io/galaxy` via the repo's `sync.py` (registered in `sync-manifest.json`). Upstream-only additions (new elements) appear in the category folders; this `SKILL.md` and `CATALOG.md` are local and preserved across syncs.
- `CATALOG.md` is a generated snapshot; when in doubt, trust the actual folder contents.
