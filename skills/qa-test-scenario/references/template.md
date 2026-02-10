# QA Test Scenario Template

**File Name Format:** `docs/tests/qa-scenarios-[feature-name].md`

```markdown
# QA Test Scenarios: [Feature Name]

**Date:** [YYYY-MM-DD]
**Priority:** [Critical / High / Medium]
**Scope:** [Brief description of what is being tested]

---

## 1. Test Coverage Overview
- **Features Covered**: [List key features]
- **Total Scenarios**: [Count]
- **Critical Path**: [Count]
- **Edge Cases**: [Count]

---

## 2. Essential Test Scenarios

| ID | Feature | Scenario | Type | Priority | Steps | Expected Result |
|----|---------|----------|------|----------|-------|-----------------|
| TS-001 | [Feature] | [Title] | Functional | CRITICAL | 1. [Step]<br>2. [Step] | [Outcome] |
| TS-002 | [Feature] | [Title] | Edge Case | HIGH | 1. [Step]<br>2. [Step] | [Outcome] |
| TS-003 | [Feature] | [Title] | Security | CRITICAL | 1. [Step]<br>2. [Step] | [Outcome] |

---

## 3. Performance & Environment
**Performance Criteria:**
- [Metric]: [Threshold] (e.g., Load time < 200ms)

**Test Environments:**
- [Platform/Browser]: [Version]
- [Device]: [OS Version]

---

## 4. Test Data Requirements
- [Data Type]: [Requirements] (e.g., User with expired subscription)

---

## 5. Execution Notes
- **Prerequisites:** [Pre-conditions]
- **Blockers:** [Known issues]
```
