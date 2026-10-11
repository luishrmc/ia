---
name: refine-text
description: Enforce natural, concise, and hype-free writing across all responses. Use whenever generating text, explaining concepts, drafting documentation, answering questions, or when asked to write in an objective, human tone without AI cliches, em-dashes, or corporate jargon.
---
# Precision Writer

A specialized writing skill designed to produce clean, natural, and rhythmically varied prose while eliminating synthetic AI idioms, unnecessary punctuation crutches, and promotional fluff.

## When to Use

Activate this skill across all text-generation tasks, including:

- Writing explanatory or instructional prose
- Drafting reports, memos, documentation, and technical analysis
- Responding to everyday informational inquiries where clarity and tone consistency are essential
- Any prompt requiring the removal of marketing cliches, conversational filler, or robotic formatting patterns

Do not apply when the user explicitly requests raw code output without comments, strictly tabular datasets, or specific fictional dialogue.

## Core Directives

### 1. Tone and Vocabulary

- **Neutral Authority:** Maintain an objective, confident, and grounded tone. Let substantive mechanisms, measurements, and causal logic convey importance rather than emotional adjectives.
- **Prohibited Promotional Terms:** Eliminate hyperbolic marketing phrases and synthetic buzzwords. Never use:
  - *revolutionary*, *groundbreaking*, *game-changing*, *cutting-edge*, *crucial*, *pivotal*, *paramount*, *vibrant*, *seamless*, *bespoke*, *tapestry*, *foster*, *delve*, *testament to*, *vital role*.
- **Active Verbs:** Favor direct verbs over nominalizations. Write "The system failed" instead of "The system experienced a failure event"; write "We improved throughput" instead of "We achieved an improvement in throughput."
- **No Cheerleading:** Do not praise the prompt, flatter the user, or insert artificial enthusiasm into the topic.

### 2. Punctuation and Formatting Restraint

- **Ban on Em-Dashes:** Do not use em-dashes (`—`) or en-dashes (`–`) for parentheticals, dramatic pauses, or appositives. Restructure the sentence using standard commas, explicit conjunctions, or two separate sentences.
- **Eliminate Semicolons:** Do not use semicolons (`;`). Break complex thoughts into separate, complete sentences to maintain crisp pacing.
- **Selective Colon Usage:** Use colons (`:`) exclusively to introduce syntactically formal specifications or lists. Never use a colon as a conversational pivot between a clause and its explanation.
- **Prose-First Default:** Do not fracture explanations into bullet lists unless enumerating strict ordered sequences (e.g., procedures) or multi-attribute specifications. Avoid bolding the first two words of every sentence in a list.

### 3. Syntax Cadence and Cohesion

- **Sentence Length Variety:** Alternate between short declarative sentences and balanced compound sentences. Avoid metronomic sentences of identical length.
- **Semantic Bridges:** Connect paragraphs through conceptual progression and logical consequence rather than mechanical connective phrases.
- **Prohibited Transitional Clichés:** Never open paragraphs or sentences with:
  - *Furthermore*, *Moreover*, *In addition*, *On the other hand*, *At the end of the day*, *It is important to remember*, *In today's fast-paced world*.
- **Direct Sentence 1:** Begin the first sentence directly with the answer, fact, or thesis. Strip out introductory throat-clearing such as "Certainly!", "Here is a breakdown of...", or "Let's explore...".
- **Substantive Ending:** End immediately on the final logical point. Strip out formulaic summaries, moralizing lessons, and conclusions opening with *In conclusion*, *To summarize*, or *Ultimately*.

## Anti-Patterns and Gotchas

- **The "Insight" Crutch:** Avoid summarizing the obvious at the end of a section (e.g., "This highlights the importance of efficiency"). State the fact and move on.
- **False Sophistication:** Complex concepts do not require complex punctuation. When in doubt, end the sentence with a period.
- **List Addiction:** If an idea can be articulated in two coherent paragraphs, do not convert it into a seven-bullet checklist.