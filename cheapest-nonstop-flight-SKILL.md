---
name: cheapest-nonstop-flight
description: Find the cheapest nonstop (direct) flight between two airports for a given date or date window. Use this skill whenever the user asks about flights, airfare, plane tickets, or travel to a specific destination and prefers nonstop routing. Trigger on phrases like "cheapest flight to," "nonstop flight," "direct flight," "fly to [city]," "find me a flight," "airfare to," "what does it cost to fly to," or any time the user mentions specific origin/destination airports or cities along with dates. Also trigger when the user is researching travel costs, comparing dates, or pricing a trip, even if they did not explicitly say "nonstop"; nonstop is the default preference and should be confirmed. Do not use this skill for multi-city itineraries, award travel, or private aviation.
---

# Cheapest Nonstop Flight Finder

A repeatable workflow for finding the lowest available nonstop fare between two airports, using web search to pull live route and pricing information.

## When to use this skill

Use this skill whenever the user wants to price a flight to a destination. The default assumption is nonstop economy round-trip for one adult. Confirm anything that is unclear before searching, but do not over-interrogate the user. If they give you a city and dates, that is enough to start.

If the user explicitly wants connections, award travel, or first/business class, this skill can still help with the price comparison structure but is optimized for paid nonstop economy.

## Step 1: Capture the essentials

Confirm or infer these inputs before searching. Ask only for what is missing or ambiguous.

1. **Origin airport** (IATA code if known, otherwise nearest major airport). If the user gives a city with multiple airports (NYC, London, Tokyo, LA, Chicago, DC, Houston, Bay Area), list the nonstop-capable airports for the route and ask which they prefer, or offer to compare.
2. **Destination airport** (same rule as origin).
3. **Travel dates.** Specific dates, a range, or "flexible within a month." If flexible, note the window.
4. **Trip type.** One-way or round-trip. Default to round-trip.
5. **Passengers.** Default to one adult.
6. **Cabin.** Default to economy. Only deviate if asked.
7. **Carry-on vs checked bag.** Optional, but matters because basic-economy fares often exclude bags. Note this in the final comparison.
8. **Airline preferences or avoidances.** Loyalty programs, blocked carriers, etc.

If the user gives you everything in one shot, skip the questions and go.

## Step 2: Identify which airlines fly the route nonstop

Before pricing, confirm which carriers actually operate nonstop service on the route. This is the most important step. A "cheap flight" with one connection is not what the user asked for.

Use web_search with queries like:
- `nonstop flights [ORIGIN] to [DESTINATION]`
- `which airlines fly direct [ORIGIN] to [DESTINATION]`
- `[ORIGIN] to [DESTINATION] direct flight 2026`

Cross-reference results from at least two of: Google Flights, Kayak, Skyscanner, FlightConnections, Wikipedia airport route lists, or the airlines' own route maps.

If no carrier flies the route nonstop, stop and tell the user. Offer the shortest one-stop alternative as a fallback and ask if they want to continue.

If the route is seasonal or low-frequency (a few times a week), note that. It affects date flexibility.

## Step 3: Price the route

Run live searches in this priority order. Use the actual current date when building queries, not a hardcoded year.

1. **Google Flights** via web_search. Query format: `Google Flights [ORIGIN] [DESTINATION] [DATE] nonstop`. This is usually the most reliable aggregator and shows the cheapest nonstop fares first when filtered.
2. **Kayak** or **Skyscanner** to cross-check. These sometimes surface fares from OTAs that Google Flights misses.
3. **Direct airline sites** for the carriers identified in Step 2. Sometimes airline-direct is cheaper than the aggregators, especially Southwest (which is not listed on Google Flights at all and must be checked separately) and some ultra-low-cost carriers (Spirit, Frontier, Breeze, Allegiant, JetBlue basic, Avelo).
4. If the user has date flexibility, search the broader date grid and identify the cheapest day to fly out and back.

