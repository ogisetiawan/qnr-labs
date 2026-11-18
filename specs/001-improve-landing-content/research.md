# Research: Improve Landing Content

## Decision: Keep the current static stack

**Rationale**: The site is already Astro, static output, TypeScript 6, Tailwind CSS v4, and Node.js 26. The feature changes homepage words and section order. No requirement needs a new package, island, or server route.

**Alternatives considered**: A content-collection migration for Account Switcher. Rejected for this feature because the product spec still has unresolved project fields, and this feature does not add a project. Moving storage would be a different change.

## Decision: Reuse the homepage components

**Rationale**: `Hero`, `Process`, `DigitalLabs`, `Services`, `Contact`, and `SiteFooter` already exist and use the current visual system. New copy belongs in those components. `OpenSource.astro` is the one new section, built with the same container and section pattern.

**Alternatives considered**: Rebuild the page from the linked reference layouts. Rejected. Those links are not requirements, and the constitution forbids a new aesthetic.

## Decision: Show Development Approach once

**Rationale**: `Process.astro` and `IdeaPath.astro` both tell the path from a problem to a product, and `Services.astro` tells it again. The feature allows that path in one section. `Process.astro` becomes Development Approach, with the six approved stages and the sentence that they are a recommended framework. `IdeaPath.astro` is removed from `index.astro` and its file is kept.

**Alternatives considered**: Keep both visuals and change only the words. Rejected because the visitor would still read two sequences.

## Decision: Point "Explore Digital Labs" at the homepage section

**Rationale**: Digital Labs is on the homepage, and the success criteria are met there. The action target is `#labs`. "How We Build" targets the approach section. `/labs` already exists, and its current description says "Released open-source projects." That sentence conflicts with selective open source. This feature does not change `/labs`; the conflict is reported and left for a later decision.

**Alternatives considered**: Send "Explore Digital Labs" to `/labs`. Rejected for this feature because that page's current description overclaims open source.

## Decision: Replace the open-source identity, not every mention

**Rationale**: The hero eyebrow "Open Source Digital Labs" and the Digital Labs stat "Open source" present open source as the studio identity. The owner chose selective sharing. The eyebrow states that the studio is founder-led. The stat is removed. A dedicated section says QNR publishes selected projects and does not publish every project. Account Switcher is not labeled open source while its repository is unresolved.

**Alternatives considered**: Keep the eyebrow and add a qualifier. Rejected because the eyebrow would still define the studio as open source.

## Decision: Keep service names as labeled examples

**Rationale**: The owner supplied four names and also said they are hypotheses, not verified capabilities. The Services heading and description are the approved sentences. The four names render only with a visible statement that they are not a confirmed offer. They are not links, prices, or the contact path.

**Alternatives considered**: Drop the four names to avoid any catalog reading. Rejected because the owner included them in the chosen section note, with that warning attached.

## Decision: Use Contact as the closing call to action

**Rationale**: Direct contact is the closing section. `Contact.astro` already lists Email and GitHub as unresolved and has no form. It moves to the end of `main`, before the footer. Its heading and lede stay a plain invitation to contact QNR through a public channel. No new slogan is added. The footer is unchanged.

**Alternatives considered**: Add a second call-to-action component and keep Contact. Rejected because the page would then have two contact invitations.

## Decision: Leave unresolved project fields unresolved

**Rationale**: The section note's sample card uses "Productivity", a sample problem sentence, "[Actual stack]", and "[Actual license]". Those are patterns. Account Switcher keeps `[TBD]` for description, install destination, date, and the other unconfirmed fields. "100+ installs" remains the only metric. No personal-problem story is written.

**Alternatives considered**: Fill the sample sentence into Account Switcher so the card looks complete. Rejected. That would invent the product story.
