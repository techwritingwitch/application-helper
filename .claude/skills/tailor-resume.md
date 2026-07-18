# Tailor Resume

Tailor `master-resume.md` to a specific role and company, then write the result to `output/`.

## Usage

`/tailor-resume <job-description-url>`

## Steps

### 1. Research

Fetch the job description at the URL provided in `args`. Then search the web for:
- The company: what they do, their size, their culture and values, recent news
- The role: how this type of role typically operates at a company of this kind
- Pay rates: typical salary or day rate for this role and seniority level in the same location as the role (or remote-adjusted if remote). Note the source and date of any figures found.

### 2. Read the master resume and voice guide

Read `master-resume.md` and `my-voice.md` from the project root.

`master-resume.md` is the source of truth — the tailored resume must only draw from content that exists here. Do not invent experience, skills, or achievements.

`my-voice.md` defines how the resume should sound. Follow it closely when writing all resume content — the summary, bullet points, and any other copy. Pay particular attention to the banned words and phrases list; none of those should appear anywhere in the output.

### 3. Ask clarifying questions

Before writing anything, ask the user two questions:

1. **Skills and experience to emphasise** — which skills, tools, or areas of experience should be foregrounded for this role? (e.g. "push the stakeholder management and cross-functional work, less the hands-on writing")
2. **Skills and experience to downplay or omit** — anything that might create a wrong impression, feel irrelevant, or invite questions they're not prepared for?

Wait for the user's answers before continuing.

### 4. Write the tailored resume

Using the research, the master resume, and the user's answers, write a tailored resume that:

- Opens with a summary paragraph written specifically for this role and company — not a generic profile
- Selects and reorders experience entries to foreground what's most relevant
- Adjusts bullet points to emphasise the skills and outcomes the user asked to highlight
- Omits or minimises anything the user asked to downplay
- Uses language from the job description where it fits naturally — do not keyword-stuff
- Stays honest: every claim must be supportable from `master-resume.md`

### 5. Save the resume

Write the tailored resume to `output/` as a markdown file. Name it using the format:

`[company-name]-[role-slug].md`

For example: `relevance-ai-technical-writer.md`

### 6. Write the interview prep file

Write a second file to `output/` named `[company-name]-[role-slug]-interview-prep.md`.

This file is designed to be used alongside Claude during interview preparation. It should contain:

**Company & role background**
- What the company does, their stage, culture, and recent news
- What this role is responsible for and where it sits in the org (if known)
- Salary research: the figures found in step 1, with sources and dates

**Likely interview questions**
Anticipate the questions most likely to come up in an initial screening or first-round interview for this role at this company. For each question:
- Write the question as the interviewer would ask it
- Note *why* this question is likely (what the interviewer is trying to assess)
- Leave a blank `**Your answer:**` field for the user to fill in

Cover at least:
- Motivational questions (why this company, why this role)
- Experience and skills questions drawn from the JD requirements
- Behavioural questions typical for this type of role
- Any questions likely to arise from gaps or mismatches between the master resume and the JD

**Weak spots to address**
Flag anything in the application that a sceptical interviewer might push back on — thin experience, a career gap, a skill listed in the JD that's underrepresented in the resume. For each one, suggest how to address it.

### 7. Tell the user what was created

Report both file paths and flag any places where the master resume felt thin for this role — gaps the user might want to fill before applying.
