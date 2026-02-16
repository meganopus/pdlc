---
description: HEAVY complexity project kickoff — generates full documentation suite for enterprise, platform, regulated, or multi-team projects.
---

# Project Kickoff Workflow (HEAVY)

This workflow is for **enterprise, platform, regulated, or multi-team projects** where predictability and scale are critical. Each feature is independently deployable and documentation is versioned.

## When to Use HEAVY

Use this workflow if ANY of the following apply:
- Multi-team project
- External API consumers
- Regulated or compliance-heavy domain
- Data model changes affecting multiple services
- Long-lived platform with multiple stakeholders

---

# Global Artifacts (Once Per Project)

These are created **once** and governed centrally.

## Step 1: PRD (Signed-Off)

1.  **Read**: Load `skills/prd-generator/SKILL.md` for interview guidance.
2.  **Interview**: Follow the skill's data-gathering process to collect requirements, user stories, acceptance criteria, constraints, and dependencies.
3.  **Confirm**: Require explicit sign-off before proceeding.
4.  **Generate**: Execute the skill to produce the PRD.
5.  **Approve**: Stop and wait for explicit user approval. Do NOT auto-proceed.

## Step 2: Functional Specification Document (FSD)

1.  **Read**: Load `skills/fsd-generator/SKILL.md` for interview guidance.
2.  **Interview**: Follow the skill's data-gathering process to collect detailed functional flows and business rules.
3.  **Generate**: Execute the skill to produce `docs/features/[feature-name]/fsd.md`.
4.  **Approve**: Stop and wait for explicit user approval. Do NOT auto-proceed.

## Step 3: Tech Stack & Architecture Decision

1.  **Read**: Load `skills/tech-stack/SKILL.md` for interview guidance.
2.  **Interview**: Follow the skill's data-gathering process to collect application type, team expertise, frontend/backend frameworks, database, auth strategy, hosting/infra, CI/CD, and third-party integrations.
3.  **Confirm**: Summarize stack choices and trade-offs.
4.  **Generate**: Execute the skill to produce `docs/tech-stack.md`.
5.  **Approve**: Stop and wait for explicit user approval. Do NOT auto-proceed.

## Step 4: Design System

1.  **Read**: Load `skills/design-system/SKILL.md` for interview guidance.
2.  **Interview**: Follow the skill's data-gathering process to collect brand identity, colors, typography, component styles, and accessibility requirements.
3.  **Confirm**: Summarize the design direction.
4.  **Generate**: Execute the skill to produce the Design System.
5.  **Approve**: Stop and wait for explicit user approval. Do NOT auto-proceed.

## Step 5: Core ERD  [Optional, ask user if they want to do this]

> [!IMPORTANT]
> **Why this matters for HEAVY projects:**
> Skipping this step often leads to "data silos" where different features duplicate data inconsistently. A unified ERD is critical for reporting, analytics, and maintaining data integrity across a large system.

1.  **Read**: Load `skills/erd-generator/SKILL.md` for interview guidance.
2.  **Interview**: Follow the skill's data-gathering process to collect core entities, attributes, relationships, cardinalities, and constraints.
3.  **Confirm**: Review entity diagram.
4.  **Generate**: Execute the skill to produce `docs/erd/core-erd.md` with Mermaid ERD.
5.  **Approve**: Stop and wait for explicit user approval. Do NOT auto-proceed.

## Step 6: Core API Standards & Contract Governance [Optional, ask user if they want to do this]

> [!IMPORTANT]
> **Why this matters for HEAVY projects:**
> Inconsistent APIs are the #1 cause of "integration hell" in multi-team projects. Defining standards and contracts upfront allows frontend and backend teams to work independently without blocking each other.

1.  **Interview**: Define platform-wide API conventions.
    *   *Question*: "What are your standards for authentication, error handling, versioning, and rate limiting?"
2.  **Document Standards**: Create `docs/api-standards.md` covering:
    - Auth flow (OAuth, JWT, API keys)
    - Error response format
    - Versioning strategy
    - Rate limiting policy
3.  **Generate Contracts**:
    *   **Objective**: Allow frontend and backend teams to work in parallel.
    *   **Action**: Generate OpenAPI/Swagger specifications based on the FSD and Data Model.
    *   **Output**: Create `docs/api/contracts/` containing the spec files (e.g., `openapi.yaml`).
4.  **Approve**: Wait for explicit user approval. Do NOT auto-proceed after generating contracts.

---

# Per-Feature Artifacts (Repeat Per Feature)

These are created **for each feature or module**.

## Layer Reference

Stories are decomposed **bottom-up** using the following layers. Layers without upstream dependencies can be worked in parallel.

```
L1 (Data Model) ──→ L3 (Backend / API) ──┐
                                          ├──→ L5 (Integration / E2E)
L2 (UI Foundation) ──→ L4 (Feature UI) ──┘
```

| Tag | Purpose | Depends On | Notes |
|-----|---------|------------|-------|
| `L1-data` | Schema, migrations, seed data | — | *First feature: includes project scaffold* |
| `L2-ui-foundation` | Shared components, layouts, design tokens | — | *First feature: includes UI init* |
| `L3-backend` | API endpoints, services, business logic | L1 | |
| `L4-feature-ui` | Screens, pages, feature-specific UI | L2 | |
| `L5-integration` | E2E flows, cross-cutting wiring | L3 + L4 | |

> [!NOTE]
> **Not all layers apply to every project.** Use only the layers relevant to the project's tech stack (see `docs/tech-stack.md`). For backend-only projects, omit L2/L4. For frontend-only projects, omit L1/L3. The dependency graph adjusts accordingly.

## Step 7: Feature PRD Addendum

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

## Step 8: Sprint Stories

1.  **Read**: Load `skills/story-generator/SKILL.md` for guidance.
2.  **Generate**: Execute the skill to break the feature into sprint-ready, estimated stories.
    *   **Layer-tag** each story using the Layer Reference above (`L1-data`, `L2-ui-foundation`, `L3-backend`, `L4-feature-ui`, `L5-integration`).
    *   **Mark dependencies** between stories (e.g., `depends: FEAT-001`).
    *   **Order bottom-up** — L1/L2 stories first, then L3/L4, then L5.
    *   **First feature only**: include scaffold / init tasks within L1 and L2 stories.
    *   **Subsequent features**: skip scaffold. Only include L2 stories if the feature requires **new** shared components.
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

## Step 9: Global Artifacts Integration

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
5.  **Approve**: Wait for explicit user approval. Do NOT auto-proceed after integration.

---

# Completion

*   Notify the user that all documents have been generated.
*   Provide a summary of files created and their locations.
*   Remind user that the **dependency graph** in `stories/dependency-graph.md` shows the recommended build order.
*   Remind user that ERD and API changes are explicit, audited, and merged back into global artifacts.
