---
description: An interactive interview workflow to generate a Product Brief.
---

# Create Product Brief Workflow

This workflow guides you through an interactive interview process to generate a comprehensive Product Brief.

## Steps

1.  **Initiate Interview**: Start by asking the user for a high-level overview of their product idea.
    *   *Question*: "What is the name of your product and what is its primary purpose? Who is the target audience?"
2.  **Gather Details**: Continue asking clarifying questions to cover all sections of a Product Brief. Ensure you cover:
    *   **Problem & Solution**: What specific problem does it solve and how?
    *   **Key Features**: What are the core capabilities?
    *   **Business Model**: How will it make money or sustain itself?
    *   **Competitive Landscape**: Who are the competitors and what makes this product unique?
    *   **Success Metrics**: How will success be measured?
    *   **Status**: What is the current stage of the project?
3.  **Refine & Confirm**:
    *   Ask if there are any specific constraints or strategic goals to include.
    *   Summarize your understanding of the product.
    *   *Question*: "Does this summary accurately reflect your product vision? Is there anything you'd like to add or change?"
4.  **Generate**: Once confirmed, use the `product-brief` skill to generate the document.
    *   *Action*: Execute `skills/product-brief/SKILL.md` with the gathered information.
    *   *Command*: `view_file skills/product-brief/SKILL.md` (to read instructions) then generate content.

## Completion

*   Notify the user that the Product Brief has been generated.
*   Provide the file location.
