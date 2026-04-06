# Class Content Skills

Four Claude Desktop skills for writing on-brand Class Technologies marketing content.

## What This Is

A skill stack that automates the process of writing blog posts and marketing content for Class Technologies. The skills encode brand voice, writing standards, terminology rules, quality checks, and document formatting so that every piece of content follows the same playbook and ships as a publication-ready Word document.

The stack consists of four skills that work in sequence:

1. **Class Brand Voice** — The DNA layer. Defines how Class communicates: voice constants, tone flexes, messaging pillars, terminology rules, and anti-patterns. Loaded automatically before any writing begins.

2. **Class Content Writer** — The execution layer. Takes a topic idea through a five-phase process: creative intake funnel, research, structure selection, drafting, and handoff. Includes four blog templates, headline formulas, opening hook patterns, and anti-AI writing rules.

3. **Class Content QA** — The validation layer. Scores content against brand standards, catches AI writing patterns, verifies evidence quality, and produces a structured QA report. After QA passes, generates a Class-branded .docx of the finished post.

4. **Class Brand Document** — The formatting layer. Defines the exact typography hierarchy, color palette, table styles, and python-docx implementation for all Class-branded Word documents. Used by Content QA to produce the final deliverable.

## Installation

### 1. Copy the skill folders to your Claude Desktop skills directory

```bash
# Clone this repo
git clone https://github.com/russellteter/class-content-skills.git
cd class-content-skills

# Copy each skill folder to your Claude skills directory
cp -r class-brand-voice ~/.claude/skills/
cp -r class-content-writer ~/.claude/skills/
cp -r class-content-qa ~/.claude/skills/
cp -r class-brand-document ~/.claude/skills/
```

### 2. Restart Claude Desktop

Close and reopen Claude Desktop (or start a new Cowork session). The skills will appear in your available skills list automatically.

### 3. Verify installation

In a new session, you should see `class-brand-voice`, `class-content-writer`, `class-content-qa`, and `class-brand-document` in your available skills.

## How to Use

### Write a blog post
1. Open a Claude Desktop session
2. Type your blog idea (topic, angle, any context you have)
3. Type `/class-content-writer` and press enter
4. Answer the two rounds of intake questions (about 30 seconds)
5. Claude writes the draft

### Run quality assurance
After reviewing the draft, type `/class-content-qa` and press enter. Claude runs the full validation pass, returns a scored QA report, and generates a Class-branded .docx of the finished post.

### Shortcut
To chain everything without stopping, add "and run QA when you're done" to your initial request.

## File Structure

```
class-brand-voice/
  SKILL.md                          # Voice constants, tone matrix, messaging architecture
  references/
    terminology.md                  # Product terms, feature descriptions, banned words
    anti-patterns.md                # 10 anti-patterns with bad/good examples
    messaging-pillars.md            # 4 solution pillars, 3 advantage pillars
    voice-examples.md               # Annotated excerpts from published Class content

class-content-writer/
  SKILL.md                          # 5-phase writing process, 4 templates, anti-AI rules
  references/
    writing-rules.md                # Pre-delivery checklist
    headline-formulas.md            # 5 headline patterns from published posts
    hook-formulas.md                # 5 opening hook patterns with templates

class-content-qa/
  SKILL.md                          # 5-step QA process, scoring rubric, branded doc generation

class-brand-document/
  SKILL.md                          # Typography, colors, table styles, document templates
  references/
    document-templates.md           # Full template implementations (FAQ, roadmap, report)
    style-guide.md                  # Complete python-docx code reference
  scripts/
    class_doc_styles.py             # Importable Python styling module
```

## Interactive Intake

When the content writer skill triggers, it presents two rounds of multiple-choice questions:

**Round 1 — The Seed:** Where did this idea come from? What's the one takeaway?
**Round 2 — Shaping the Draft:** What raw material do you have? Who's the reader?

Claude uses these answers to determine template, positioning level, and structure. Every question includes an "Other" option for custom input.

## What the Skills Enforce

- **Terminology:** Banned words list, feature-by-outcome descriptions, "built on" framing
- **Voice:** Contractions, active voice, problem-before-solution, Class as enabler not hero
- **Evidence:** Minimum 2 independent research citations, full customer quote attribution
- **AI Detection:** Three-item list elimination, adverb removal, false agency correction
- **Structure:** Template compliance, subheading frequency, paragraph length limits
- **SEO:** Primary keyword placement, meta description, internal links
- **Document Formatting:** Class-branded .docx output with proper typography, colors, and layout

## Pipeline Output

The complete pipeline produces:
1. A scored QA report (in chat) with specific flags and fixes
2. A publication-ready Class-branded Word document (.docx) of the finished blog post

