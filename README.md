# Class Content Skills

Three Claude Desktop skills for writing on-brand Class Technologies marketing content.

## What This Is

A skill stack that automates the process of writing blog posts and marketing content for Class Technologies. The skills encode brand voice, writing standards, terminology rules, and quality checks so that every piece of content follows the same playbook.

The stack consists of three skills that work in sequence:

1. **Class Brand Voice** — The DNA layer. Defines how Class communicates: voice constants, tone flexes, messaging pillars, terminology rules, and anti-patterns. Loaded automatically before any writing begins.

2. **Class Content Writer** — The execution layer. Takes a topic idea through a five-phase process: interactive intake, research, structure selection, drafting, and handoff. Includes four blog templates, headline formulas, opening hook patterns, and anti-AI writing rules.

3. **Class Content QA** — The validation layer. Scores content against brand standards, catches AI writing patterns, verifies evidence quality, and produces a structured QA report with a 10-point score.

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
```

### 2. Restart Claude Desktop

Close and reopen Claude Desktop (or start a new Cowork session). The skills will appear in your available skills list automatically.

### 3. Verify installation

In a new session, you should see `class-brand-voice`, `class-content-writer`, and `class-content-qa` in your available skills.

## How to Use

### Write a blog post

1. Open a Claude Desktop session
2. Type your blog idea (topic, angle, any context you have)
3. Type `/class-content-writer` and press enter
4. Answer the two rounds of multiple-choice intake questions (about 30 seconds)
5. Claude writes the draft

### Run quality assurance

After reviewing the draft, type `/class-content-qa` and press enter. Claude runs the full validation pass and returns a scored QA report.

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
  SKILL.md                          # 5-step QA process, scoring rubric, report format
```

## Interactive Intake

When the content writer skill triggers, it presents two rounds of multiple-choice questions before writing:

**Round 1:** Audience, Vertical, Content Goal, Class Positioning
**Round 2:** Format/Length, Solution Pillars, Proof Points

Every question includes an "Other" option for custom input. After both rounds, Claude summarizes the brief and confirms before proceeding.

## What the Skills Enforce

- **Terminology:** Banned words list, feature-by-outcome descriptions, "built on" framing
- **Voice:** Contractions, active voice, problem-before-solution, Class as enabler not hero
- **Evidence:** Minimum 2 independent research citations, full customer quote attribution
- **AI Detection:** Three-item list elimination, adverb removal, false agency correction
- **Structure:** Template compliance, subheading frequency, paragraph length limits
- **SEO:** Primary keyword placement, meta description, internal links

