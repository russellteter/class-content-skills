---
name: class-content-writer
description: >
  Write blog posts, articles, and long-form marketing content for Class Technologies.
  This is the execution skill — it turns topic ideas into structured, on-brand content
  following Class's proven templates, formulas, and voice patterns. Always loads
  class-brand-voice first as the foundation, then applies the writing structures here.
  Trigger on: "write a Class blog post", "draft a blog for Class", "create an article
  about virtual training", "write content about VILT", "Class blog about [topic]",
  "write a customer story for Class", "draft a thought leadership piece",
  "create a Class article about [topic]", "blog post about breakout rooms",
  "write about engagement in virtual training", "Class content about government training",
  "corporate training article", or any request to produce long-form written content
  for Class Technologies marketing. Also trigger when the user provides a blog post
  idea or topic and wants it developed into a full draft. Use the class-content-qa
  skill after drafting to validate the output.
---

# Class Content Writer

This skill produces blog posts and long-form content for Class Technologies. It works in a defined sequence: intake, research, structure, draft, and handoff to quality review.

**Before writing anything, read the class-brand-voice skill.** That skill defines the voice constants, terminology, and messaging pillars. This skill handles structure and execution.

## The Writing Process

### Phase 1: Creative Intake (MANDATORY)

**This step is required every time this skill triggers.** Do not skip it, even if the user provides a detailed brief. The intake discovers the story before any writing begins.

The intake is a decision funnel — start big picture, narrow down. Claude can infer template selection, positioning level, vertical messaging, pillar connections, and format from these four questions combined with whatever the user said in their original prompt. Do not ask the user to do Claude's job.

Use the AskUserQuestion tool to run two rounds of questions. Wait for answers to Round 1 before asking Round 2.

#### Round 1: The Seed

These two questions extract the creative origin and the core argument. They matter more than anything else because they determine whether the content has a real point of view or is just generic category copy.

Call AskUserQuestion with these two questions:

**Question 1 — What sparked this?**
- question: "Where did this content idea come from?"
- header: "The Spark"
- multiSelect: false
- options:
  - label: "A customer conversation or win" | description: "Something a customer said, did, or achieved that's worth sharing"
  - label: "A pain point that keeps coming up" | description: "A problem you hear from prospects, trainers, or L&D teams repeatedly"
  - label: "A trend or research finding" | description: "New data, an industry shift, or a report you want to react to"
  - label: "A competitor claim or market gap" | description: "Something a competitor is saying that's wrong, or a category blind spot"

**Question 2 — What's the point?**
- question: "If the reader remembers one thing, what should it be?"
- header: "The Takeaway"
- multiSelect: false
- options:
  - label: "There's a better way to do this than what they're doing now" | description: "Reframe their current approach — show the gap and the path forward"
  - label: "Here's how to actually do this well" | description: "Practical, actionable guidance they can implement"
  - label: "This problem is bigger than they realize" | description: "Raise urgency — the cost of inaction or the scale of the opportunity"
  - label: "Other organizations are already solving this" | description: "Social proof — show what's possible with real examples"

#### Round 2: Shaping the Draft

After receiving Round 1 answers, ask these two questions. They determine what Claude has to work with and how to frame the piece.

Call AskUserQuestion with these two questions:

**Question 3 — What do you have to work with?**
- question: "What raw material can you bring to this piece?"
- header: "Your Material"
- multiSelect: true
- options:
  - label: "Customer quotes or specific data" | description: "Named quotes, metrics, or outcomes you can paste in or describe"
  - label: "A rough angle or key points" | description: "You've been thinking about this — you have notes, a hot take, or bullet points"
  - label: "A link or source to react to" | description: "An article, report, competitor page, or research you want to build around"
  - label: "Just the topic" | description: "Starting from scratch — Claude should research and develop the angle"

**Question 4 — Who's reading this?**
- question: "Picture the person reading this. What's their situation?"
- header: "The Reader"
- multiSelect: false
- options:
  - label: "They're evaluating tools and comparing options" | description: "Mid-funnel buyer doing research — needs proof and differentiation"
  - label: "They train virtually but aren't getting the results they want" | description: "Practitioner who's frustrated — needs practical help and a better approach"
  - label: "They need to justify training investment to leadership" | description: "Building a business case — needs ROI evidence and peer examples"
  - label: "They're skeptical virtual training can match in-person" | description: "Needs to be shown, not told — proof over promises"

#### After Intake

Once both rounds are answered, do three things before writing:

1. **Synthesize the brief.** Summarize in 2-3 sentences what you're going to write and why. Example: "Writing a blog post about the hidden cost of running training on meeting tools — sparked by a pain point you keep hearing, aimed at practitioners who are frustrated with their current results. You've got some notes on key points, so I'll build around those and layer in third-party research. The piece should leave readers thinking there's a better way to do this."

2. **Confirm with the user.** Wait for a go-ahead before proceeding. If anything sounds off, adjust.

3. **Let Claude do the mapping.** Based on the four answers plus the user's original prompt, Claude determines:
   - **Template** — Customer win → Template B. Pain point → Template A. Trend/research → Template C. How-to takeaway → Template D.
   - **Positioning level** — Customer story or tool comparison reader → stronger Class presence. Trend piece or skeptical reader → softer, earn-trust-first approach.
   - **Vertical messaging** — Pull from the brand voice messaging-pillars reference based on whatever context the user provided.
   - **Pillar connections** — Determined by the topic itself, not by asking the user to pick from an internal list.
   - **Format and length** — Blog (1,400-1,800 words) unless the user specified otherwise in their original prompt.

   Do not ask the user to make these decisions. These are craft decisions the skill exists to make.

Then proceed to Phase 2.


### Phase 2: Research & Evidence Gathering

Every Class blog post needs evidence. Before writing, assemble:

- **2-3 third-party research citations from at least 2 independent sources** — LinkedIn reports, Training Magazine surveys, ATD research, Brandon Hall studies, Gartner/Forrester data, academic journals. Do a web search for current data relevant to the topic. Do not rely on a single survey or report used multiple times. If you can only find one source, flag the gap in the handoff notes.
- **1-2 customer quotes that reference specific outcomes** (if available) — Full attribution: name, title, company. Check class.com/customer-stories/ and the blog archive. Quotes must address a specific challenge or measurable result, not generic praise like "Class is great." A quote saying "we saw participation increase five-fold" is strong. A quote saying "Class is an imperative element to improve quality" is weak unless paired with a specific outcome. If only weak quotes are available, flag that the draft needs a stronger customer proof point before publishing.
- **Relevant Class features** — Map topic to specific features using the class-brand-voice terminology reference. Describe by outcome, not feature name.
- **Competitor/category context** — What do meeting tools NOT do that's relevant to this topic? This frames Class's differentiation.

### Phase 3: Structure Selection

Choose the template that fits the content goal. Class uses four proven structures:

#### Template A: Problem → Best Practices → Platform Advantage
**Best for:** How-to posts, instructional design topics, operational challenges
**Length:** 1,400-1,800 words

```
1. Headline (Problem/Solution format, 9-14 words)
2. Key Takeaways (4-6 bullets previewing the post)
3. Opening Hook (relatable struggle or data point, 2-3 sentences)
4. Why This Matters (industry context + research, 150-200 words)
5. Universal Best Practices (5-6 actionable tactics, platform-agnostic, 100-150 words each)
6. How Class Enables These (2-3 feature-to-outcome connections, 150-200 words)
7. Closing Statement (restate tension + path forward, 50-75 words)
8. CTA (demo or resource, action-oriented)
```

#### Template B: Research / Case Study Narrative
**Best for:** Customer stories, research findings, day-in-the-life posts
**Length:** 1,000-1,400 words

```
1. Headline (narrative framing, 9-12 words)
2. Key Takeaways (4-5 bullets)
3. Context Setting (customer/research situation, 100-150 words)
4. Narrative Sections (3-5 sections, each with quote + feature + outcome)
5. Results / Impact (quantified where possible)
6. Closing Reflection (what this means for the reader)
7. CTA (demo or related resource)
```

#### Template C: Industry Trend / Argument
**Best for:** Thought leadership, trend analysis, category positioning
**Length:** 1,400-1,800 words

```
1. Headline (assertive claim, 8-14 words)
2. Key Takeaways (4-6 bullets)
3. Opening (trend observation + research, 100-150 words)
4. Core Argument (5-7 sections, each 100-200 words, mix data + reasoning)
5. Real-World Example (case study mid-article, 200-300 words)
6. Closing Argument (reinforces headline claim)
7. CTA (demo or resource)
```

#### Template D: Educational / How-To Guide
**Best for:** Comprehensive guides, framework explanations, strategy pieces
**Length:** 1,600-2,000 words

