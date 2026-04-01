# analyze-codebase

Scans an existing codebase to produce a `project-context.md` — enabling all downstream skills to work in brownfield-aware mode.

**Trigger:** *"Analyze my codebase"* or *"Analyze my project"*

---

## What it does

Reads your project's manifest files, data models, routes, and key business logic. Builds a structured understanding of your tech stack, domain entities, existing features, and constraints — then validates everything with you before writing the output.

Run it once before `create-prd` on an existing project. Re-run it anytime the codebase changes significantly.

---

## Output

Produces `knowledge/project-context.md` (path configured in `_project/config.yaml`) containing:

- Tech stack and dependencies
- Architecture shape
- Domain model (entities and relationships)
- Existing features grouped by area
- API / screen surface
- Technical and business constraints
- Conventions observed in the codebase
- Changelog (updated on each run)

This file is automatically detected by `create-prd`, which will start in brownfield mode.

---

## Two Modes

### First run — Full analysis
Runs the complete 4-step workflow: structure scan → deep dive → validation → output.

### Subsequent runs — Incremental update
Detects `project-context.md` already exists and offers:
- `[U] Update` — uses `git log` to find what changed since the last run, re-reads only affected files, updates sections in-place, appends a changelog entry
- `[F] Full re-analysis` — starts from scratch

---

## Workflow Steps

| Step | What happens |
|---|---|
| 1 — Structure | Scans directory tree, reads manifest files, detects tech stack |
| 2 — Deep Dive | Reads models, routes, and key business logic (auto-proceeds) |
| 3 — Validate | Walks through findings with you, fills gaps code can't reveal |
| 4 — Complete | Writes `project-context.md` from template |
| Incremental | Git-diff based update of affected sections only |

---

## What it reads

| File type | Purpose |
|---|---|
| `package.json`, `pyproject.toml`, `go.mod`, etc. | Tech stack detection |
| `prisma/schema.prisma`, `models/`, `entities/` | Domain model |
| `routes/`, `controllers/`, `api/`, `screens/` | Feature mapping |
| `services/`, `use-cases/`, `domain/` | Business logic |
| `.env.example` | External service dependencies |
| `README.md` (first 60 lines) | High-level project description |

It does **not** read: test files, migration files, lock files, generated files, or assets.
