---
description: An interactive interview workflow to generate a Technical Design Document (TDD).
---

# Create TDD Workflow

This workflow guides you through an interactive interview process to generate a Technical Design Document (TDD).

## Steps

1.  **Initiate Interview**: Focus on the technical implementation details.
    *   *Question*: "What is the scope of the technical design? Do you have existing technical constraints or technology preferences?"
2.  **Gather Details**: Discuss the technical stack and architecture.
    *   **Frontend**: Framework (React, Vue, etc.), State Management, Styling solution.
    *   **Backend**: Language/Framework (Node, Python, Go, etc.), API style (REST, GraphQL).
    *   **Database**: Type (SQL, NoSQL), Specific technology (PostgreSQL, MongoDB).
    *   **Architecture**: Monolith, Microservices, Serverless?
    *   **Infrastructure**: Cloud provider (AWS, Azure, GCP), Deployment strategy (Docker, K8s).
    *   **Security**: Authentication capabilities, Data protection needs.
    *   **Performance**: Scalability requirements, Expected load.
3.  **Refine & Confirm**:
    *   Summarize the technical decisions.
    *   *Question*: "Based on our discussion, here is the proposed technical stack and architecture... [Summary]. Is this correct?"
4.  **Generate**: Use the `tdd-generator` skill to generate the document.
    *   *Action*: Execute `skills/tdd-generator/SKILL.md` with the gathered information.
    *   *Command*: `view_file skills/tdd-generator/SKILL.md` (to read instructions) then generate content.

## Completion

*   Notify the user that the Technical Design Document has been generated.
*   Provide the file location.
