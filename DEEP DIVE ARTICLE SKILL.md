---
name: deep-dive-article
description: Write in-depth analytical articles (2,500–4,000 words) on crypto, DeFi, and finance topics with original opinions, web-researched sources, inline citations, and a human-sounding editorial voice. Use this skill whenever the user asks for a "deep dive", "analysis piece", "long-form article", "explainer", "breakdown", "thesis", or "write up" on a specific protocol, token, ecosystem, financial concept, market event, or investment topic. Also trigger when the user names a specific project (e.g. Aerodrome, Morpho, Lido, a specific token or chain) and asks for an article, post, write-up, or content. Default to this skill for any article-length finance/crypto deliverable; do not produce these as plain chat responses.
---

# Deep-Dive Article

Produces a 2,500–4,000 word analytical article on a crypto, DeFi, or finance topic. The output reads like a thoughtful operator wrote it: a real thesis, specific facts, varied rhythm, and zero AI tells.

## The job

The reader is intelligent, busy, and skeptical. They want one of two things from a piece this long:

1. A specific, defensible thesis they hadn't formed themselves
2. A thorough enough mapping of a topic that they can form their own thesis from it

Either way, the article has to do the actual analytical work. Surveys, neutral summaries, and "on one hand / on the other hand" pieces fail this skill's bar. Pick a position, defend it with evidence, acknowledge the counter-case honestly, and end somewhere the reader couldn't have ended on their own.

## Workflow

Run these steps in order. Don't skip the research phase, and don't skip the outline.

### 1. Clarify the scope (only if genuinely ambiguous)

If the prompt is clear ("write a deep dive on Aerodrome's veAERO mechanics" → clear), skip this. If it's broad ("write something on DeFi yields"), ask one question to pin down: the specific angle, the timeframe, and whether there's a thesis the user already has in mind. Don't interrogate. One question, maybe two.

### 2. Research

Run web searches before writing. The skill is useless if the facts are stale or hallucinated. Minimum standards:

- 5–10 distinct searches covering: the primary subject, recent news/developments (last 90 days), counter-arguments and critics, comparable projects or analogues, and any specific data points the thesis will rest on (TVL, yields, volume, market share, etc.)
- Web-fetch primary sources when you cite numbers: protocol docs, Dune dashboards, official blog posts, SEC filings, earnings transcripts. Don't cite a number you only saw in a tweet.
- For anything legal or regulatory, find the actual rule, filing, or statute. Don't paraphrase a journalist paraphrasing the rule.
- Surface conflicting sources and note the conflict in the piece. Disagreement is interesting.

If the topic is settled history (e.g. "the 2022 Luna collapse"), you can lean more on synthesis than fresh sources, but still verify dates, figures, and quotes.

### 3. Develop the thesis

Before outlining, write one sentence: *the thesis*. What is this article arguing? What would a smart reader's takeaway be?

Bad theses: "Aerodrome is an important DeFi protocol." (No argument.) "Crypto is volatile." (No insight.)

Good theses: "Aerodrome's emissions schedule is structurally incompatible with its stated goal of becoming Base's liquidity layer, and the team has roughly 12 months to fix it before the ve flywheel breaks." Or: "Morpho's vault model is the first credible answer to the inefficiency Aave and Compound have lived with for five years, but the risk is now in curator selection, not protocol code."

A thesis has a claim, a reason, and stakes. If the thesis can be inverted and still sound reasonable, it's not sharp enough yet.

### 4. Outline

Sketch the structure before writing prose. A 3,000-word piece typically needs:

- A lede that hooks with a specific fact, scene, or counterintuitive observation (not a definitional intro)
- The thesis surfaced within the first 250 words
- 3–6 body sections that each do real work (build evidence, address a counter, walk through a mechanism, compare to an analogue)
- A "what could break this thesis" section, honestly engaged
- A close that lands somewhere the lede gestured at, with a concrete implication or prediction

Subheads should be specific and informative, not cute. "The emissions problem" beats "A closer look."

### 5. Write