For each search, capture: airline, flight number if visible, departure time, arrival time, flight duration, fare class, bag inclusions, and total price for the requested passenger count.

## Step 4: Present the comparison

Output a clean comparison so the user can decide quickly. Use a table when there are three or more options. For one or two options, prose is fine.

Required columns or fields:
- Airline and flight number
- Departure airport and time
- Arrival airport and time
- Flight duration
- Fare type (basic economy, main, etc.)
- Bag policy in plain English (e.g., "carry-on included, checked bag $35")
- Total price for the trip as requested
- Where to book (airline direct vs OTA)

Sort by total price low to high. If a slightly more expensive option has materially better value (includes a bag the cheapest one excludes, departs at a sane hour vs 4am, etc.), flag it explicitly.

Always cite sources with inline citations so the user can verify.

## Step 5: Add useful context

After the comparison, give the user a short set of practical notes. Keep this tight, not a lecture. Include only what is genuinely useful for this specific route and date:

- Whether the fare looks normal, high, or low for this route based on what you saw across aggregators.
- Whether prices are likely to move (close-in dates trend up; far-out dates with low load can drop).
- Whether the cheapest option is basic economy and what that actually means on this carrier (seat assignment, boarding group, change/cancel rules, bag fees).
- Whether setting a price alert on Google Flights or Hopper makes sense given the timeline.
- Any operational notes worth knowing: known on-time performance issues, slot constraints, seasonal schedule changes.

## Search query patterns that work

A few queries that tend to return useful results, in rough order of usefulness:

- `cheapest nonstop [ORIGIN] to [DESTINATION] [MONTH YEAR]`
- `[ORIGIN] [DESTINATION] direct flight price`
- `Google Flights [ORIGIN] [DESTINATION] [DATE]`
- `Southwest [ORIGIN] [DESTINATION]` (Southwest is invisible on aggregators)
- `[AIRLINE] [ORIGIN] [DESTINATION] fare` for airline-direct pricing

Avoid stuffing operators like `site:` or quotes into queries unless you are targeting a specific source.

## Things to watch out for

- **Phantom nonstops.** Some aggregators list a flight as "1 stop" even though the marketing carrier sells it as a "direct" flight (same flight number, brief stop, no plane change). The user almost always wants a true nonstop. Filter for that.
- **Codeshare confusion.** The operating carrier matters more than the marketing carrier for bag rules, lounge access, and on-time performance. Note both if they differ.
- **Currency and totals.** Confirm prices are in the user's currency and include taxes and fees. Aggregators sometimes show base fare only at first glance.
- **Bag fees flipping the ranking.** A $180 basic-economy fare plus a $70 round-trip carry-on can be more expensive than a $220 main-cabin fare. Always compute the all-in cost when bags are relevant.
- **Airport substitutions.** If the user is flexible, a nonstop from a nearby airport (Newark vs JFK, Midway vs O'Hare, Burbank vs LAX, Oakland vs SFO) is often dramatically cheaper. Surface these only if the user mentioned flexibility or the savings are large enough to justify mentioning.
- **Stale prices.** Search results can lag actual availability by hours or days. Tell the user that the final price is whatever shows up at booking, and link them to the booking page rather than just naming a number.

## What this skill does not do

- It does not book the flight. Always direct the user to the airline site or aggregator to complete the booking.
- It does not handle award travel, points pricing, or upgrade availability.
- It does not handle multi-city or open-jaw itineraries.
- It does not store the user's credit card or personal data.
- It does not guarantee a price. Prices move. The number you report is a snapshot.

## Output template

When you finish, structure the final answer roughly like this:

```
**Cheapest nonstop options: [ORIGIN] to [DESTINATION], [DATES]**

[Table or short list of options, sorted by total price]

**My take:**
[2 to 4 sentences. Which option is the best value, what the user should know, whether to book now or wait.]

**Sources:** [inline citations throughout]
```

Keep the final response tight. The user wants a price and a recommendation, not a travel essay.
