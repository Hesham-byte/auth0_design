# Design System Strategy: The Cognitive Sanctuary

This design system is built to transform the "AI Homework Helper" from a mere utility into a **Cognitive Sanctuary**. We are moving away from the cluttered, grid-heavy aesthetics of traditional EdTech. Instead, we are adopting a high-end editorial approach that balances the "Smart" (high-tech, AI-driven) with the "Secure" (private, safe, nurturing).

## 1. Creative North Star: "The Digital Mentor"
The interface should feel like a premium, physical workspace—think high-quality paper, frosted glass partitions, and focused lighting. We break the "template" look through **intentional asymmetry**: placing key actions slightly off-center or overlapping elements to create a sense of organic movement. This design system prioritizes breathing room (whitespace) and tonal depth over rigid lines.

---

## 2. Color & Surface Architecture
We use color not just for decoration, but to define the "Sanctuary."

### The "No-Line" Rule
**Explicit Instruction:** You are prohibited from using 1px solid borders to section content. Boundaries must be defined solely through background color shifts or subtle tonal transitions. 
*   *Example:* A list item should not have a bottom border. It should sit on a `surface-container-low` background, perhaps shifting to `surface-container-high` on hover.

### Surface Hierarchy & Nesting
Treat the UI as a series of physical layers. Use the Material tiers to "nest" importance:
1.  **Base Layer:** `surface` (#f8f9fb) – The canvas.
2.  **Sectioning:** `surface-container-low` (#f2f4f6) – Large layout blocks.
3.  **Interaction Hubs:** `surface-container-lowest` (#ffffff) – Where the student types or reads.
4.  **Prominent Overlays:** `surface-container-highest` (#e0e3e5) – Used sparingly for "Secure Vault" panels or AI-suggested hints.

### The "Glass & Gradient" Rule
To elevate the "Smart" aspect of the AI, use **Glassmorphism** for floating elements. Apply `surface-container-lowest` at 70% opacity with a `backdrop-filter: blur(12px)`.
*   **Signature Texture:** Main CTAs should use a subtle linear gradient from `primary` (#2b3896) to `primary-container` (#4551af) at a 135-degree angle. This provides a "soul" to the action that flat indigo cannot achieve.

---

## 3. Typography: The Editorial Voice
We use a dual-font strategy to balance authority with approachability.

*   **Display & Headlines (Manrope):** This is our "Editorial" voice. Use `display-lg` and `headline-md` with tighter letter-spacing (-2%) to create a sophisticated, high-tech look for welcome messages and progress titles.
*   **Body & Labels (Inter):** This is our "Utility" voice. Highly legible and neutral. Use `body-lg` for AI-generated explanations to ensure zero eye strain for students.
*   **The Hierarchy Goal:** Use dramatic size contrasts. A `display-sm` headline paired with a `label-md` sub-header creates a professional, intentional layout that feels "designed," not just "filled."

---

## 4. Elevation & Depth
In this system, depth is felt, not seen.

*   **Tonal Layering:** Achieve "lift" by stacking tones. A `surface-container-lowest` card placed on a `surface-container-low` background creates a natural, soft lift without a single shadow.
*   **Ambient Shadows:** If an element must float (like a "Secure Token Vault" modal), use a tinted shadow: `0px 20px 40px rgba(43, 56, 150, 0.06)`. By tinting the shadow with our `primary` blue, it feels like natural light interacting with the interface.
*   **The "Ghost Border" Fallback:** If accessibility requires a container edge, use the `outline-variant` (#c5c5d4) at **15% opacity**. Never use a 100% opaque border.

---

## 5. Signature Components

### The Secure Vault (Security Identity)
To emphasize the **Auth0 Secure Token Vault**, use the `secondary` (#006a63) tokens. Security shouldn't feel "alarming" (red) or "boring" (gray); it should feel "calm" (teal).
*   Use a `secondary-container` (#8bf1e6) background for security-related notifications.
*   Incorporate a subtle "shield" icon using the `on-secondary-container` (#006f67) color.

### Buttons (The Kinetic Set)
*   **Primary:** Gradient of `primary` to `primary-container`. `xl` (1.5rem) roundedness.
*   **Secondary:** `surface-container-highest` background with `on-surface` text. No border.
*   **Interactive State:** On hover, a button should not just get darker; it should "grow" slightly (transform: scale(1.02)) and increase shadow diffusion to mimic being pulled toward the student.

### AI Interaction Cards
*   Forbid dividers. Use `spacing-8` (2rem) of vertical white space to separate the AI's response from the student's question.
*   Apply a `surface-variant` left-aligned accent bar (4px width) to AI responses to denote "Generated Insight" without boxing the text in.

### Inputs & Fields
*   **The Focus State:** When a student clicks into a homework input, the background should shift from `surface-container-low` to `surface-container-lowest`, and a "Ghost Border" of `primary` at 30% opacity should fade in.

---

## 6. Do’s and Don’ts

### Do:
*   **Do** use asymmetrical layouts (e.g., a wide left column for content and a narrow, floating right column for the "Secure Vault" status).
*   **Do** use the `xl` (1.5rem) roundedness for main container cards to make the tech feel friendly to students.
*   **Do** use `tertiary-fixed` (#ffdeac) for progress highlights—it's the "Warm Orange" that signals success and movement.

### Don’t:
*   **Don’t** use black (#000000) for text. Always use `on-surface` (#191c1e) to maintain a premium, soft-contrast look.
*   **Don’t** use traditional "Card" shadows on every element. If everything floats, nothing is important.
*   **Don’t** use 90-degree corners. Everything in a student's world should feel safe and "rounded."
*   **Don’t** use dividers. If you feel the need to separate two things, increase the spacing token (e.g., move from `spacing-4` to `spacing-8`).

By adhering to these editorial principles, you will create an experience that doesn't just help with homework—it creates a secure, premium environment where students feel empowered and protected.