Length target: 2,500–4,000 words. If the topic doesn't earn 2,500 words of original analysis, push back and propose a shorter piece instead of padding.

Voice and posture defaults (apply automatically):

- **Have actual opinions.** Use first person sparingly but unambiguously when stating a view: "I don't buy the bull case here, and here's why." Hedging language ("it could be argued", "some might say") is banned unless you're genuinely representing a real third party.
- **Be specific.** Numbers, names, dates, tickers, contract addresses when relevant. "Aerodrome's TVL grew significantly" is worthless. "AERO TVL went from $180M in January to $1.4B by April, then bled back to $600M as emissions outpaced incentives" is an article sentence.
- **Vary rhythm.** Mix short punchy sentences with longer ones that carry complex thoughts. Avoid the AI cadence of "three medium-length sentences with similar structure, one after another, each starting differently but feeling the same."
- **Cut filler.** No "in today's rapidly evolving landscape." No "it's important to note that." No "ultimately." No "in conclusion."
- **No em dashes** (per user preference). Use commas, parentheses, periods, or colons instead.
- **No rule of three.** When you catch yourself listing three things, ask if two or four is more honest.
- **No promotional language.** Don't call anything "revolutionary," "groundbreaking," or "game-changing." Show, don't adjectivize.

Apply the humanizer skill's principles automatically. Before finishing, scan the draft for: AI vocabulary (delve, navigate, landscape, tapestry, multifaceted, robust), inflated symbolism, vague attributions ("experts say", "critics argue" without naming them), passive constructions hiding agency, and superficial -ing analyses ("highlighting the importance of..."). Fix them.

### 6. Citations

Inline citations using markdown link syntax: `[anchor text](url)`. Cite when:

- Stating a specific number or statistic
- Quoting or paraphrasing a specific person or document
- Making a claim that the average reader would reasonably want to verify
- Disagreeing with a named position (link to the position you're disagreeing with)

Don't over-cite. Don't cite obvious or background facts. A 3,000-word piece typically has 8–15 inline links, not 40.

Use primary sources where possible. Order of preference: official docs / filings / on-chain data > the project's own blog > reputable analytical sources (Messari, The Block, Bankless if topical, Delphi) > major financial press (Bloomberg, Reuters, FT, WSJ) > everything else. Avoid CoinTelegraph and similar aggregators unless they're the only source for breaking news.

### 7. Format

Ask the user (or use what they specified) before writing. Common options:

- **Markdown file** in the workspace at `/mnt/user-data/outputs/`, named for the topic
- **Styled HTML** with a dark editorial aesthetic (see references/html-template.md for the styling pattern)
- **Plain prose in chat** for short pieces or when iterating

For markdown and HTML, include: title, optional dek/subtitle, byline if specified, body with subheads, and inline links. Don't add a generated "Sources" appendix; the inline links are the sources.

### 8. Self-review before delivering

Run this checklist silently:

- [ ] Does the lede earn the reader's attention with something specific?
- [ ] Is the thesis stated clearly in the first 250 words?
- [ ] Does every body section do real work, or could it be cut?
- [ ] Are the strongest counter-arguments honestly addressed?
- [ ] Does the close land somewhere, or does it just stop?
- [ ] Any AI tells (delve, navigate, landscape, in conclusion, em dashes, rule of three)?
- [ ] Any unsourced specific claims that should be cited?
- [ ] Any hedging that should be a direct statement instead?

Fix what fails. Then deliver.

## What this skill does not do

- Generic SEO content for lead generation (use the humanizer + standard prompting; this skill is for analytical pieces, not keyword-optimized resource pages)
- Neutral-voice explainers (this skill has opinions on purpose)
- Pieces under 2,000 words (the structure here is overkill; just write it directly)
- Pure news coverage (use a news-style brief; this skill is for analysis)

If the user asks for one of the above, say so and offer the right alternative instead of forcing the deep-dive shape.

## Reference files

- `references/html-template.md` — The dark editorial HTML pattern for styled output
- `references/voice-guide.md` — Expanded guidance on voice, rhythm, and the specific AI tells to scrub
