# Quickstart: Improve Landing Content

Validation guide for the homepage content contract. It does not contain the implementation.

## Prerequisites

- The feature spec, [data-model.md](./data-model.md), and [contracts/homepage-sections.md](./contracts/homepage-sections.md) are the checks.
- Node.js 26 and pnpm are already pinned.
- No new package is installed.

## Setup

Open the homepage after implementation. The owner starts the local server with `pnpm dev` only when they want that check. This guide does not require a browser session from the agent.

## Checks

Read `/` from top to bottom.

1. The blocks appear as Hero, Development Approach, Digital Labs, Services, Open Source, contact call to action, footer.
2. The hero headline, description, founder-led wording, and two action labels match the contract.
3. "Explore Digital Labs" moves to Digital Labs on the same page. "How We Build" moves to Development Approach.
4. The six stages appear once, with the framework disclaimer.
5. Digital Labs shows Account Switcher, "100+ installs", and the existing `[TBD]` labels. It does not show a second metric, a sample problem sentence, or an "Open source" statistic.
6. Services uses the approved heading and description. Any of the four example names is marked as not a confirmed offer.
7. Open Source says sharing is selective. Account Switcher is not labeled open source.
8. Direct contact appears only in the closing call to action. Email and GitHub stay unresolved. There is no form.
9. The footer text is unchanged.
10. The page does not show About, FAQ, a team, a price, a client, or a testimonial.

## Commands the owner may run

- `pnpm exec astro check` after type changes.
- `pnpm build` when a milestone check is requested.

Expected result: both succeed, and the built homepage still passes the ten checks. Neither command is part of planning.

## Out of scope for this check

`/labs` currently describes released work as open source. This feature does not change that page. A pass on `/` does not mean `/labs` matches the selective open-source decision.
