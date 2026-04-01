# Step: Incremental Update

**Mode: Update existing project-context.md**

## STEP GOAL:

Detect what changed in the codebase since the last analysis, re-read only the affected files, update the relevant sections in-place, and append a dated changelog entry.

## MANDATORY EXECUTION RULES (READ FIRST):

- 📖 CRITICAL: Read the complete step file before taking any action
- 🎯 ONLY re-read files that actually changed — do not redo the full analysis
- 💾 Update sections IN-PLACE — the document reflects current state, not history
- 📋 Changelog is the ONLY append — everything else is updated, not added to
- ✅ YOU MUST ALWAYS SPEAK in your Agent communication style with the config `{communication_language}`
- ✅ YOU MUST ALWAYS WRITE document content in `{document_output_language}`

---

## SEQUENCE OF INSTRUCTIONS:

### 1. Read Existing project-context.md

Read `{outputFile}` completely — load the current content and frontmatter.
Note the `generatedAt` date from frontmatter — this is the baseline.

### 2. Detect Changes

**If project uses git** (check for `.git/` at `{project_root}`):

Run: `git log --since="{{generatedAt}}" --name-only --pretty=format: | sort -u`

This returns the list of files changed since the last analysis. From this list:
- Filter out: test files, migration files, lock files, generated files, `.env`, assets
- Categorize what remains:

| Category | Signals |
|----------|---------|
| **Domain model changed** | models/, entities/, schema/, prisma/ |
| **New features / routes** | routes/, controllers/, api/, screens/, pages/ |
| **Business logic changed** | services/, use-cases/, domain/, lib/ |
| **Tech stack changed** | package.json, requirements.txt, go.mod, etc. |
| **Config / infra changed** | docker-compose, .github/, k8s/, config/ |

**If no git:** compare file modification dates against `generatedAt` using the same categorization.

### 3. Present Change Summary to User

Report what was detected before reading anything:

"**Changes detected since {{generatedAt}}:**

- {{N}} files changed in total
- Affects: {{list of categories — e.g. Domain model, Routes, Business logic}}

**Files I'll re-read:**
{{list of relevant changed files, grouped by category}}

**Skipped** (tests, locks, assets, generated): {{count}} files

Does this look right? Anything I should also check that's not in this list?"

Wait for user confirmation or additions before reading any files.

### 4. Re-read Only Affected Files

Based on confirmed categories, re-read ONLY the relevant files:

- **Domain model changed** → re-read model/schema files that changed
- **New features / routes** → re-read changed route/controller files
- **Business logic changed** → re-read changed service/domain files
- **Tech stack changed** → re-read manifest files (package.json, etc.)
- **Config / infra changed** → note the change, assess if it affects constraints section

Do NOT re-read files that haven't changed.

### 5. Identify What's New, Changed, or Removed

From re-reading, determine:
- **New entities** added to the domain model
- **Modified entities** (new fields, changed relationships)
- **Removed entities** (if any)
- **New features or endpoints**
- **Modified features** (significant behavior changes)
- **New or changed constraints**
- **Tech stack updates** (new major dependencies, removed ones)

### 6. Validate with User

Present the delta — what you found changed — and ask for input:

"**Here's what changed since the last analysis:**

**Domain Model:**
- New: {{new entities}}
- Modified: {{changed entities and what changed}}
- Removed: {{removed entities if any}}

**Features:**
- New: {{new features or endpoints}}
- Modified: {{changed features}}

**Constraints:**
- {{any new or changed constraints}}

**Tech Stack:**
- {{any dependency changes worth noting}}

---

Anything I've missed or misread? Anything that changed that the code doesn't show (business decisions, new constraints)?"

Wait for user response before updating the document.

### 7. Update Sections In-Place

Apply all confirmed changes to the relevant sections of `{outputFile}`:

- Replace outdated entity rows in the Domain Model table
- Add new entity rows
- Remove rows for entities that no longer exist
- Update the Existing Features section (add new, update changed, remove obsolete)
- Update API / Interface Surface table
- Update Constraints if needed
- Update Tech Stack if dependencies changed

**Rule:** The document always reflects the CURRENT state. Do not keep outdated content alongside new content.

### 8. Append Changelog Entry

At the bottom of the document, under `## Changelog`, prepend a new entry (most recent first):

```markdown
### {{current date}}

**Changed files:** {{count}}
**Sections updated:** {{list of sections that changed}}

**What's new:**
- {{bullet per significant addition}}

**What changed:**
- {{bullet per significant modification}}

**What was removed:**
- {{bullet per removal, if any}}
```

### 9. Update Frontmatter

Update `{outputFile}` frontmatter:

```yaml
generatedAt: '{{current date}}'
```

Also update `entitiesFound` and `featuresFound` arrays if they changed.

### 10. Confirm Completion

"**project-context.md updated.**

**Sections updated:** {{list}}
**Changelog entry added:** {{current date}}

Your downstream skills (create-prd, etc.) will now pick up the updated context automatically."

---

## 🚨 SYSTEM SUCCESS/FAILURE METRICS

### ✅ SUCCESS:

- `generatedAt` date used as correct baseline for git diff
- Only changed and relevant files re-read (no unnecessary full re-analysis)
- Change summary confirmed with user before updating
- All affected sections updated in-place — document reflects current state
- Outdated content removed, not kept alongside new content
- Changelog entry prepended with clear summary of what changed
- `generatedAt` updated in frontmatter to current date

### ❌ SYSTEM FAILURE:

- Re-reading unchanged files (defeats the purpose of incremental)
- Appending new content without removing outdated content
- Not confirming detected changes with user before updating
- Forgetting to update `generatedAt` in frontmatter
- Writing changelog in the wrong order (must be most recent first)
- Updating sections without user validation of the delta

**Master Rule:** Surgical updates only. The document stays clean and current — sections reflect now, changelog shows history.
