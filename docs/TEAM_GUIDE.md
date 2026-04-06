# Class Content Skill Stack — Team Guide

**April 2026**

---

## What This Is

Four AI skills built into Claude Desktop that write on-brand Class Technologies blog posts and deliver them as publication-ready Word documents. The skills encode our brand voice, writing standards, terminology rules, quality checks, and document formatting so every piece of content follows the same playbook regardless of who requests it.

## How the Four Skills Work Together

**1. Brand Voice (DNA)** loads first and defines how Class communicates: voice identity, tone by content type, messaging pillars, terminology rules, anti-patterns, and real examples from published content. You never call this directly. It loads automatically.

**2. Content Writer (Execution)** takes your topic through five phases: a creative intake funnel, web research for current data, template selection, drafting with anti-AI rules applied during writing, and handoff with a summary of evidence cited and any gaps.

**3. Content QA (Validation)** scores the draft on a 10-point scale across five dimensions: AI pattern detection (30%), brand voice compliance (25%), evidence quality (20%), structure (15%), and readability (10%). After QA passes and edits are applied, it generates a Class-branded Word document of the finished post.

**4. Brand Document (Formatting)** defines the exact typography, colors, and layout for all Class Word documents. Content QA reads this skill automatically when generating the final .docx. You never call it directly.

---

## How to Use It

### Step 1: Start the Writer
Type your blog idea, then type `/class-content-writer` and press enter.

### Step 2: Answer the Intake Questions (~30 seconds)
Claude asks four questions in two rounds. These work as a decision funnel — starting with the big picture and narrowing down. Claude uses your answers to make the craft decisions (template, positioning level, structure) so you don't have to.

| Round | Question | What It's Asking |
|-------|----------|------------------|
| Round 1 | The Spark | Where did this idea come from? A customer win, a recurring pain point, a trend or research finding, or a competitor gap. |
| | The Takeaway | If the reader remembers one thing, what should it be? A better way, practical guidance, urgency, or social proof. |
| Round 2 | Your Material | What raw material do you have? Customer quotes, notes and key points, a link to react to, or just the topic. |
| | The Reader | Picture the reader. Are they comparing tools, frustrated with results, justifying budget, or skeptical about virtual? |

Every question includes an "Other" option for custom input. After both rounds, Claude summarizes what it's going to write and confirms before proceeding.

### Step 3: Review the Draft
Claude writes the full post. Read it, give feedback if you want changes.

### Step 4: Run QA
Type `/class-content-qa` and press enter. Claude returns a scored report with specific flags and fixes. Once all edits are applied, Claude generates a Class-branded .docx of the finished blog post and saves it for you.

### Shortcut
To skip the pause between draft and QA, add "and run QA when you're done" to your initial request. Claude still runs the intake questions but chains everything else.

---

## What You Get at the End

1. A scored QA report (in chat) with specific flags and recommended fixes
2. A publication-ready Class-branded Word document (.docx) with proper typography, colors, and layout

---

## What the Skills Enforce Automatically

| Category | What It Checks |
|----------|----------------|
| Terminology | Banned words, feature-by-outcome descriptions, "built on Zoom and Teams" framing, VILT spelled out on first use |
| Voice | Contractions, active voice, problem-before-solution, Class as enabler not hero, no aggressive sales language |
| Evidence | Minimum 2 independent research citations, customer quotes with full attribution (name, title, company), no unsourced claims |
| AI Detection | Three-item list elimination, -ly adverb removal, false agency correction, throat-clearing deletion, em dash removal |
| Structure | Template compliance, subheading every 150-250 words, 2-4 sentence paragraphs, CTA with action verb |
| Document | Roboto/Roboto Light fonts, Navy (#0A1849) text, Purple (#4739E7) headings, branded table styles, proper margins |

---

## Installation

See the [README](../README.md) for installation instructions.

## File Structure (14 files across 4 skills)

| Skill | Files | Contains |
|-------|-------|----------|
| Brand Voice | SKILL.md + 4 reference files | Voice identity, tone matrix, terminology bible, anti-patterns, messaging pillars, published examples |
| Content Writer | SKILL.md + 3 reference files | 5-phase process, 4 templates, writing checklist, headline formulas, hook patterns, creative intake funnel |
| Content QA | SKILL.md | 5-step QA process, AI detection rules, scoring rubric, branded doc generation step |
| Brand Document | SKILL.md + 2 reference files + 1 script | Typography hierarchy, color palette, table styles, document templates, python-docx module |

