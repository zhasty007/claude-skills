---
name: market-sizing
description: Build a structured market size estimate using top-down and bottom-up approaches, with explicit assumptions, math, and sensitivity analysis. Use this skill whenever a user asks to "size the market," "estimate TAM/SAM/SOM," "size the opportunity," or wants to understand the addressable market for a product, service, or geography. Trigger on phrases like "how big is the market," "market size for," "TAM analysis," "addressable market," "revenue opportunity for," or when a user is preparing a business case, investment thesis, or strategic recommendation that requires a quantified market opportunity. Also trigger when the user has a market size estimate and wants it pressure-tested.
---

# Market Sizing

A consulting skill for producing defensible market size estimates. The goal is not a single number but a structured estimate with transparent assumptions that can survive a CFO's questioning.

## When to use this skill

The user needs a quantified market opportunity. Common contexts: business case for a new product, investment thesis, strategic planning, board pitch, expansion decision. The skill also applies when the user has an existing estimate and wants it validated.

## What this skill produces

A market sizing analysis with:

1. **Definition of the market** — Precisely what is being sized, including geography, segment, time period, and what is excluded
2. **Top-down estimate** — Starting from a large population and narrowing down via filters
3. **Bottom-up estimate** — Starting from unit economics and scaling up
4. **Reconciliation** — Where the two approaches converge or diverge, and why
5. **Sensitivity** — Which assumption most affects the answer, and the range of outcomes if that assumption shifts
6. **Confidence rating and gaps** — How confident the estimate is and what would tighten it

## Process

1. **Define the market precisely.** Before estimating anything, force the user to specify:
   - The product or service (with enough specificity to exclude adjacent categories)
   - Geography (country, region, or global)
   - Time period (current year, 5-year forward, fully ramped state)
   - Customer segment (consumer, SMB, mid-market, enterprise; B2B vs B2C; subsegments)
   - What is explicitly out of scope
   
   A loose definition produces a useless estimate.

2. **Run top-down.** Start from a known large number (population, total industry spend, total addressable customer base) and apply sequential filters. Each filter is an assumption that must be stated. Example chain: US adults → adults with relevant condition → adults who would seek treatment → adults with insurance coverage → adults who would choose this product over alternatives → revenue per user.

3. **Run bottom-up.** Start from the unit (one customer, one transaction, one location) and scale up. Example: revenue per customer × customers per sales rep × number of sales reps × penetration rate. Or: revenue per location × number of viable locations × ramp curve.

4. **Show the math at every step.** Each step is a line item with a number, a unit, and the source or assumption behind it. Sources should be specific enough that the user can verify them ("US Census 2024 population estimate," "internal pilot data on conversion rate," "industry analyst report by X"). Do not cite specific reports the user has not provided; describe the type of source they should consult.

5. **Produce low, base, and high cases.** For each approach, provide a conservative, base, and optimistic estimate based on plausible ranges for the most uncertain assumptions.

6. **Reconcile.** Compare the two approaches. If they converge within 20%, that is a reasonable check. If they diverge significantly, investigate why. The divergence usually reveals a flawed assumption in one or both approaches, and finding it is more valuable than averaging the two numbers.

7. **Identify the single most sensitive assumption.** Out of all the inputs, which one moves the answer the most. State it explicitly and recommend the user validate that assumption first.

## Output format

Use a clear two-column or table-based layout for the math. Each row is one step. Columns: variable, value, unit, source or assumption.

End with a one-paragraph summary that states the base case number, the range, the confidence level, and the single highest-leverage assumption to validate next.

## Constraints

- Do not produce a single number without showing the work. Single numbers are unfalsifiable and unusable.
- Do not invent statistics. If a number is not available, state the assumption and label it as such.
- Do not present false precision. "$12.34M" implies measurement; "$12M (range $8M-$18M)" reflects reality.
- Do not skip the reconciliation step. Top-down and bottom-up agreeing is a meaningful signal; disagreeing is more meaningful still.

## Example trigger phrases

- "Size the market for [product] in [geography]"
- "What's the TAM for this opportunity"
- "Build me a market sizing for the business case"
- "How big is this opportunity"
- "Pressure test this market size estimate"
