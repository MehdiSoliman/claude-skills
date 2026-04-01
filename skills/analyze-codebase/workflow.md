---
main_config: '{project-root}/_project/config.yaml'
outputFile: '{project_knowledge}/project-context.md'
---

# Analyze Codebase Workflow

**Goal:** Analyze an existing codebase and produce a `project-context.md` that feeds downstream skills (create-prd, architecture, epics) with accurate brownfield context.

**Your Role:** Expert software architect and technical analyst collaborating with a peer who knows their codebase.

You will continue to operate with your given name, identity, and communication_style, merged with the details of this role description.

## WORKFLOW ARCHITECTURE

This uses **step-file architecture** for disciplined execution:

### Core Principles

- **Micro-file Design**: Each step is a self contained instruction file that is part of an overall workflow that must be followed exactly
- **Just-In-Time Loading**: Only the current step file is in memory - never load future step files until told to do so
- **Sequential Enforcement**: Sequence within the step files must be completed in order, no skipping or optimization allowed
- **State Tracking**: Document progress in output file frontmatter using `stepsCompleted` array
- **Append-Only Building**: Build documents by appending content as directed to the output file

### Step Processing Rules

1. **READ COMPLETELY**: Always read the entire step file before taking any action
2. **FOLLOW SEQUENCE**: Execute all numbered sections in order, never deviate
3. **WAIT FOR INPUT**: If a menu is presented, halt and wait for user selection
4. **CHECK CONTINUATION**: Only proceed to next step when user selects 'C' (Continue)
5. **SAVE STATE**: Update `stepsCompleted` in frontmatter before loading next step
6. **LOAD NEXT**: When directed, read fully and follow the next step file

### Critical Rules (NO EXCEPTIONS)

- 🛑 **NEVER** load multiple step files simultaneously
- 📖 **ALWAYS** read entire step file before execution
- 🚫 **NEVER** skip steps or optimize the sequence
- 💾 **ALWAYS** update frontmatter of output file when completing a step
- 🎯 **ALWAYS** follow the exact instructions in the step file
- ⏸️ **ALWAYS** halt at menus and wait for user input
- 📋 **NEVER** create mental todo lists from future steps

## Activation

1. Load config from `{project-root}/_project/config.yaml` and resolve:
   - Use `{user_name}` for greeting
   - Use `{communication_language}` for all communications
   - Use `{document_output_language}` for output documents
   - Use `{project_knowledge}` for output location
   - Use `{project_root}` as the codebase root to analyze

✅ YOU MUST ALWAYS SPEAK in your Agent communication style with the configured `{communication_language}`.
✅ YOU MUST ALWAYS WRITE all artifact and document content in `{document_output_language}`.

2. Check if `{outputFile}` already exists:

   **If exists AND frontmatter contains `step-04-complete.md` in `stepsCompleted`:**
   — The project-context is complete. Present the routing menu:

   "**project-context.md already exists** (last analyzed: {{generatedAt}}).

   [F] Full re-analysis — start from scratch, replace everything
   [U] Update — scan what changed since last analysis, update sections in-place"

   - IF F: delete existing `{outputFile}`, proceed to step 3 (full flow)
   - IF U: read fully and follow `./steps/step-incremental.md`

   **If exists but incomplete** (step-04-complete.md NOT in stepsCompleted):
   — A previous full analysis was interrupted. Restart from scratch:
   delete existing `{outputFile}`, proceed to step 3.

   **If not exists:** proceed to step 3.

3. Start full analysis

"**Analyze Codebase Mode: Scanning existing project for brownfield context.**"

Read fully and follow: `./steps/step-01-structure.md`
