# application-helper

A Claude Code skill that tailors your resume to a specific role and company.

Give it a job description URL. It researches the role, reads your master resume, asks what to emphasise and downplay, then writes a tailored resume to `output/`.

## Setup

1. **Clone this repo**

   ```
   git clone https://github.com/techwritingwitch/application-helper.git
   cd application-helper
   ```

2. **Build your master resume**

   The master resume is the source of truth the skill reads from. The more detail it contains, the better the output — the skill selects and trims, so thin input produces thin resumes.

   Open `master-resume.md` and fill it in manually, or use the following prompt in Claude Code (with your LinkedIn PDF attached) to generate a comprehensive first draft:

   ```
   Role: You are an expert executive resume writer and career strategist.

   Task: Analyze the provided background materials and construct an exhaustive, comprehensive master resume (master-resume.md). The goal is a "kitchen sink" document containing maximum detail, metrics, and project scope, which will be tailored for specific applications later.

   Inputs provided:
   - [Attach your LinkedIn PDF export]
   - The my-voice.md file in this repo

   Execution instructions:
   1. Synthesize & expand: merge the LinkedIn data with any publicly available technical contributions, repositories, and writing you have online.
   2. Maximize detail: under each role, break down achievements into sub-categories (e.g. Tech Stack, Core Projects, Leadership). Do not optimise for brevity; optimise for completeness.
   3. Adhere to voice: strict compliance with my-voice.md is mandatory.
   4. Format: output in clean, highly organised Markdown.

   Clarification guardrail: if any critical technical details, metrics, or context are ambiguous or missing, do not invent them. Flag them or ask me directly at the end of your response.
   ```

   To export your LinkedIn profile as a PDF: **Me → Settings & Privacy → Data privacy → Get a copy of your data**, or use the PDF export option on your profile page.

3. **Review, correct, and fill in the gaps**

   The generated resume is a starting point, not a finished product. Read through it carefully before using it — AI works from what it can find publicly, which means it can miss things, overstate things, or get details subtly wrong.

   Check for:
   - **Accuracy** — every claim should be something you'd comfortably say in an interview. If it sounds better than reality, fix it.
   - **Completeness** — add anything that's missing, especially experience that isn't well represented online
   - **Your voice** — rewrite any lines that don't sound like you, even if they're technically correct
   - **Flagged gaps** — at the end of the generated resume you'll find a **Flagged gaps** section listing details that couldn't be found or confirmed. Work through these: metrics, dates, event counts, tool names, certification details, and salary expectations

   This step is not optional. The master resume is your document — the skill is here to help you build it faster, not to build it for you.

4. **Open the project in Claude Code**

   ```
   claude
   ```

## Usage

```
/tailor-resume https://example.com/jobs/technical-writer
```

The skill will:
1. Fetch and read the job description
2. Research the company and pay rates for the role and location
3. Ask which skills and experience to emphasise or downplay
4. Write a tailored resume to `output/[company]-[role].md`
5. Write an interview prep file to `output/[company]-[role]-interview-prep.md`

## Output

Two files are written to `output/` per application:

**`[company]-[role].md`** — your tailored resume. Import into Google Docs (File → Import) to edit and export as PDF.

**`[company]-[role]-interview-prep.md`** — interview preparation file containing:
- Company and role background
- Salary research for the role and location
- Anticipated interview questions with space for your answers
- Weak spots a sceptical interviewer might push back on

Use the interview prep file as context in a Claude conversation to keep preparing as you move through the process.

The `output/` folder is gitignored — your files stay local.

## Notes

- The skill will only draw from content in `master-resume.md` — it won't invent experience
- It flags gaps where your master resume felt thin for a role, so you know what to address
- Run `/tailor-resume` once per application; tweak the output before sending

## Requirements

- [Claude Code](https://claude.ai/code) (CLI or desktop app)
