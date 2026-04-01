---
stepsCompleted: []
userValidated: false
generatedAt: ''
techStack:
  language: ''
  framework: ''
  database: ''
architectureShape: ''
entitiesFound: []
featuresFound: []
workflowType: 'project-context'
---

# Project Context — {{project_name}}

**Generated:** {{date}}
**Analyzed by:** {{user_name}}

---

## Tech Stack

**Language:** {{language}}
**Framework:** {{framework}}
**Database:** {{database}}
**Key Libraries:** {{libs}}
**Infrastructure:** {{infra}}

---

## Architecture

**Shape:** {{monolith | monorepo | microservices | client-server | etc.}}

{{description of how the system is structured — key layers, main modules, how they relate}}

---

## Domain Model

{{description of the domain and how entities relate to each other}}

### Key Entities

| Entity | Description | Key Relationships |
|--------|-------------|-------------------|
| {{Entity}} | {{what it represents}} | {{related to X, Y}} |

---

## Existing Features

{{grouped list of what's already built in the system}}

### {{Feature Area 1}}
- {{feature}}
- {{feature}}

### {{Feature Area 2}}
- {{feature}}
- {{feature}}

---

## API / Interface Surface

{{overview of the existing API or screen structure}}

| Endpoint / Screen | Purpose |
|-------------------|---------|
| {{route or screen}} | {{what it does}} |

---

## Constraints

Constraints that any new development must respect:

- **Technical:** {{hard technical constraints — framework limits, legacy code, etc.}}
- **Performance:** {{existing performance requirements or patterns in place}}
- **Security:** {{auth mechanisms, data access patterns}}
- **Business:** {{rules that cannot change}}

---

## Conventions

Patterns observed in the codebase that new work should follow:

- **Naming:** {{naming conventions}}
- **Structure:** {{how files and folders are organized}}
- **Patterns:** {{architectural or coding patterns in use}}

---

## Notes

{{anything important that doesn't fit above — pain points, known debt, user-provided context}}

---

## Changelog

<!-- Most recent entry first -->

### {{date}} — Initial analysis

**Sections created:** Tech Stack, Architecture, Domain Model, Existing Features, API Surface, Constraints, Conventions
