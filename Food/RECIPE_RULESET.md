# Recipe Vault Ruleset

## Overview
This document defines the complete standardized format and tagging system for all recipes in the vault.

---

## YAML Frontmatter Structure

Every recipe must include the following YAML frontmatter at the top:

```yaml
---
tags:
  - tag1
  - tag2/subcategory
  - parent_tag
source: URL or Book Title
Cuisine: Cuisine Type or [Array, Of, Types]
Type: Main|Side|Dessert|Drink|Base|Condiment
Meal: [Array of: Breakfast, Lunch, Dinner, Snack]
Difficulty: [Leave blank or: Easy, Medium, Hard]
Author: Author Name
Date added: YYYY-MM-DD
image: filename.webp
obsidianUIMode: preview
aliases:
  - Alternative Name
---
```

### Field Details

| Field | Required | Format | Notes |
|-------|----------|--------|-------|
| tags | Yes | Array | See tagging rules below |
| source | Yes | URL or string | Include full URL for web sources |
| Cuisine | No | String or array | e.g., "Italian" or ["Italian", "Mediterranean"] |
| Type | Yes | Single value | Must be one of the main types |
| Meal | No | Array | Typical meal times for this dish |
| Difficulty | No | Leave blank | If filled, use: Easy, Medium, or Hard |
| Author | Yes | String | Person or organization name |
| Date added | Yes | YYYY-MM-DD | **Always use current date when creating** |
| image | Yes | Filename | Must be .webp format |
| obsidianUIMode | Yes | "preview" | Renders note in preview mode by default |
| aliases | No | Array | Original name if title was simplified |

---

## Tagging System

### Core Tagging Rules

**Ingredient Tags:**
- Only tag prominent or large-quantity ingredients
- Never tag pantry staples
- Use quantitative thresholds for consistency

**Specific Ingredient Thresholds:**

| Ingredient | Rule |
|-----------|------|
| Garlic | Minimum 1 full bulb (8+ cloves) |
| Lemon/Lime | Only if major part of dish or large quantities |
| Onions | Only if prominent or large quantity |
| Sugar | Never (pantry staple) |
| Turmeric, Cumin, Fennel, Red Pepper Flakes | Never (pantry staples) |
| Butter, Eggs, Milk | Only if prominent/large amount |
| Vanilla | Never (pantry staple) |

### Hierarchy & Parent Tags

**Bases Plugin Requirement:** When using subcategorized tags (e.g., `beef/ground`), always include the parent tag (`beef`) in the tags array for Bases plugin compatibility.

**Example:**
```yaml
tags:
  - beef           # Parent tag
  - beef/ground    # Child tag
  - tomatoes       # Flat tag
```

### Standard Subcategory Patterns

Use these established hierarchies for consistency:

**Proteins:**
- `beef/ground`, `beef/chuckroast`
- `pork/bacon`, `pork/pancetta`, `pork/ground`
- `chicken`
- `seafood/salmon`, `seafood/scallops`, `seafood/shrimp`, `seafood/crab`, `seafood/anchovies`

**Vegetables:**
- `potatoes/russet`, `potatoes/yukonGold`, `potatoes/sweet`
- `tomatoes/cherry`, `tomatoes/grape`, `tomatoes/canned/diced`
- `mushrooms/crimini`, `mushrooms/button`

**Legumes:**
- `beans/black`, `beans/cannellini`, `beans/butter`, `beans/navy`

**Dairy & Milk:**
- `cheese/parmesan`, `cheese/cream`, `cheese/halloumi`, `cheese/cheddar`, `cheese/american`
- `milk/coconut`, `milk/sweetenedcondensed`, `milk/butter`

**Carbs & Noodles:**
- `noodles/spaghetti`, `noodles/orecchiette`, `noodles/lasagna`, `noodles/freshramen`

**Spicy Elements:**
- `chiles/chipotle`

### Tag Categories

**Dish Type Tags:**
- Main, Side, Dessert, Soup, Salad, Sandwich, Tacos, etc.

**Equipment Tags:**
- instantpot, slowcooker, etc. (only if specialty equipment required)

**Special Tags:**
- wishlist (not yet made)
- party, camping (occasion/context specific)
- healthy, etc. (descriptive)