```
1. Headline (How-to or guide format)
2. Key Takeaways (4-6 bullets)
3. Opening Hook (problem or opportunity)
4. Why This Matters (business case + research, 200-250 words)
5. Core Theory/Framework (academic backing, explained accessibly)
6. Numbered Strategy Section (5-6 tactics, each with explanation, 150-200 words)
7. Organizational/Cultural Context (how to enable these practices)
8. Closing Thought
9. CTA
```

### Phase 4: Writing the Draft

Follow these rules while drafting. Read [references/writing-rules.md](references/writing-rules.md) for the complete checklist.

**Headline rules:**
- 9-14 words. Practical verbs: "Make," "Improve," "Reduce," "Help," "Rethink."
- Include the primary keyword naturally.
- No buzzwords. No clickbait. The headline should tell the reader exactly what they'll get.

**Opening hook rules:**
- Start with a specific problem, data point, or scenario. Never start with "In today's..." or any throat-clearing.
- Put the reader in the room. Sensory details. Named roles. Specific numbers.
- 2-3 sentences max before the reader knows what this post is about.

**Body rules:**
- Paragraphs: 2-4 sentences (80% of paragraphs). 5 sentences max for complex concepts.
- Subheadings every 150-250 words. Benefit-focused, not just topic labels.
- Active voice throughout. Name the actor.
- Data integrated into the narrative (not segregated into callout boxes).
- Features described by outcome ("see all breakout groups from one screen") not by name ("Bird's Eye View").
- Customer quotes with full attribution (name, title, company).

**Anti-AI rules to follow DURING drafting (do not defer these to QA):**
- **Two items, not three.** When listing things in prose, default to pairs. "engagement data and compliance records" not "engagement data, compliance records, and analytics." Three-item lists are the single most common AI tell. Every time you write a comma-separated list, count the items. If there are three, cut one or restructure.
- **Kill -ly adverbs.** Delete "increasingly," "significantly," "effectively," "dramatically," "seamlessly," "ultimately." Find a stronger verb or cut the word. "Clients want evidence" not "Clients increasingly want evidence."
- **No inanimate agents.** Never let a tool, platform, data, or document perform a human action. "Documentation assembles itself" is false agency. "Program managers pull compliance docs from one source" names the human. Every sentence needs a person doing the verb.
- **Vary sentence length.** After writing a paragraph, check: are any three consecutive sentences roughly the same length? Break one shorter or combine two longer.

**Key Takeaways rules:**
- Place near the top, after headline and before or just after the opening hook.
- 4-6 bullets that preview the post's main points.
- Each bullet is one standalone insight — valuable even without reading the full post.
- Written as declarative statements, not questions.

**CTA rules:**
- End every post with a CTA.
- Action verb + specific benefit: "Schedule a 20-minute walkthrough to see how Class handles [topic-relevant feature]."
- "Get a Live Demo" and "Schedule a Demo" are the primary patterns.
- Secondary: "Download the [specific resource]" or "See how [customer] uses Class for [topic]."
- Never: "Learn more," "Contact us," "Sign up now."

**Word count targets:**
- Blog posts: 1,400-1,800 words (sweet spot: 1,500)
- Customer stories: 1,000-1,400 words
- Thought leadership: 1,400-1,800 words
- Guides: 1,600-2,000 words

### Phase 5: Handoff to Quality Review

After completing the draft, the class-content-qa skill should validate:
- Brand voice compliance (terminology, tone, anti-patterns)
- AI writing pattern detection (binary contrasts, throat-clearing, false agency)
- Evidence quality (all claims sourced, quotes attributed)
- Structure compliance (correct template, proper section flow)
- Russell voice layer (if the piece needs Russell's personal voice)

Present the draft to the user with:
1. The full draft text
2. A summary of template used, word count, and key evidence cited
3. Any gaps that need user input (missing customer quotes, unverified data, topic areas needing SME review)

## SEO Integration

Every blog post should include:
- **Primary keyword** — used in headline, first paragraph, one subheading, and meta description
- **2-3 secondary keywords** — used naturally in body copy and subheadings
- **Meta description** — under 160 characters, includes primary keyword, compels the click
- **Internal links** — 2-3 links to related Class blog posts or resources
- **External links** — 1-2 links to authoritative third-party sources cited in the post

Write for humans first. SEO is structure, not stuffing.

## Reference Files

- [references/writing-rules.md](references/writing-rules.md) — Complete writing checklist: paragraph length, sentence structure, formatting, and pre-delivery quality checks
- [references/headline-formulas.md](references/headline-formulas.md) — Proven Class headline patterns with examples and when to use each
- [references/hook-formulas.md](references/hook-formulas.md) — Opening hook patterns extracted from published Class content
