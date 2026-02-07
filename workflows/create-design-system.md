---
description: An interactive interview workflow to generate a Design System.
---

# Create Design System Workflow

This workflow guides you through an interactive interview process to generate a Design System documentation.

## Steps

1.  **Initiate Interview**: Ask about the visual identity and brand guidelines.
    *   *Question*: "Do you have an existing brand guide or visual identity? If not, how would you describe the desired look and feel (e.g., modern, playful, corporate, minimalist)?"
2.  **Gather Details**: Drill down into specific design elements.
    *   **Colors**: What are the primary, secondary, and accent colors? Any specific hex codes or preferences?
    *   **Typography**: What font families should be used for headings and body text? (e.g., Serif, Sans-serif, Monospace)
    *   **Spacing & Layout**: Do you prefer a spacious design or a dense information-rich layout?
    *   **UI Components**: Any specific preferences for buttons (rounded, sharp), cards (shadows, borders), and inputs?
    *   **Iconography**: What style of icons? (e.g., solid, outline, dual-tone)
    *   **Dark Mode**: Should the system support dark mode?
3.  **Refine & Confirm**:
    *   Summarize the design decisions.
    *   *Question*: "Here is the proposed design direction... [Summary]. Does this align with your vision?"
4.  **Generate**: Use the `design-system` skill to generate the document.
    *   *Action*: Execute `skills/design-system/SKILL.md` with the gathered information.
    *   *Command*: `view_file skills/design-system/SKILL.md` (to read instructions) then generate content.

## Completion

*   Notify the user that the Design System documentation has been generated.
*   Provide the file location.
