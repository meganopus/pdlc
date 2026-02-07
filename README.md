# Prompter Skills

A [Mountd](https://github.com/meganopus/mountd) compatible comprehensive collection of professional-grade AI skills and workflows based off [Propmpter](https://github.com/Dedesfr/Prompter). These skills help you generate high-quality project documentation, from Product Briefs to Technical Design Documents.

## Usage

### Using with Mountd

You can use these skills directly with `mountd` without installing anything globally.

```bash
# Run the interactive project kickoff interview
npx mountd meganopus/Prompter

# Or if you have the repo cloned locally
npx mountd
```

### Available Workflows

This repository includes interactive workflows that act as an "Interview Mode" to guide you through document creation.

- **🚀 Project Kickoff** (`project-kickoff`): A comprehensive end-to-end interview that generates a Product Brief, Design System, Wireframes, and TDD in one go.
- **📄 Create Product Brief** (`create-product-brief`): Generates a high-level executive summary and product definition.
- **🎨 Create Design System** (`create-design-system`): Defines your visual identity, tokens, and components.
- **📐 Create Wireframes** (`create-wireframes`): Generates detailed UI/UX wireframe descriptions.
- **⚙️ Create TDD** (`create-tdd`): Generates a complete Technical Design Document.

## Skills

This repository contains the following individual skills that can be used via `mountd` or manually:

| Skill | Description |
|-------|-------------|
| **ai-humanizer** | Refine content to be conversational, friendly, and undetectable as AI. |
| **api-contract-generator** | Generate OpenAPI/Swagger API contracts from PRDs. |
| **design-system** | Create a comprehensive design system with tokens, components, and guidelines. |
| **document-explainer** | Explain complex documents or code in simple terms. |
| **epic-generator** | Generate detailed Epics from high-level requirements. |
| **epic-single** | Generate a single, detailed Epic. |
| **erd-generator** | Create Entity Relationship Diagrams (ERD). |
| **fsd-generator** | Generate a Functional Specification Document (FSD). |
| **prd-agent-generator** | Create a PRD specifically for AI Agents. |
| **prd-generator** | Generate a comprehensive PRD for software features. |
| **product-brief** | Create a high-level Product Brief. |
| **qa-test-scenario** | Generate comprehensive QA test scenarios. |
| **skill-creator** | Create a new skill for the Prompter system. |
| **story-generator** | Generate detailed User Stories. |
| **story-single** | Generate a single, detailed User Story. |
| **tdd-generator** | Generate a Test-Driven Development (TDD) plan. |
| **tdd-lite-generator** | Generate a lightweight TDD plan. |
| **wireframe-generator** | Create wireframe descriptions for UI visualization. |

## License

MIT
