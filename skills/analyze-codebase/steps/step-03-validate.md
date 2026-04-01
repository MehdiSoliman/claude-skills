# Step 3: Validate with User

**Progress: Step 3 of 4** - Next: Generate project-context.md

## STEP GOAL:

Walk through the complete analysis with the user, correct misunderstandings, and fill gaps that the code alone couldn't reveal — especially business context, intent, and constraints not visible in code.

## MANDATORY EXECUTION RULES (READ FIRST):

### Universal Rules:

- 🛑 NEVER present findings as definitive — the user knows their system better than you do
- 📖 CRITICAL: Read the complete step file before taking any action
- 📋 YOU ARE A FACILITATOR — present findings as hypotheses to be validated
- ✅ YOU MUST ALWAYS SPEAK in your Agent communication style with the config `{communication_language}`

### Step-Specific Rules:

- 🎯 This is a conversation, not a report — ask, listen, refine
- 🚫 FORBIDDEN to proceed without user confirming the analysis is accurate
- 💬 Surface what code CANNOT tell you — business intent, priorities, hidden constraints
- 🔍 Pay special attention to corrections — they reveal what matters most

## SEQUENCE OF INSTRUCTIONS:

### 1. Present Full Analysis

Walk the user through everything found in steps 1 and 2, section by section:

---
"**Here's my complete analysis of {{project_name}}. Please correct anything that's wrong or incomplete.**

---

**Tech Stack**
{{tech stack summary from step 1}}

---

**Architecture Shape**
{{architecture description}}

---

**Domain Model — Key Entities**
{{list each entity with brief description and key relationships}}

---

**Existing Features**
{{grouped list of what's already built}}

---

**API / Interface Surface**
{{key endpoints or screens}}

---

**Constraints I've Noticed**
{{technical constraints, limitations, notable debt}}

---

What's wrong, missing, or needs more nuance?"

---

### 2. Fill Business Context Gaps

Code reveals WHAT exists. Ask the user about WHY and WHAT NEXT:

Ask these questions (one at a time, based on what's still unclear):

**About the current state:**
- "What parts of the existing system are you most proud of / want to preserve?"
- "What parts are causing the most pain right now?"
- "Are there any architectural decisions I should know about — things that were intentional even if they look odd?"

**About constraints:**
- "Are there any hard constraints I should know — performance requirements, scaling expectations, compliance rules?"
- "Is there anything that absolutely cannot change in the existing system?"

**About the future:**
- "What's the primary goal of what you're building next — extending an existing feature or adding something new?"
- "Are there any integrations (third-party APIs, services) that will be involved?"

Ask only the questions that aren't already clear from the code. Do not interrogate — keep it conversational.

### 3. Refine the Analysis

Based on user responses:
- Correct any misidentified entities or features
- Add context that wasn't in the code
- Note constraints explicitly mentioned by the user
- Update your understanding of the domain language (use the user's words, not generic terms)

### 4. Final Confirmation

Present the refined summary and ask for sign-off:

"**Here's the updated picture:**

{{refined summary — same sections as step 1, now updated}}

---

Are you happy with this as the basis for your project context document? Any final adjustments?"

Wait for confirmation before proceeding.

### 5. Save State

Update frontmatter of `{outputFile}`:

```yaml
stepsCompleted: ['step-01-structure.md', 'step-02-deep-dive.md', 'step-03-validate.md']
userValidated: true
```

### 6. Present Menu

"**Ready to generate your project-context.md.**"

Display: "[C] Continue — Generate project-context.md (Step 4 of 4)"

#### Menu Handling Logic:

- IF C: update frontmatter, then read fully and follow: `./step-04-complete.md`
- IF user requests more changes: apply them, redisplay refined summary, redisplay menu
- IF user asks questions: answer and redisplay menu

---

## 🚨 SYSTEM SUCCESS/FAILURE METRICS

### ✅ SUCCESS:

- Full analysis presented section by section
- Business context gaps filled through targeted questions
- User corrected misunderstandings or confirmed accuracy
- Domain language updated to match user's own terminology
- Final summary confirmed by user
- Frontmatter updated with userValidated: true

### ❌ SYSTEM FAILURE:

- Presenting analysis as definitive without inviting corrections
- Asking all gap questions at once instead of conversationally
- Proceeding without user confirmation
- Using technical jargon instead of the user's domain language
- Not updating analysis based on user corrections

**Master Rule:** The user knows their system. Your analysis is a starting hypothesis. Correct it, then generate.
