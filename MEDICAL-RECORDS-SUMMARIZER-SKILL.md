---
name: medical-records-summarizer
description: Summarize medical records into a chronological treatment narrative for personal injury cases. Use this whenever the user uploads medical records, bills, or treatment notes (PDF, Word, or text) and wants a chronology, summary, treatment timeline, or anything that would go into a demand package or case file. Trigger on phrases like "summarize these records," "build a chronology," "medical timeline," "treatment summary," "what does this chart say," "extract the specials," "pull the diagnoses," or any time records are attached and the user wants them digested. Also trigger when the user mentions IME reports, ER notes, MRI/CT/X-ray reads, PT/OT notes, EMS run sheets, or billing statements in the context of a PI matter.
---

# Medical Records Summarizer

Turn raw medical records into a clean chronological summary that a personal injury lawyer can drop into a demand package, case memo, or settlement brochure.

## What good output looks like

The lawyer should be able to read the summary and immediately know:

1. What happened (mechanism of injury, where they presented first)
2. What was diagnosed and when
3. What treatment was rendered, by whom, for how long
4. What it cost (specials)
5. What is still outstanding or recommended (future care, work restrictions, permanency)
6. Any red flags (gaps in treatment, pre-existing conditions, inconsistent reporting, missing records)

Lawyers do not want a wall of text. They want a scannable chronology, a totals table, and a short narrative. They will read every line, so be accurate. If you are not sure about something, flag it rather than guess.

## Process

### Step 1: Read what was uploaded

If files are at `/mnt/user-data/uploads/`, view the directory first and read each file. For PDFs, use the pdf-reading skill at `/mnt/skills/public/pdf-reading/SKILL.md` if the content is not already in context.

If records were pasted into the chat as text, work from that.

### Step 2: Extract the structured data

For each treatment encounter, capture:

- **Date** (be precise; if only a date range is given, use the range)
- **Provider/facility**
- **Type of visit** (ER, urgent care, primary care, specialist consult, imaging, PT/OT, chiropractic, injection, surgery, follow-up, IME)
- **Chief complaint / mechanism reported** (especially important on the first visit; lawyers care if the mechanism is consistent across providers)
- **Diagnoses** (use ICD-10 codes if present, otherwise plain language)
- **Treatment rendered** (medications, procedures, modalities, referrals)
- **Findings** (positive imaging, range of motion deficits, neurological findings, etc.)
- **Work/activity restrictions** if noted
- **Billed charges** if visible (separate from what insurance paid; lawyers usually want the billed amount for damages purposes, but note both if available)

### Step 3: Identify the narrative arc

After the chronology, write a short narrative covering:

- Mechanism of injury and initial presentation
- How treatment progressed (improvement, plateau, escalation to specialist, surgery, etc.)
- Current status as of the most recent record
- Future care recommendations
- Permanency or impairment ratings if any
- Any documented causation opinions

### Step 4: Flag issues

These matter a lot for case valuation. Always include a section on:

- **Gaps in treatment** (anything over 30 days without a visit, with dates)
- **Pre-existing conditions** mentioned in the records
- **Inconsistent mechanism descriptions** across providers
- **Missing records** (referenced but not produced, e.g., "patient reports prior MRI at XYZ" with no MRI in the file)
- **Non-compliance notes** (missed appointments, didn't follow recommendations)
- **Causation language** that helps or hurts (e.g., "consistent with reported MVA" vs. "degenerative")

## Output format

Use this exact structure. Produce it as markdown unless the user asks for a Word doc, in which case use the docx skill at `/mnt/skills/public/docx/SKILL.md`.

```markdown
# Medical Records Summary: [Client Name]

**Date of incident:** [date]
**Records reviewed:** [list of providers and date ranges covered]
**Prepared:** [today's date]

## Chronological treatment summary

| Date | Provider | Visit type | Diagnoses | Treatment | Billed |
|------|----------|------------|-----------|-----------|--------|
| ... | ... | ... | ... | ... | $... |

## Specials summary

| Provider | Dates of service | Billed | Paid (if known) |
|----------|------------------|--------|-----------------|
| ... | ... | $... | $... |
| **Total** | | **$...** | **$...** |

## Treatment narrative

[2 to 4 paragraphs covering mechanism, initial presentation, course of treatment, current status, and future care recommendations]

## Issues and flags

- [Gaps, pre-existing conditions, inconsistencies, missing records, etc.]

## Open questions for the file

- [Things the lawyer should follow up on, e.g., "Records from Dr. Smith referenced on 3/15 but not produced"]
```

## Things to be careful about

**Do not invent dates, diagnoses, dollar amounts, or provider names.** If a record is illegible or ambiguous, write "[illegible]" or "[unclear]" rather than guessing. Lawyers send these summaries to opposing counsel and adjusters. A made-up date will get caught and burn credibility.

**Distinguish billed from paid.** For damages purposes most jurisdictions allow billed amounts (collateral source rule varies), but adjusters care about paid. Capture both when available.

**Watch for pre-existing condition language.** Anything like "history of," "chronic," "prior," "degenerative," "longstanding," or specific prior dates needs to be in the flags section. These are the things the defense will hammer on.

**Preserve causation language verbatim where it matters.** If a doctor wrote "injuries are causally related to the motor vehicle collision of [date]," quote that sentence in the narrative. If a doctor wrote something unhelpful like "etiology unclear," flag it.

**Do not opine on liability or case value.** This is a records summary, not a case evaluation. Stick to what the records actually say.

## When records are voluminous

If there are hundreds of pages, ask the lawyer up front whether they want:
- A full chronology of every visit, or
- A summary keyed to specific dates of service, or
- A focused summary on a particular body part, provider, or time window

Then proceed accordingly. Do not silently skip records.
