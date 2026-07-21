---
name: deck-builder
description: Use when the user wants a slide deck, presentation, pitch, or .pptx built from data, notes, a CSV, or a rough outline. Turns raw content into a clean, dark-themed, minimal presentation - not a wall of text. Trigger on "make a deck", "pricing slides", "pitch deck", "turn this into slides", or any .pptx request.
---

# Deck Builder

Build a real `.pptx` with `python-pptx`. Never output slide text as chat - always produce a file.

## Rules

1. **One idea per slide.** If a slide has more than ~6 lines, split it.
2. **Structure by default:** title slide -> one slide per item/section -> a comparison/summary slide.
3. **Dark, minimal theme** unless the user asks otherwise:
   - background `#0E0F13`, text `#ECEDEE`, muted `#8A8F98`, accent `#7CC4FF`, thin rules `#2A2D33`
   - font: a clean sans (Helvetica Neue / Inter / Arial fallback)
   - generous whitespace, no clip-art, no gradients
4. **16:9** (13.33 x 7.5 in). Big title type (40-54pt), readable body (16-20pt).
5. Pull numbers/labels straight from the source. Never invent figures.

## Steps

1. Read the source. If it's a CSV, parse it into rows.
2. Plan the slide list out loud (1 line each) before building.
3. Ensure `python-pptx` is installed; if missing, install it, then build.
4. Write a `build_deck.py` that defines the theme as constants and helpers
   (`set_slide_bg`, `add_text`, `add_rule`), then generates each slide.
5. Save as `<topic>.pptx` and tell the user the exact path.

## Quality bar

- Consistent alignment across slides (same left margin, same baseline grid).
- Comparison slide = equal-width columns, items side by side.
- No overflowing text. No default white template showing through.

## Output

A single `.pptx` file + one line: what it contains and where it is.
