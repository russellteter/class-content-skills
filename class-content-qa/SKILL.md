---
name: class-content-qa
description: >
  Quality assurance and validation skill for Class Technologies marketing content.
  Run this AFTER drafting content with class-content-writer (or after receiving any
  Class content that needs review). This skill checks for brand voice compliance,
  AI writing pattern detection, terminology violations, evidence quality, structural
  compliance, and overall readiness for publication. Trigger on: "review this Class
  content", "check this blog post", "QA this draft", "is this on-brand for Class",
  "check for AI patterns", "review for brand compliance", "de-slop this",
  "make this sound less AI", "clean up this Class content", "does this match our
  voice", "brand review", "content review", "check this before publishing",
  or any request to validate, review, or improve existing Class Technologies content.
  Also trigger proactively after class-content-writer produces a draft. Layers the
  russell-voice anti-slop rules on top of Class brand standards for the final
  quality pass.
---

# Class Content QA

This skill validates Class Technologies content against brand standards, catches AI writing patterns, and ensures publication readiness. It runs as the final pass before content goes to the user for review.

**Prerequisites:** This skill references class-brand-voice for terminology and voice standards. Read that skill's reference files (especially terminology.md and anti-patterns.md) before running validation.

## The QA Process

### Step 1: AI Pattern Detection (Most Critical)

This is the highest-priority check. AI-generated content has tell-tale structural patterns that trained readers (and detection tools) recognize. Scan every paragraph for these patterns and flag every instance.

**Binary Contrasts** — The "Not X, it's Y" pattern.
- "It's not about technology. It's about the learning."
- "The problem isn't knowledge. It's application."
- "This isn't a nice-to-have. It's a must-have."

**Fix:** State Y directly. Delete the negation setup. "Application matters more than knowledge transfer" is cleaner than the contrast formula.

**Throat-Clearing Openers** — Warm-up phrases that delay the point.
- "In today's rapidly evolving learning landscape..."
- "As organizations increasingly turn to virtual solutions..."
- "It's no secret that virtual training has become..."
- "When it comes to effective virtual learning..."
- "In a world where remote work is the new normal..."

**Fix:** Delete the entire opener. Start with the specific thing.

**Dramatic Fragmentation** — Short fragments stacked for false emphasis.
- "Engagement. Connection. Results."
- "One platform. One experience. Zero friction."
- "That's it. That's the difference."

**Fix:** Complete sentences. "Class gives instructors engagement data, connection tools, and measurable results" is more credible than the staccato version.

**False Agency** — Giving tools, concepts, or documents human verbs. This includes obvious cases AND subtle ones where inanimate things "do" things only people can do.

Obvious:
- "The platform transforms the experience."
- "This data tells a powerful story."
- "Class empowers organizations to..."

Subtle (these slip through first drafts):
- "Compliance documentation assembles itself." → "Program managers pull compliance docs from one source."
- "The integration eliminates manual work." → "Providers eliminate manual work by connecting their classroom to their LMS."
- "Templates ensure consistency." → "Instructors deliver consistent sessions by starting from the same template."
- "Analytics demonstrate ROI." → "Training managers demonstrate ROI by showing clients engagement analytics."

**Fix:** For every sentence, ask: is a human doing the verb? If not, name the person and make them the subject.

**Performative Emphasis** — Phrases that announce importance instead of demonstrating it.
- "Let that sink in."
- "This matters. A lot."
- "Full stop."
- "Make no mistake."
- "Here's why this is important."

**Fix:** Delete entirely. If the point is important, the content demonstrates it.

**Narrator-from-a-Distance** — Floating above the scene instead of putting the reader in it.
- "People tend to disengage when..."
- "Organizations often struggle with..."
- "This happens because..."
- "Nobody designed this."

**Fix:** Put the reader in the room. "You've seen it happen: ten minutes into the breakout, three of the four groups have gone silent."

**Lazy Extremes** — Sweeping claims without qualification.
- "Every organization needs..."
- "Everyone struggles with..."
- "Always" / "Never" / "All"

**Fix:** Be specific. "L&D teams running 50+ sessions monthly..." / "Organizations with distributed workforces..."

**Three-Item Rhythm (Most Common Pattern — Check Every List)** — AI defaults to triples in prose. Humans use pairs or singles. This is the single most frequent AI tell in Class content drafts. Scan every comma-separated list in the post and count items.

Flagged examples:
- "engagement, connection, and results"
- "plan, execute, and measure"
- "engagement tracking, delivery consistency, and compliance documentation"
- "standardized templates, structured breakouts, and real-time monitoring"
- "attendance records, assessment results, and engagement data"

Exempt: bullet/numbered lists, product name lists (Docebo, Cornerstone, Canvas), and lists of 4+ items.

**Fix:** Drop to two items ("engagement and compliance records"), or restructure the sentence entirely. Do not simply delete the weakest item if it changes the meaning — rewrite the sentence to make two items carry the point.

**-ly Adverbs** — AI overuses adverbs as intensifiers. Flag every -ly word.

Common offenders: "increasingly," "significantly," "effectively," "dramatically," "seamlessly," "ultimately," "consistently," "essentially," "fundamentally."