---

## Recipe Structure & Content

### Section Order

1. **YAML Frontmatter** (required)
2. **Image Embed** (required)
3. **Ingredients Section**
4. **Directions Section**
5. **Notes Section**

### Image Formatting

- Format: `.webp` only
- Embed syntax: `![[image.webp|hs-med locr]]`
- **Important:** Always include the `|hs-med locr` sizing suffix
- Placement: Immediately after frontmatter

### Ingredients Section

```markdown
## Ingredients
servings: X servings

[For multi-part recipes, organize by component:]

**Component Name:**
- [ ] 1 ingredient
- [ ] 2 ingredient

[List special equipment if needed:]

**Special Equipment:** Item 1, Item 2
```

**Guidelines:**
- Start with `servings:` line
- Use checkboxes: `- [ ]` for each ingredient
- Organize complex recipes by component sections
- Include Special Equipment subsection if applicable

### Directions Section

```markdown
## Directions

[For multi-part recipes, organize by component:]

**Component Name:**

1. [ ] First step
2. [ ] Second step

[Include "Do Ahead" sections as needed]
```

**Guidelines:**
- Number all steps with checkboxes: `1. [ ]`
- Organize multi-component recipes by section
- Use exact text from source recipe (don't paraphrase)
- Include "Do Ahead" instructions for make-ahead components

### Notes Section

```markdown
## Notes

[Practical, actionable tips only]

- Storage instructions
- Technique clarifications
- Ingredient substitutions
- Make-ahead options

[Optional: Brief summary of flavor profile and composition]
```

**Guidelines:**
- Include only practical, actionable information
- Never include flavor text or author's stories
- Cover storage, technique, substitutions, and make-ahead options
- Can end with a brief summary of what makes the dish work
- Use bullet points or paragraph format as needed

---

## Title & Alias Convention

- **Title:** Use simplified, clean names when possible
  - Example: "Lasagna" instead of "BA's Best Lasagna"
- **Aliases:** If the original is different, preserve it here
  - Example: `aliases: - BA's Best Lasagna`

---

## Type Definitions

- **Main:** Entrée, primary dish of a meal
- **Side:** Accompaniment to main course
- **Dessert:** Sweet course
- **Drink:** Beverages
- **Base:** Component/ingredient recipe (stocks, sauces, dressings)
- **Condiment:** Topping or flavor enhancer

---

## Meal Categories

- **Breakfast:** Morning meal
- **Lunch:** Midday meal
- **Dinner:** Evening meal
- **Snack:** Light bite or appetizer

---

## Difficulty Levels

- **Easy:** Straightforward technique, minimal skill required
- **Medium:** Some technique or timing involved
- **Hard:** Complex, multi-step, or advanced technique

**Note:** Leave blank if difficulty is uncertain or not applicable (e.g., for condiments or bases).

---

## Date Added Convention

**Format:** YYYY-MM-DD (ISO 8601)

**Rule:** Always use the current date when creating a new recipe.

**Examples:**
- 2026-07-09 (July 9, 2026)
- 2026-12-25 (December 25, 2026)

---

## Frontmatter Preservation

When updating recipes:
- Never remove or modify existing YAML fields unless correcting errors
- Add new fields only when adding new recipes
- Preserve all original metadata (aliases, author, source, etc.)

---

## Quick Checklist for New Recipes

- [ ] YAML frontmatter complete (all required fields)
- [ ] Tags follow hierarchy rules (parent + child when applicable)
- [ ] No pantry staples tagged (sugar, vanilla, spices)
- [ ] Ingredient quantities meet tagging thresholds
- [ ] Image embedded with `|hs-med locr` sizing
- [ ] Ingredients organized by component if multi-part
- [ ] Directions use exact source text
- [ ] Notes include practical tips only (no flavor text)
- [ ] obsidianUIMode set to "preview"
- [ ] Date added is today's date in YYYY-MM-DD format
- [ ] Title simplified with original in aliases if needed

---

## Example Recipe Structure

See any recipe in `/Sync/food/recipes/` for a complete, formatted example following this ruleset.

Last Updated: 2026-07-09
