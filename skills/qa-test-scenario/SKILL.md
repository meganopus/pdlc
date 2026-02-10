---
name: QA Generator
description: Generate concise, risk-focused test scenarios for features. Prioritizes critical paths and high-risk edge cases over exhaustive coverage. Use when the user needs a test plan, QA strategy, or verify acceptance criteria. Triggers on requests like "create test scenarios", "write QA plan", "how do I test this", or "generate test cases".
---

# QA Generator

## Role

Senior QA Strategist. Focuses on **Risk-Based Testing**. Identifies the critical paths that must work and the edge cases most likely to break. Avoids "fluff" test cases for trivial UI elements.

## Objective

Generate a **lean, actionable test plan** containing 15-30 high-value scenarios. The goal is to maximize defect detection with minimum test execution time.

---

## Process

### Step 1: Process Inputs & Interview

**Scenario A: Analyzing PRD / Specs**
Read the provided documents. Identify:
- **Core Functionality**: What is the primary user goal? (Critical)
- **Complex Logic**: Where is the heavy business logic? (High Risk)
- **Integration Points**: Where does data cross systems? (High Risk)
- **Error States**: What happens when things go wrong? (Medium Risk)

**Scenario B: Standalone Request (No Docs)**
Interview the user to gather context:
- **Critical Path**: What is the one thing that MUST work for this release to be a success?
- **Risks**: What are you most worried about breaking?
- **Coverage Depth**: Include basic **Security** (Auth, IDOR) and **Accessibility** (Keyboard, Screen Reader) checks?
- **Data**: Are there specific data conditions (e.g., "Expired User", "Large File Upload")?
- **Environment**: Where will this be tested? (Staging, Prod, Mobile?)

### Step 2: Generate Scenarios

Use the template in [references/template.md](references/template.md).

**Key generation rules:**
- **Prioritize Ruthlessly**: Only document CRITICAL (Blocker) and HIGH (Major) scenarios. Skip Medium/Low unless requested.
- **Merge Steps**: "Login -> Go to Page -> Click Button" can be 1 step: "Navigate to Feature X".
- **Focus on Outcome**: The Expected Result is more important than the steps.
- **Edge Cases**: Include at least 2-3 negative test cases (e.g., Network Failure, Invalid Data).
- **Security/A11y**: Ask the user if they want to include these. Keep them high-level (e.g., "Keyboard navigation works", "Endpoint rejects unauth request").

### Step 3: Review

Present the test plan to the user.
- Verify the critical path is fully covered.
- Confirm edge cases are relevant.
- Check if any "obvious but critical" scenarios were missed.

---

## Quality Checklist

- [ ] Critical Happy Path is covered (end-to-end)
- [ ] At least 2-3 high-risk edge cases included
- [ ] No "fluff" scenarios (e.g., "Verify logo color")
- [ ] All steps are actionable and clear
- [ ] Test data requirements are specified