**Fix:** Delete the adverb and strengthen the verb. "Clients want evidence" not "Clients increasingly want evidence." Max 2 -ly words per 1,500-word post.

**Em Dashes** — AI overuses em dashes (—) for dramatic pauses.

**Fix:** Replace with commas or periods. No em dashes in Class content.

### Step 2: Brand Voice Compliance

Check against the class-brand-voice standards:

**Terminology scan:**
- Any banned words? (revolutionary, cutting-edge, game-changing, leverage, synergy, holistic, robust, ecosystem, innovative, world-class, thought leader)
- Features described by outcome or by name? (Must be by outcome)
- "Built on Zoom and Teams" or "integrates with"? (Must be "built on")
- "Purpose-built" used for differentiation?
- "VILT" spelled out on first use?
- Competitor names used? (Must use category: "meeting tools," not specific products)

**Voice attribute check:**
- Is it credible? (Claims sourced?)
- Is it accessible? (Plain language, contractions used?)
- Is it practical? (Actionable guidance in every section?)
- Is it honest? (Acknowledges limitations?)
- Is it consultant-like? (Best practices before product?)
- Is it outcome-focused? (Features tied to what people DO?)

**Tone check:**
- Does the tone match the content type? (Blog = 60/40 conversational/authoritative)
- Does the tone match the vertical? (Government = security-first, Healthcare = safety-first)
- Is there artificial urgency or fear-based messaging?
- Is there aggressive sales language in educational content?

### Step 3: Evidence Quality

**Research citations:**
- Are there at least 2 third-party citations from independent sources? (Required for blog posts. The same survey cited twice counts as one source, not two.)
- Is each citation attributed to a named source with specifics (report name, year, sample size)?
- Are statistics specific (percentages, sample sizes)?
- Are any claims unsourced?
- If only one source was available, is the gap flagged in the QA report?

**Customer quotes:**
- Do quotes include full attribution (name, title, company)? All three required. Flag any missing element.
- Are quotes substantive? A strong quote references a specific challenge, measurable result, or workflow change. A weak quote offers generic praise ("Class is essential for quality"). Flag weak quotes and recommend either finding a stronger one or pairing the weak quote with a specific data point from the same customer.
- Do quotes come from the target vertical? A Volvo quote in a training-providers post is off-target unless the point is about how enterprise buyers evaluate providers.

### Step 4: Structural Compliance

**For blog posts, check:**
- Key Takeaways section present near top? (4-6 bullets)
- Subheading every 150-250 words?
- Paragraphs 2-4 sentences (80%+ of paragraphs)?
- CTA at end with action verb + specific benefit?
- Word count in target range?
- Template pattern followed?

**Formatting:**
- Bold text used sparingly (5-8 instances max)?
- No more than one exclamation mark?
- No emojis in blog/website content?
- Active voice in 90%+ of sentences?

### Step 5: Russell Voice Layer (Final Pass)

Apply the russell-voice skill rules as the final quality filter. This catches patterns that pass brand compliance but still sound "written by AI":

- Contractions used everywhere possible?
- Any adverbs (-ly words)? Kill them.
- Any passive voice? Find the actor.
- Any inanimate thing doing a human verb? Name the person.
- Any "here's what/this/that" throat-clearing? Cut to the point.
- Three consecutive sentences match length? Break one.
- Does it sound like an email from a human who has a job? Good.
- Does it sound like an AI wrote a "professional blog post"? Rewrite the whole thing.

## Output Format

When reviewing content, produce a structured report:

```
## QA Report: [Content Title]

### AI Pattern Flags
[List each flagged pattern with the specific text and suggested fix]

### Terminology Violations
[List each violation with correction]

### Evidence Gaps
[List unsourced claims or missing citations]

### Voice & Tone Notes
[Assessment of overall voice compliance with specific callouts]

### Structural Notes
[Any template or formatting deviations]

### Overall Assessment
[Ready for review / Needs revision / Major rewrite needed]

### Recommended Edits
[Prioritized list of specific edits, highest-impact first]
```

## Scoring (Optional)

If the user wants a quantitative assessment:

| Dimension | Weight | Criteria |
|-----------|--------|----------|
| AI Pattern Detection | 30% | Zero AI patterns = 10. Each pattern found = -1. Below 5 = rewrite needed. |
| Brand Voice Compliance | 25% | Terminology, voice attributes, tone alignment |
| Evidence Quality | 20% | Sources cited, claims supported, quotes attributed |
| Structure | 15% | Template followed, formatting correct, flow logical |
| Readability | 10% | Paragraph length, sentence variety, scannability |

**Score 8+/10:** Ready for user review.
**Score 6-7/10:** Needs specific edits (provide the edits).
**Score below 6:** Substantial revision or rewrite recommended.

## Reference Files

- Read class-brand-voice/references/terminology.md for the complete banned words list and preferred terms
- Read class-brand-voice/references/anti-patterns.md for detailed anti-pattern examples with fixes
- Read the russell-voice skill references (phrases.md, structures.md) for the complete AI pattern detection rules
