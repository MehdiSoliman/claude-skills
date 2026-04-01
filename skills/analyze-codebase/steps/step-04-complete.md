# Step 4: Generate project-context.md

**Final Step — Generate Output**

## MANDATORY EXECUTION RULES (READ FIRST):

- ✅ THIS IS THE FINAL STEP — produce the output document
- 📖 CRITICAL: Read the complete step file before taking any action
- 💾 Write the complete project-context.md — no partial output
- ✅ YOU MUST ALWAYS SPEAK in your Agent communication style with the config `{communication_language}`
- ✅ YOU MUST ALWAYS WRITE document content in `{document_output_language}`

## SEQUENCE OF INSTRUCTIONS:

### 1. Write project-context.md

The output file already exists at `{outputFile}` (created in step 1 from the template). Now fill in all sections completely using everything learned in steps 1–3.

Use the validated analysis from step 3. Use the user's domain language — not generic terms.

Write each section in full. Do not leave placeholder text.

### 2. Update Frontmatter

Update the frontmatter of `{outputFile}` to mark completion:

```yaml
stepsCompleted: ['step-01-structure.md', 'step-02-deep-dive.md', 'step-03-validate.md', 'step-04-complete.md']
userValidated: true
generatedAt: {{current date}}
```

### 3. Confirm Completion

Inform the user:

"**project-context.md generated** at `{outputFile}`.

This file will be automatically picked up by the `create-prd` skill when you run it in this project. It will start in **brownfield mode** — aware of your existing system, tech stack, and constraints.

**What's in your project-context.md:**
- Tech stack and architecture
- Domain model ({{entityCount}} entities)
- Existing features ({{featureCount}} areas)
- Constraints and conventions

**Next step:** Run `create-prd` to build your PRD with full brownfield context."

---

## SUCCESS METRICS:

✅ All sections of project-context.md filled completely — no placeholder text remaining
✅ Domain language matches user's terminology from step 3 validation
✅ Frontmatter updated with completion status and date
✅ User informed of the output location and how to use it
✅ Clear next step (create-prd) communicated

## FAILURE MODES:

❌ Leaving placeholder text in any section of the output
❌ Using generic technical terms instead of the user's domain language
❌ Not updating frontmatter with completion status
❌ Partial output — all sections must be filled

**Final Reminder:** This document feeds create-prd and future skills. Quality here means quality everywhere downstream.
