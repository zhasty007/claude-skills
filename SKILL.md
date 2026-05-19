---
name: client-meeting-prep
description: Prepare a consultant for a specific client meeting by predicting questions, objections, and the optimal posture. Use this skill whenever a user mentions an upcoming client meeting, executive presentation, steering committee, partner call, or stakeholder conversation and asks for help preparing, anticipating questions, or rehearsing. Trigger on phrases like "prep me for," "I have a meeting with," "what will they ask," "how should I handle [stakeholder]," "anticipate objections," "meeting prep," or when the user describes a meeting context and shares background on the attendees. Also trigger when the user wants to think through "what does good look like" for an upcoming conversation.
---

# Client Meeting Prep

A consulting skill for preparing a consultant for a specific client meeting. The goal is to walk in with the conversation already mostly run in your head.

## When to use this skill

The user has an upcoming meeting and wants to prepare deliberately. The skill applies whether the meeting is a routine status update or a high-stakes decision conversation. Higher stakes means more value.

## What this skill produces

A meeting prep brief covering:

1. **Meeting objective** — One sentence stating what success looks like, observable and specific
2. **Stakeholder read** — What each attendee likely cares about and how they tend to engage
3. **Three likely questions** — In order of probability, with prepared answers
4. **Three likely objections** — In order of probability, with responses
5. **One question to ask** — The single question that, if asked at the right moment, shifts the conversation
6. **Opening line and closing ask** — Specific words for the two moments that matter most
7. **Failure modes** — How this meeting could go wrong and the early signals

## Process

1. **Gather context aggressively.** Ask the user:
   - Who is in the meeting (roles, not just names; tenure if known)
   - What is the stated purpose vs. the actual purpose (often different)
   - What has happened in prior meetings with this group
   - What outcome the user wants and what outcome they would accept
   - What the attendees already know vs. what is new to them
   - Any known sensitivities, relationships, or political dynamics

2. **Define success observably.** A vague objective ("get alignment") produces vague preparation. Force specificity: "Get the CFO to verbally commit to including this in the FY26 budget cycle." If the user cannot state success observably, that itself is the first thing to fix.

3. **Read each stakeholder individually.** For each attendee:
   - What is their role's natural concern (a CFO's natural concern differs from a COO's)
   - What is their personal track record on similar topics
   - How do they tend to engage (the asker, the skeptic, the silent decider, the procedural one)
   - What would they need to hear to feel comfortable

4. **Predict 3 likely questions, in priority order.** For each, draft an answer that:
   - Acknowledges the question fairly
   - Provides the answer directly
   - Stops without over-explaining
   
   The questions to anticipate hardest are the ones the user does not want to be asked.

5. **Predict 3 likely objections, in priority order.** For each:
   - State the objection in the strongest form (do not strawman)
   - Identify what is right about it
   - Provide the response that addresses the legitimate concern
   - Note what to do if the objection persists despite the response

6. **Find the one question to ask.** Most meeting prep over-prepares for answering and under-prepares for asking. A well-placed question can:
   - Reframe the conversation around what the user controls
   - Get a senior person to commit publicly to a position
   - Surface a hidden objection before it gets raised in front of others
   - Shift the meeting from problem-listing to decision-making
   
   Identify which of these applies and draft the question.

7. **Draft the opening line and the closing ask.** These two moments are disproportionately important:
   - Opening: the first sentence sets the frame. It should not be "Thanks for taking the time." It should be a sentence that tells the room why this meeting matters.
   - Closing: the explicit ask. What does the user want each attendee to do after the meeting. State it as a verb-led sentence.

8. **Name the failure modes.** How could this meeting go sideways. Common patterns:
   - One attendee derails into a tangent
   - A senior person who was not expected to attend shows up
   - The meeting gets cut to half its scheduled time
   - The decision gets deferred
   - A side conversation has already produced a decision the user does not know about
   
   For each likely failure mode, name one recovery move.

## Output format

Structured brief with section headers. The opening line and closing ask are written out verbatim, not described.

End with a one-paragraph "if you only remember three things" summary the user can scan in the 30 seconds before the meeting starts.

## Constraints

- Do not produce generic prep that could apply to any meeting. Every section should reference specific details the user provided.
- Do not invent attendee preferences. If the user did not say how the CFO tends to engage, ask or label the prediction as a working assumption.
- Do not draft answers that hedge to the point of being meaningless. Crisp answers, even if wrong, force the user to refine; mushy answers do not.

## Example trigger phrases

- "Prep me for my meeting with [stakeholder] tomorrow"
- "What will the steering committee ask"
- "How should I handle the CFO on this"
- "I have a meeting with the partner about [topic], help me prepare"
- "Anticipate objections to my recommendation"
