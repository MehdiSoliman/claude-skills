# claude-skills

A shared library of Claude Code skills for product and engineering workflows.

Skills are reusable AI-assisted workflows that run directly inside Claude Code. They follow a structured, step-by-step architecture that ensures consistent, high-quality output across any project.

---

## Available Skills

| Skill | Trigger | Description |
|---|---|---|
| [`create-prd`](./skills/create-prd/) | *"I want to create a new PRD"* | Guides you through a full Product Requirements Document via structured PM facilitation |
| [`analyze-codebase`](./skills/analyze-codebase/) | *"Analyze my codebase"* | Scans an existing project to produce a `project-context.md` — enabling brownfield-aware PRD creation |
| [`check-implementation-readiness`](./skills/check-implementation-readiness/) | *"Check implementation readiness"* | Validates that PRD, UX, Architecture and Epics are complete and aligned before development starts |

---

## How it Works

Each skill is a self-contained workflow made of step files. Claude Code reads one step at a time, facilitates a conversation, and builds output incrementally. No step is skipped, no content is generated without your input.

All skills share a single `_project/config.yaml` file per project — one file that tells every skill where to find your input documents and where to write output.

---

## Getting Started

**→ See [SETUP.md](./SETUP.md) for full installation and project configuration instructions.**

---

## Repository Structure

```
claude-skills/
├── .claude-plugin/
│   ├── marketplace.json       # Skill catalog — tells Claude Code what's available
│   └── plugin.json            # Plugin identity
├── skills/
│   ├── create-prd/            # PRD creation workflow
│   ├── analyze-codebase/      # Codebase analysis workflow
│   └── check-implementation-readiness/
├── _templates/
│   └── project-config.yaml   # Template to copy into each project
├── skills-lock.json           # Tracks skill versions
└── SETUP.md                   # Installation guide
```

---

## Project Configuration

Each project that uses these skills needs a `_project/config.yaml` at its root. Copy from `_templates/project-config.yaml` and fill in your values:

```yaml
user_name: "Your Name"
project_name: "My Project"
communication_language: "English"
document_output_language: "English"
planning_artifacts: "planning"    # where PRDs are written
project_knowledge: "knowledge"    # where input docs live
```

See [SETUP.md](./SETUP.md) for the full project folder structure.

---

## Adding a New Skill

1. Create a folder under `skills/<skill-name>/`
2. Add a `SKILL.md` with `name` and `description` frontmatter
3. Add a `workflow.md` that loads `_project/config.yaml` and routes to step files
4. Add step files under `steps/`
5. Add output templates under `templates/` if needed

Skills follow the step-file architecture — see any existing skill for reference.
