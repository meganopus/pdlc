# PDLC

**Stop hallucinating architecture. Start shipping with clarity.**

PDLC gives your AI coding assistant a structured kickoff workflow that transforms vague ideas into production-ready documentation—Product Briefs, PRDs, Design Systems, ERDs, and TDDs—before a single line of code is written.

## ⚡ Quick Start

```bash
# Install the kickoff bundle that fits your project
npx mountd add meganopus/pdlc kickoff-light-bundle  # For MVPs & startups
npx mountd add meganopus/pdlc kickoff-heavy-bundle  # For enterprise projects

# Then run the interactive kickoff workflow
/project-kickoff-light   # or /project-kickoff-heavy
```

## 🎯 Why Kickoff Bundles?

AI coding assistants are powerful, but they often start building before understanding the full picture. The result? Constant refactoring, missed requirements, and technical debt from day one.

**Kickoff Bundles solve this by:**

| Problem | Solution |
|---------|----------|
| 🤯 "The AI kept changing its approach mid-feature" | Locks in architecture decisions upfront via TDD |
| 📝 "We have no documentation" | Auto-generates Product Brief, PRD, and Design System |
| 🔄 "Every new feature breaks assumptions" | Creates ERD and API Contracts before implementation |
| 🎨 "The UI is inconsistent everywhere" | Establishes Design Tokens and Wireframe standards |

## 📦 Choose Your Bundle

### `kickoff-light-bundle` — Move Fast, Ship Smart
*For: MVPs, startups, internal tools, hackathons*

One workflow installs everything you need to go from idea → implementation in **minutes**:
- **Integrated Spec (`docs/spec.md`)** — Combined Product Brief, PRD, and FSD in one file.
- **Tech Stack & ERD** — Essential architecture decisions and data models.
- **Traceable Task List (`docs/todo.md`)** — Direct-to-code checklist instead of Jira tickets.

```bash
npx mountd add meganopus/pdlc kickoff-light-bundle
```

---

### `kickoff-heavy-bundle` — Enterprise-Grade Planning
*For: Regulated industries, multi-team projects, platform engineering*

A comprehensive suite for predictability and scale:
- **Global Artifacts** — Semantic Versioned Product Brief, PRD, and Design System.
- **Core Architecture** — Centralized ERD, API Standards, and Tech Stack.
- **Feature Artifacts** — Per-feature FSD, API Contracts (OpenAPI).
- **Sprint Stories** — Granular, estimated tickets for agile teams.

```bash
npx mountd add meganopus/pdlc kickoff-heavy-bundle
```

## 🔧 Additional Skills & Workflows

Beyond the kickoff bundles, PDLC includes standalone skills you can cherry-pick as needed:

<details>
<summary><strong>📚 All Available Skills</strong></summary>

| Skill | Description |
|-------|-------------|
| `ai-humanizer` | Refine content to be conversational and undetectable as AI |
| `document-explainer` | Explain complex documents or code in simple terms |
| `epic-single` | Generate a single, detailed Epic |
| `story-single` | Generate a single, detailed User Story |
| `prd-agent-generator` | Create PRDs specifically for AI Agents |
| `qa-test-scenario` | Generate comprehensive QA test scenarios |
| `tdd-lite-generator` | Lightweight TDD for smaller changes |
| `skill-creator` | Create new skills for the PDLC system |

**Install individual skills:**
```bash
npx mountd add meganopus/pdlc skill-name
```

</details>

<details>
<summary><strong>🔄 All Available Workflows</strong></summary>

| Workflow | Description |
|----------|-------------|
| `/create-product-brief` | Interactive interview for Product Brief |
| `/create-design-system` | Interactive interview for Design System |
| `/create-wireframes` | Interactive interview for Wireframes |
| `/create-tdd` | Interactive interview for TDD |
| `/add-feature-light` | Add features with Tech Spec approach |
| `/add-feature-heavy` | Full documentation suite for new features |
| `/start-story` | **Context-aware** story starter (auto-loads Light vs Heavy docs) |
| `/fix-typechecks` | Systematic TypeScript error resolution |

**Install individual workflows:**
```bash
npx mountd add meganopus/pdlc workflow-name
```

</details>

## 📖 How It Works

1. **Install a bundle** → Skills and workflows are copied to your `.agent/` directory
2. **Run the kickoff workflow** → Answer questions about your project
3. **Review generated docs** → Product Brief, PRD, Design System, etc.
4. **Start building** → Your AI assistant now has full context

## License

MIT
