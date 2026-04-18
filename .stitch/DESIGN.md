# Design System Specification: The Organic Authority

## 1. Overview & Creative North Star
**The Creative North Star: "The Digital Arboretum"**
This design system moves beyond the standard "NGO Template" to create a high-end editorial experience that mirrors the complexity and resilience of rural ecosystems. It rejects the "flatness" of modern SaaS design in favor of **Organic Brutalism**—a style that combines rigid, authoritative structures (academic/corporate) with fluid, layered transitions (nature/growth).

The system is defined by three pillars:
*   **Structured Depth:** Using hexagonal motifs and geometric overlays to represent interconnected nodes of data.
*   **Intentional Asymmetry:** Breaking the standard 12-column grid with overlapping elements to create a sense of movement and organic life.
*   **Tonal Authority:** Relying on deep, saturated greens and blues to establish trust, using high-contrast typography to ensure academic clarity.

---

## 2. Colors & Surface Logic
The palette is rooted in the earth but elevated by digital vibrancy. We move away from lines and borders, using color as the primary architect of space.

### The "No-Line" Rule
**Explicit Instruction:** Do not use 1px solid borders to define sections or containers. 
*   **Boundary Definition:** Sections must be delineated by shifts in background color (e.g., a `surface-container-low` section transitioning into a `primary-container` section). 
*   **Ghost Borders:** If a boundary is essential for accessibility, use `outline-variant` at 15% opacity maximum.

### Surface Hierarchy & Nesting
Treat the interface as a physical stack of materials. 
*   **Base:** `surface` (#f8faf8) – The canvas.
*   **Low Tier:** `surface-container-low` (#f2f4f2) – Used for subtle content grouping.
*   **Interactive Tier:** `surface-container-lowest` (#ffffff) – Used for cards that need to "pop" from the background.
*   **Glassmorphism:** For floating elements or utility bars, use `surface-variant` at 80% opacity with a `24px` backdrop-blur to allow the rich greens and nature textures to bleed through.

### Signature Gradients
To avoid a "flat" corporate feel, use subtle radial gradients on Primary CTAs:
*   **Primary Action:** Linear gradient from `primary` (#022c01) to `primary-container` (#1a4314) at 135 degrees.

---

## 3. Typography: The Editorial Voice
We utilize a pairing of **Manrope** for impact and **Inter** for precision.

| Level | Token | Font | Size | Weight | Use Case |
| :--- | :--- | :--- | :--- | :--- | :--- |
| **Display** | `display-lg` | Manrope | 3.5rem | 700 | Hero headlines; high-impact storytelling. |
| **Headline** | `headline-md` | Manrope | 1.75rem | 600 | Section headers; academic resource titles. |
| **Title** | `title-md` | Inter | 1.125rem | 600 | Card titles; navigation labels. |
| **Body** | `body-lg` | Inter | 1rem | 400 | Standard reading; reports and success stories. |
| **Label** | `label-md` | Inter | 0.75rem | 500 | Metadata; tags; utility bar items. |

**The Hierarchy Strategy:** Headline styles use tighter letter-spacing (-0.02em) to feel "heavy" and authoritative, while Body text uses standard spacing for maximum legibility in long-form resource documents.

---

## 4. Elevation & Depth
Depth is achieved through **Tonal Layering** rather than structural shadows.

*   **The Layering Principle:** Instead of a shadow, place a `surface-container-lowest` card on top of a `surface-container-low` background. This creates a "soft lift."
*   **Ambient Shadows:** For floating hexagons or sticky headers, use: `box-shadow: 0 20px 40px rgba(25, 28, 27, 0.06);`. This mimics natural light filtered through a canopy.
*   **Hexagonal Visual Motifs:** Use the hexagonal shape as a masking container for imagery or as a subtle background watermark using the `outline-variant` token. Hexagons should overlap slightly to suggest "Interconnected Nodes."

---

## 5. Components

### Utility Bar & Sticky Header
*   **Utility Bar:** `surface-container-high` (#e6e9e7). High-density text using `label-sm`.
*   **Header:** Fixed position. Use `surface` (#f8faf8) with a 90% opacity and `blur(12px)`. No bottom border; use a very soft ambient shadow on scroll.

### Primary & Secondary Buttons
*   **Primary:** `primary` (#022c01) background, `on-primary` (#ffffff) text. `0.375rem` (md) corner radius.
*   **Secondary:** `surface-container-highest` background. No border. Text in `on-surface`.
*   **Interaction:** On hover, the primary button shifts to `primary-container` with a subtle increase in the ambient shadow.

### Hexagonal Cards (The Node Pattern)
*   For success stories, use a modular grid where cards are not simple rectangles.
*   **Visual Style:** Use a `surface-container-lowest` background. 
*   **Interconnection:** Use a `0.5px` dashed line using `outline-variant` to "connect" the centers of adjacent cards, reinforcing the "Nexus" concept.
*   **Constraint:** No dividers. Use `2.5rem` (40px) of vertical padding to separate content blocks.

### Organizational Accordion (Hierarchical Tree)
*   Use for complex resource structures.
*   **State Change:** An open accordion item should shift the background to `surface-container-low`, creating an "inset" feel.
*   **Iconography:** Use `tertiary` (Amber) for expand/collapse icons to guide the eye to interactive nodes.

---

## 6. Do’s and Don’ts

### Do:
*   **Do** overlap image containers over background color shifts to create a "layered" look.
*   **Do** use `tertiary-fixed` (Amber) sparingly—only for high-priority interactive elements or critical data points.
*   **Do** use nature-textured backgrounds (subtle soil/leaf patterns) as overlays on `primary-container` sections using `multiply` blend mode at 5-10% opacity.

### Don’t:
*   **Don’t** use pure black (#000000) for text. Always use `on-surface` (#191c1b) to maintain a premium, soft-contrast feel.
*   **Don’t** use standard "drop shadows" on cards. Rely on color shifts between `surface` tiers first.
*   **Don’t** use sharp corners. Always follow the `md` (0.375rem) or `lg` (0.5rem) roundedness scale to keep the "Organic" feel.
*   **Don't** clutter the grid. If a section feels crowded, increase the vertical whitespace rather than adding a divider line.

---

## 7. Signature Footer
*   **Background:** `primary-container` (#1a4314).
*   **Structure:** Multi-column layout with high-contrast `on-primary-fixed` text.
*   **Visual Element:** A large, cropped hexagonal "Nexus" watermark in the bottom-right corner, using a slightly lighter green (`on-primary-container`) at 5% opacity.
