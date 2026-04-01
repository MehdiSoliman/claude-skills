# Step 1: Project Structure & Tech Stack

**Progress: Step 1 of 4** - Next: Deep Dive

## STEP GOAL:

Scan the project structure and detect the tech stack — languages, frameworks, dependencies, and high-level architecture shape — before doing any deep file reading.

## MANDATORY EXECUTION RULES (READ FIRST):

### Universal Rules:

- 🛑 NEVER guess or assume technology choices — read the actual files
- 📖 CRITICAL: Read the complete step file before taking any action
- 📋 YOU ARE A TECHNICAL ANALYST, not a content generator
- ✅ YOU MUST ALWAYS SPEAK in your Agent communication style with the config `{communication_language}`

### Step-Specific Rules:

- 🎯 Focus only on structure and tech detection — no deep logic reading yet
- 🚫 FORBIDDEN to read business logic or feature files in this step
- 🔍 Read only manifest files, config files, and directory structure

## SEQUENCE OF INSTRUCTIONS:

### 1. Scan Directory Structure

List the top 2 levels of the project at `{project_root}`:
- Identify key directories (src, app, lib, api, components, models, services, etc.)
- Note what each top-level folder likely contains based on its name
- Identify obvious entry points (main.ts, app.py, index.js, Program.cs, etc.)
- Note any infrastructure files (docker-compose.yml, .github/, k8s/, etc.)

### 2. Detect Tech Stack from Manifest Files

Read whichever of the following exist at `{project_root}`:

**JavaScript / TypeScript:**
- `package.json` → framework, key dependencies, scripts
- `tsconfig.json` → TypeScript config, strict mode

**Python:**
- `requirements.txt` or `pyproject.toml` or `Pipfile` → dependencies, Python version

**Mobile:**
- `pubspec.yaml` → Flutter
- `build.gradle` or `Package.swift` → Android / iOS native

**Other:**
- `go.mod` → Go
- `Cargo.toml` → Rust
- `pom.xml` or `build.gradle` → Java / Kotlin
- `Gemfile` → Ruby
- `composer.json` → PHP

Also read:
- `.env.example` or `.env.sample` → understand what external services are used
- `README.md` (first 60 lines only) → high-level description if available

### 3. Build Tech Stack Summary

From what you've read, identify:
- **Primary language(s)**
- **Framework(s)** (Next.js, FastAPI, Spring Boot, Flutter, etc.)
- **Database(s)** (PostgreSQL, MongoDB, Redis, etc. — inferred from deps or env vars)
- **Key libraries** (auth, ORM, state management, testing, etc.)
- **Infrastructure** (Docker, CI/CD, cloud provider hints)
- **Architecture shape** (monolith, monorepo, microservices, client-server, etc.)

### 4. Present Findings to User

Report what you found:

"**{{project_name}} — Structure Analysis**

**Tech Stack Detected:**
- Language: {{language}}
- Framework: {{framework}}
- Database: {{database}}
- Key libraries: {{libs}}
- Infrastructure: {{infra}}

**Architecture Shape:** {{shape}}

**Key directories:**
{{list of directories with one-line description each}}

**Entry points:** {{entry points found}}

Does this match your understanding? Anything I've misread or missed?"

Wait for user confirmation or corrections before continuing.

### 5. Save State to Output File

Create `{outputFile}` from `../templates/project-context-template.md` and update frontmatter:

```yaml
stepsCompleted: ['step-01-structure.md']
techStack:
  language: {{language}}
  framework: {{framework}}
  database: {{database}}
architectureShape: {{shape}}
```

### 6. Present Menu

"**What would you like to do?**"

Display: "[C] Continue to Deep Dive (Step 2 of 4)"

#### Menu Handling Logic:

- IF C: update frontmatter with this step added to stepsCompleted, then read fully and follow: `./step-02-deep-dive.md`
- IF user provides corrections: apply them, update summary, redisplay menu
- IF user asks questions: answer and redisplay menu

#### EXECUTION RULES:

- ALWAYS halt and wait for user input after presenting menu
- ONLY proceed when user selects 'C'

---

## 🚨 SYSTEM SUCCESS/FAILURE METRICS

### ✅ SUCCESS:

- Directory structure scanned at `{project_root}`
- All manifest files found and read
- Tech stack correctly identified from actual files (not guessed)
- Findings presented clearly to user
- User confirmed or corrected the findings
- Output file created from template with frontmatter initialized

### ❌ SYSTEM FAILURE:

- Guessing tech stack without reading manifest files
- Reading business logic files in this step
- Not presenting findings to user before continuing
- Proceeding without user selecting 'C'
- Not creating output file with initialized frontmatter

**Master Rule:** Read manifests and structure only. No business logic yet. Always confirm with the user before continuing.
