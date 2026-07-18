# Interview Debrief

Run a structured debrief after an interview, then update the interview prep file for the next round.

## Usage

`/interview-debrief [company]-[role-slug]`

For example: `/interview-debrief relevance-ai-technical-writer`

## Steps

### 1. Load context

Read `output/[company]-[role-slug]-interview-prep.md`. This is the source of truth for this application — you'll be adding to it, not replacing anything.

If the file doesn't exist, tell the user and stop.

### 2. Run the debrief conversationally

Work through the following topics one at a time. Ask each question, wait for the answer, then move to the next. Don't present them all at once.

**Questions asked in the interview**
- Which questions from the prep file actually came up?
- Were there any questions you weren't expecting? Ask the user to describe them.
- Were there any questions you felt you answered well? Any you'd want to handle differently?

**What you learned about the role**
- Did you get any new information about the role, the team, or how the company operates?
- Did anything shift your impression of the role — positively or negatively?
- Were any of the salary/rate figures discussed? If so, what was mentioned?

**Next steps**
- What are the next steps in the process?
- Is there another interview round expected? If so, what format (technical, panel, hiring manager, etc.)?

### 3. Update the interview prep file

Append a new section to `output/[company]-[role-slug]-interview-prep.md` under the heading:

`## Debrief — Round [N] — [today's date]`

Include:
- **Questions that came up** — from the prep list, and any unexpected ones
- **Questions to add to prep** — new questions that appeared, reworded as the interviewer asked them, with a blank `**Your answer:**` field
- **New role/company information** — anything learned that updates the picture of the role
- **Salary/rate notes** — if anything was discussed
- **What to strengthen** — based on questions that felt shaky, what to work on before the next round
- **Next steps** — format and focus of the next round if known

Do not remove or overwrite any existing content in the file — only append.

### 4. Confirm

Tell the user the file has been updated and summarise in 2–3 sentences what they should focus on before the next round.
