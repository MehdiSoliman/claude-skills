# Step 2: Deep Dive

**Progress: Step 2 of 4** - Next: Validate with User

## STEP GOAL:

Read key source files to understand the domain model, existing features, API contracts, and constraints. Build a complete technical picture before presenting it to the user for validation.

## MANDATORY EXECUTION RULES (READ FIRST):

### Universal Rules:

- 🛑 NEVER summarize without reading the actual files
- 📖 CRITICAL: Read the complete step file before taking any action
- 📋 YOU ARE A TECHNICAL ANALYST — observe and understand, do not generate content yet
- ✅ YOU MUST ALWAYS SPEAK in your Agent communication style with the config `{communication_language}`

### Step-Specific Rules:

- 🎯 Read strategically — entry points, models, routes, key services
- 🚫 FORBIDDEN to read test files, migration files, or generated files
- 🔍 Prioritize files that reveal domain language and business rules
- 💡 Build understanding progressively — entry points first, then models, then logic

## CONTEXT BOUNDARIES:

- Tech stack and directory structure from step 1 are in memory
- Focus: understand WHAT the system does, not HOW it's implemented
- Goal: extract domain language, entities, features, constraints

## SEQUENCE OF INSTRUCTIONS:

### 1. Read Entry Points

Read the main entry file(s) identified in step 1 (e.g. `main.ts`, `app.py`, `index.js`):
- What modules/routes are registered?
- What services are initialized?
- What middleware is in place?
- What does the application bootstrap tell us about its shape?

### 2. Read Data Models / Schemas

Find and read model/schema definitions:
- ORM models (`models/`, `entities/`, `schema/`, `prisma/schema.prisma`, etc.)
- Database schema files if present
- Type definitions that represent domain entities (TypeScript interfaces, Python dataclasses, etc.)

Extract:
- **Key entities** and their fields
- **Relationships** between entities
- **Business rules embedded in the model** (enums, constraints, validations)

### 3. Read Routing / API Definitions

Find and read route or controller files:
- REST routes (`routes/`, `controllers/`, `api/`)
- GraphQL schema if applicable
- Mobile navigation structure if applicable

Extract:
- **Existing API endpoints or screens**
- **What operations are supported** (CRUD, business actions)
- **Authentication/authorization patterns**

### 4. Read Key Business Logic

Identify 3-5 files that contain the most important business logic (services, use cases, domain logic):
- Look for files named after core domain concepts
- Prioritize files that are imported by many others
- Read them to understand **what the system actually does**

Extract:
- **Core business rules and workflows**
- **Domain-specific calculations or algorithms**
- **Integration points with external services**

### 5. Identify Constraints

From everything read so far, note:
- **Hard technical constraints** (specific framework limitations, legacy code that can't change, etc.)
- **Performance considerations** (caching in place, pagination patterns, etc.)
- **Security patterns** (auth mechanism, data access control)
- **Notable technical debt** (obvious workarounds, TODO comments on important issues)

### 6. Build Analysis Summary

Organize findings into:

**Domain Model:**
- List of key entities with brief description
- Key relationships

**Existing Features:**
- List of features already built, grouped by area

**API / Interface Surface:**
- Key endpoints or screens with their purpose

**Constraints:**
- Hard constraints that must be respected in the PRD

**Conventions:**
- Naming patterns, architectural patterns, coding conventions observed

### 7. Present Preliminary Findings

Brief status update to user (do NOT ask for input yet — save that for step 3):

"I've completed the deep dive. Here's a preliminary summary of what I found:

**Entities found:** {{count}} ({{list of entity names}})
**Features identified:** {{count}} areas
**Constraints noted:** {{count}}

Moving to step 3 to walk through everything with you in detail and fill any gaps."

### 8. Save State

Update frontmatter of `{outputFile}`:

```yaml
stepsCompleted: ['step-01-structure.md', 'step-02-deep-dive.md']
entitiesFound: [{{list of entity names}}]
featuresFound: [{{list of feature areas}}]
```

Then immediately read fully and follow: `./step-03-validate.md`

---

## 🚨 SYSTEM SUCCESS/FAILURE METRICS

### ✅ SUCCESS:

- Entry points, models, routes, and key business logic all read
- Domain entities and relationships identified from actual code
- Existing features mapped from routes and controllers
- Constraints identified from code patterns
- Frontmatter updated with discovered entities and features
- Brief status shown to user before proceeding

### ❌ SYSTEM FAILURE:

- Reading test files, migrations, or generated code instead of domain files
- Guessing entities without reading model files
- Skipping routing/API reading
- Not updating frontmatter before proceeding
- Presenting full analysis in this step (that's step 3)

**Master Rule:** Read deep, summarize briefly, proceed automatically to step 3. This step is about gathering — step 3 is about validating.
