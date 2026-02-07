---
description: An interactive interview workflow to generate Wireframes.
---

# Create Wireframes Workflow

This workflow guides you through an interactive interview process to generate UI/UX Wireframe descriptions.

## Steps

1.  **Initiate Interview**: Focus on the User Interface and User Experience.
    *   *Question*: "What are the key screens or views required for this application? Please walk me through the primary user flow."
2.  **Gather Details**: For each identified screen, dig deeper.
    *   **Screen Purpose**: What is the main goal of this screen?
    *   **Data Requirements**: What specific data needs to be displayed? (e.g., user profile, transaction list, charts)
    *   **Actions**: What actions can the user perform? (e.g., add new item, filter, export, edit)
    *   **Layout Preferences**: Any specific layout requirements? (e.g., dashboard style, list view, sidebar navigation)
    *   **States**: Are there specific states to consider? (e.g., empty state, loading, error, success)
3.  **Refine & Confirm**:
    *   Review the list of screens to be generated.
    *   *Question*: "I have captured the following screens: [List]. detailed needs for each... Is this complete? Are there any missing flows?"
4.  **Generate**: Use the `wireframe-generator` skill to generate the wireframes.
    *   *Action*: Execute `skills/wireframe-generator/SKILL.md` with the gathered information.
    *   *Command*: `view_file skills/wireframe-generator/SKILL.md` (to read instructions) then generate content.

## Completion

*   Notify the user that the Wireframes have been generated.
*   Provide the file location and a summary of screens covered.
