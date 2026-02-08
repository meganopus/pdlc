---
description: LIGHT complexity project kickoff — fast, lean documentation for startups, MVPs, internal tools, and fast-iteration projects.
---

# Project Kickoff Workflow (LIGHT)

This workflow is for **startups, MVPs, internal tools, and fast-iteration projects** where speed and learning are prioritized over ceremony. Documentation follows development, not blocks it.

## When to Use LIGHT

Use this workflow if ALL of the following apply:
- Single team or small team
- Internal or limited external API consumers
- Rapid iteration expected
- No heavy compliance requirements
- Simple or evolving data model

---

# Global Artifacts (Lightweight, Once)

These are created **once** in a lean format.

## Step 1: Product Brief (Lightweight)

1.  **Interview**: Quick product overview.
    *   *Question*: "What is the product, who is it for, and what problem does it solve?"
2.  **Generate**: 1-page Product Brief via `skills/product-brief/SKILL.md`.

## Step 2: PRD (Lean, Outcome-Focused)

1.  **Interview**: Focus on outcomes, not exhaustive requirements.
    *   *Question*: "What are the 3-5 key outcomes this product must achieve?"
2.  **Generate**: Lean PRD via `skills/prd-generation/SKILL.md` (short mode if available).

## Step 3: Design System (Basic or Borrowed)

1.  **Interview**: Quick visual direction.
    *   *Question*: "Are you using an existing design system (e.g., Tailwind, Material)? If not, describe the vibe in 3 words."
2.  **Generate**: Basic tokens via `skills/design-system/SKILL.md` or reference existing framework.

## Step 4: API Guidelines (Not Full Contracts)

1.  **Interview**: Minimal API conventions.
    *   *Question*: "What auth method (JWT, API key)? What's your error format?"
2.  **Document**: Brief `docs/api-guidelines.md` (1 page max).

---

# Per-Feature Artifacts (Merged & Fast)

Documentation is streamlined — FSD and TDD are **combined**.

## Step 5: Feature Epic + Key User Stories

1.  **Interview**: High-level feature scope and user needs.
    *   *Question*: "What is the feature and what are the 3-5 key user stories?"
2.  **Generate**: Create `docs/features/[feature-name]/epic-and-stories.md`.

## Step 6: UI Wireframes

1.  **Interview**: Key screens only.
    *   *Question*: "What are the 2-3 critical screens for this feature?"
2.  **Generate**: Execute `skills/wireframe-generator/SKILL.md`.

## Step 7: API Contract (Only if External/Critical)

1.  **Check**: Is this API consumed externally or is it critical?
    *   If **No**: Skip this step. Document endpoints inline in the Tech Spec.
    *   If **Yes**: Create `docs/features/[feature-name]/api-contract.md`.

## Step 8: Combined FSD + TDD (Tech Spec)

This is the core document — **FSD and TDD merged into one**.

1.  **Interview**: Functional and technical details together.
    *   *Question*: "Walk me through the feature flow and any technical considerations."
2.  **Gather Details**:
    - Key functional flows and business rules.
    - Data model changes (inline, not separate ERD doc).
    - API endpoints (inline if not external).
    - Technical approach (architecture, patterns).
3.  **Generate**: Execute `skills/tdd-generator/SKILL.md` in **LIGHT mode**.
    *   Output: `docs/features/[feature-name]/tech-spec.md` (~3 pages).

## Step 9: Sprint Stories

1.  **Generate**: Break Tech Spec into sprint-ready stories.
2.  **Output**: Append to or create `docs/features/[feature-name]/stories.md`.

---

# Completion

*   Notify the user that documentation is complete.
*   Provide a summary of files created.
*   Remind user: Documentation follows development here — iterate as you build.
