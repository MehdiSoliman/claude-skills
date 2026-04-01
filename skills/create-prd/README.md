# create-prd

Guides you through creating a comprehensive Product Requirements Document via structured PM facilitation.

**Trigger:** *"I want to create a new PRD"* or *"Let's create a product requirements document"*

---

## What it does

A step-by-step workflow where Claude acts as a product-focused PM facilitator. It asks the right questions, builds the document incrementually with your input, and never generates content without your validation.

The workflow automatically detects:
- **Greenfield** — no existing project docs → starts from scratch
- **Brownfield** — finds `project-context.md` or docs in `project_knowledge` → starts with full codebase awareness

---

## Output

Produces `planning/prd.md` (path configured in `_project/config.yaml`) containing:

1. Executive Summary
2. Success Criteria
3. Product Scope (MVP → Growth → Vision)
4. User Journeys
5. Domain Requirements *(if applicable)*
6. Innovation Analysis *(if applicable)*
7. Project-Type Requirements
8. Functional Requirements
9. Non-Functional Requirements

---

## Workflow Steps

| Step | What happens |
|---|---|
| 1 — Init | Detects existing state, discovers input documents |
| 2 — Discovery | Classifies project type, domain, complexity |
| 2b — Vision | Explores product vision and differentiators |
| 2c — Executive Summary | Drafts executive summary |
| 3 — Success Criteria | Defines measurable outcomes |
| 4 — User Journeys | Maps comprehensive user flows |
| 5 — Domain | Industry-specific requirements |
| 6 — Innovation | Competitive differentiation analysis |
| 7 — Project Type | Platform-specific requirements |
| 8 — Scoping | MVP vs roadmap decisions |
| 9 — Functional Requirements | Capability contract |
| 10 — Non-Functional Requirements | Quality attributes |
| 11 — Polish | Flow, coherence, information density review |
| 12 — Complete | Handoff and next steps |

**Resumable:** if you stop mid-workflow, the skill picks up exactly where you left off on the next run.

---

## Input Documents (optional but recommended)

Place any of these in your `project_knowledge` folder before running — the skill will load them automatically:

| File pattern | Purpose |
|---|---|
| `*brief*.md` | Product brief |
| `*research*.md` | Research documents |
| `**/project-context.md` | Output from `analyze-codebase` |
| Any docs in `project_knowledge/` | General project context |
