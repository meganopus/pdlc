---
description: HEAVY complexity feature addition — generates documentation suite consistent with the project kickoff heavy workflow.
---

# Add Feature Workflow (HEAVY)

This workflow is for adding new features or modules to an **enterprise, platform, regulated, or multi-team project**. It ensures consistent documentation standards for everything added post-kickoff.

## Layer Reference

Stories are decomposed **bottom-up** using the following layers. Layers without upstream dependencies can be worked in parallel.

```
L1 (Data Model) ──→ L3 (Backend / API) ──┐
                                          ├──→ L5 (Integration / E2E)
L2 (UI Foundation) ──→ L4 (Feature UI) ──┘
```

| Tag | Purpose | Depends On | Notes |
|-----|---------|------------|-------|
| `L1-data` | Schema, migrations, seed data | — | |
| `L2-ui-foundation` | Shared components, layouts, design tokens | — | Only if adding **new** shared components |
| `L3-backend` | API endpoints, services, business logic | L1 | |
| `L4-feature-ui` | Screens, pages, feature-specific UI | L2 | |
| `L5-integration` | E2E flows, cross-cutting wiring | L3 + L4 | |

> [!NOTE]
> **Not all layers apply to every project.** Use only the layers relevant to the project's tech stack (see `docs/tech-stack.md`). For backend-only projects, omit L2/L4. For frontend-only projects, omit L1/L3. The dependency graph adjusts accordingly.

## Step 1: Feature PRD Addendum

1.  **Read**: Load `skills/prd-generator/SKILL.md` for interview guidance.
2.  **Context**: Read the current `docs/prd.md`, `docs/erd/core-erd.md`, and `docs/api-standards.md` (if they exist) to understand the current product state.
3.  **Interview**: Follow the skill's data-gathering process, scoped to this specific feature.
4.  **Generate**: Execute the skill to produce `docs/features/[feature-name]/prd-addendum.md`.
    The addendum MUST include the following sections (omit a section only if truly not applicable, and state why):
    *   **Feature Requirements** — scope, user stories, acceptance criteria.
    *   **ERD Delta** — new or modified entities, attributes, and relationships vs. the Core ERD. Include a Mermaid ERD fragment.
    *   **API Contract** — new or modified endpoints for this feature, following the conventions in `docs/api-standards.md`. Include method, path, request/response shapes.
5.  **Discuss**: Walk the user through the addendum. If changes to the ERD or API contract are significant, highlight trade-offs explicitly.
6.  **Approve**: Stop and wait for explicit user approval. Do NOT auto-proceed.

## Step 2: Sprint Stories

1.  **Read**: Load `skills/story-generator/SKILL.md` for guidance.
2.  **Generate**: Execute the skill to break the feature into sprint-ready, estimated stories.
    *   **Layer-tag** each story using the Layer Reference above (`L1-data`, `L2-ui-foundation`, `L3-backend`, `L4-feature-ui`, `L5-integration`).
    *   **Mark dependencies** between stories (e.g., `depends: FEAT-001`).
    *   **Order bottom-up** — L1/L2 stories first, then L3/L4, then L5.
    *   **Skip Scaffold**: Since the project is already active, skip project initialization tasks. Only include L2 stories if the feature requires **new** shared components.
3.  **Output**: Create story files at `docs/features/[feature-name]/stories/`.
    *   Each story in its own markdown file (e.g., `FEAT-001-schema.md`).
    *   Generate `docs/features/[feature-name]/stories/dependency-graph.md` containing a **Mermaid dependency diagram** showing the relationships between stories.

    Example dependency graph:
    ```mermaid
    graph TD
        FEAT-001["FEAT-001: Schema (L1)"] --> FEAT-003["FEAT-003: List API (L3)"]
        FEAT-002["FEAT-002: Shared Card (L2)"] --> FEAT-004["FEAT-004: Detail Page (L4)"]
        FEAT-003 --> FEAT-005["FEAT-005: E2E Flow (L5)"]
        FEAT-004 --> FEAT-005
    ```
4.  **Approve**: Stop and wait for explicit user approval. Do NOT auto-proceed. If revisions are requested, regenerate and STOP again for approval.

## Step 3: Global Artifacts Integration

1.  **Objective**: Merge feature-specific artifacts back into the core documentation to maintain a single **cohesive** source of truth.
2.  **Merge ERD Delta** *(if applicable)*:
    *   **Input**: The ERD Delta section from `docs/features/[feature-name]/prd-addendum.md` and the current `docs/erd/core-erd.md`.
    *   **Action**: Integrate new/modified entities into the Core ERD.
    *   **CRITICAL**: Validate that no existing relationships are broken. Flag conflicts for user review.
3.  **Merge API Contracts** *(if applicable)*:
    *   **Input**: The API Contract section from the addendum and existing `docs/api/contracts/`.
    *   **Action**: Add new endpoints to the contract specs. Ensure consistency with `docs/api-standards.md`.
4.  **Refactor Global PRD**:
    *   **Input**: `docs/features/[feature-name]/prd-addendum.md` and the current `docs/prd.md`.
    *   **Action**: Integrate the new feature requirements into the Global PRD.
    *   **CRITICAL**: Do NOT just append the addendum as a new section. You must **REFACTOR** the Global PRD to weave the new feature seamlessly into the existing narrative and structure.
5.  **Update Global Dependency Graph**:
    *   **Input**: Scan ALL story files in `docs/features/*/stories/*.md`.
    *   **Action**: Integrate the stories into `docs/dependency-graph.md`, maintaining the Mermaid diagram showing ALL stories and their dependencies.
    *   **Visualization**: Use different shapes/colors for completed vs. pending stories if possible.
6.  **Approve**: Wait for explicit user approval. Do NOT auto-proceed after integration.

---

# Completion

*   Notify the user that feature documentation is complete.
*   Provide a summary of files created and their locations.
*   Remind user that the **Global Dependency Graph** in `docs/dependency-graph.md` shows the recommended build order across all features.
*   Remind user that ERD and API changes are explicit, audited, and merged back into global artifacts.
