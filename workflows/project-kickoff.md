---
description: An interactive interview workflow to generate Product Brief, Design System, Wireframes, and TDD.
---

# Project Kickoff Interview Workflow

This workflow guides you through an interactive interview process to generate a complete project documentation suite: Product Brief, Design System, Wireframes, and Technical Design Document (TDD).

## Phase 1: Product Brief

1.  **Initiate Interview**: Start by asking the user for a high-level overview of their product idea.
    *   *Question*: "What is the name of your product and what is its primary purpose? Who is the target audience?"
2.  **Gather Details**: Continue asking clarifying questions to cover all sections of a Product Brief:
    *   Problem being solved and the proposed solution.
    *   Key features and capabilities.
    *   Business model and competitive advantage.
    *   Success metrics.
3.  **Confirm**: Summarize your understanding and ask the user to confirm.
    *   *Question*: "Here is my understanding of the product... [Summary]. Is this accurate? effective immediately, please let me know if there are any changes."
4.  **Generate**: Once confirmed, use the `product-brief` skill to generate the document.
    *   *Action*: Execute `skills/product-brief/SKILL.md` with the gathered information.
    *   *Command*: `view_file skills/product-brief/SKILL.md` (to read instructions) then generate content.

## Phase 2: Design System

1.  **Initiate Interview**: Ask about the visual identity.
    *   *Question*: "Now let's define the visual language. Do you have an existing brand guide? If not, how would you describe the desired look and feel (e.g., modern, playful, corporate, dark/light mode)?"
2.  **Gather Details**:
    *   Primary and secondary colors.
    *   Typography preferences (Serif/Sans-serif, specific fonts).
    *   Key UI component styles (rounded corners, shadows, flat, etc.).
    *   Accessibility requirements.
3.  **Confirm**: Summarize the design direction.
4.  **Generate**: Use the `design-system` skill.
    *   *Action*: Execute `skills/design-system/SKILL.md`.

## Phase 3: Wireframes

1.  **Initiate Interview**: Transition to User Interface design.
    *   *Question*: "Based on the Product Brief, let's detail the key screens. Please walk me through the primary user flow step-by-step."
2.  **Gather Details**:
    *   Identify the key screens needed (e.g., Dashboard, Login, Settings, Detail View).
    *   For each screen, ask: "What data needs to be displayed here? What actions can the user take?"
    *   *Crucial Step*: Since we might not have a formal FSD or ERD yet, ask enough questions to infer the data model and API requirements needed for the wireframe generator.
    *   *Question*: "For the [Screen Name], what specific information fields are required?"
3.  **Refine**: Ensure there are no ambiguities about layout preferences (e.g., sidebar vs. top nar, card view vs. table view).
4.  **Confirm**: List the screens to be generated and ask for approval.
5.  **Generate**: Use the `wireframe-generator` skill.
    *   *Action*: Execute `skills/wireframe-generator/SKILL.md`.

## Phase 4: Technical Design Document (TDD)

1.  **Initiate Interview**: Discuss technical implementation.
    *   *Question*: "Final step is the technical design. Do you have specific technology preferences for the frontend, backend, and database?"
2.  **Gather Details**:
    *   Architecture pattern (Monolith, Microservices, Serverless).
    *   Authentication strategy (OAuth, JWT, etc.).
    *   Hosting/Deployment preferences (AWS, Vercel, Docker).
    *   Performance and scalability requirements.
3.  **Confirm**: Summarize the technical stack and architecture.
4.  **Generate**: Use the `tdd-generator` (or `tdd-lite-generator` for smaller projects) skill.
    *   *Action*: Execute `skills/tdd-generator/SKILL.md`.

## Completion

*   Notify the user that all documents have been generated.
*   Provide a summary of the files created and their locations.
