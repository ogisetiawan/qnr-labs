# Feature Specification: Improve Landing Content

**Feature Branch**: `001-improve-landing-content`

**Created**: 2026-11-19

**Status**: Draft

**Input**: User description: "Improve the content on the landing page based on IMPROVE-CONTENT.md."

This feature specifies homepage messaging only. It does not replace `specs/specs.md`. It does not approve a visual redesign or a verified service catalog.

Owner decisions on 2026-11-19:

- The homepage sections and their approved wording come from `SECTION-SUGGESTED.md`.
- A visitor who wants to talk to QNR is sent to the closing call to action, not into a service list.
- Open source is selective. Account Switcher is not called open source while its repository is unresolved.

## User Scenarios & Testing *(mandatory)*

### User Story 1 - Find the studio and its released work (Priority: P1)

A person who uses, or might use, a QNR product opens the homepage. The opening statement tells them QNR builds its own products from real problems, and the released-work area shows the real project without invented details.

**Why this priority**: The homepage exists to say who QNR is and to show real work. The later sections depend on that being true.

**Independent Test**: Read the hero and Digital Labs only. Confirm the approved headline, the founder-led identity, and Account Switcher with its unresolved fields.

**Acceptance Scenarios**:

1. **Given** the homepage, **When** a visitor reads the hero, **Then** the headline is "Turning real problems into useful digital products." and the description is "QNR Labs is an independent digital studio building its own products and developing practical digital solutions for others."
2. **Given** the hero, **When** a visitor looks for who runs the studio, **Then** they can see that it is founder-led, and they do not see a team, a client list, or a public expansion of "QNR".
3. **Given** Account Switcher is the only released project, **When** a visitor reads Digital Labs, **Then** they see that project and the verified "100+ installs" fact, while its description, problem story, solution story, install destination, release date, screenshots, technology, license, and repository stay unresolved placeholders.
4. **Given** the hero actions, **When** a visitor chooses where to go next, **Then** the two invitations are "Explore Digital Labs" and "How We Build".

---

### User Story 2 - Ask QNR to build something (Priority: P2)

A potential client wants to know that QNR also develops solutions for other people, and wants a direct way to make contact. They are not handed a verified price list or a catalog of past work.

**Why this priority**: The approved page separates own products from work for others, and the owner chose the closing call to action as the contact path.

**Independent Test**: From the services message, follow the only contact invitation. It ends at the closing call to action. No form, price, or client name appears.

**Acceptance Scenarios**:

1. **Given** the homepage, **When** a visitor reads Digital Labs and then Services, **Then** own products and help for other people are described as different activities.
2. **Given** the Services section, **When** a visitor reads the four example categories, **Then** those categories are not presented as a verified offer list, a price list, or proof of past clients.
3. **Given** a visitor wants to contact QNR, **When** they look for how to do that, **Then** the closing call to action is the place that invites direct contact, it has no contact form, and Email and GitHub stay unresolved where the address is unknown.

---

### User Story 3 - See the approach once, and see what is shared (Priority: P3)

A collaborator wants the development approach in one place, and wants an honest statement that only selected projects are published as open source.

**Why this priority**: The live page repeats the same story and uses "open source" as a blanket identity. The owner chose one approach section and selective sharing.

**Independent Test**: Count approach step lists. Read the open-source section and Account Switcher. The six stages appear once, and Account Switcher is not labeled open source.

**Acceptance Scenarios**:

1. **Given** the homepage, **When** a visitor reads Development Approach, **Then** they see the six stages Discover, Define, Design, Build, Validate, and Deliver, and they are told this is a recommended framework rather than a rigid path for every project.
2. **Given** the homepage, **When** a visitor looks for those stages outside Development Approach, **Then** they do not find a second copy of the same sequence.
3. **Given** the open-source section, **When** a visitor reads it, **Then** it says QNR publishes selected projects and does not say that every project is open source.
4. **Given** Account Switcher's repository is unresolved, **When** a visitor reads that project or the labs summary, **Then** it is not labeled open source, and a blanket "Open source" statistic is absent.

---

### Edge Cases

- Digital Labs has one project. Counts and headings must not imply a larger catalog.
- The only confirmed metric is "100+ installs". No second metric is added.
- A sample card in the section notes ("Productivity", a sample problem sentence, "[Actual stack]", "[Actual license]") is a pattern, not Account Switcher content. Those values stay unresolved for Account Switcher.
- A destination address is unresolved. The page must not link that project, or the call to action, to a guessed store, repository, or email.
- The four service categories are hypotheses. A visitor must not be able to read them as launched offers.
- About, FAQ, and a separate Contact section are not part of this homepage. Contact happens in the closing call to action.
- The footer stays as it is, including its unresolved GitHub and Email labels.

## Requirements *(mandatory)*

### Functional Requirements

- **FR-001**: The hero MUST use the headline "Turning real problems into useful digital products." and the description "QNR Labs is an independent digital studio building its own products and developing practical digital solutions for others." The hero MUST also say the studio is founder-led. It MUST NOT say the studio itself is an open-source identity.
- **FR-002**: The homepage MUST NOT say "our team", name a team, show a client, show a testimonial, show a price, or publish an expansion of "QNR".
- **FR-003**: The only install metric on the homepage MUST be "100+ installs" for Account Switcher.
- **FR-004**: Account Switcher's short description, problem story, solution story, feature bullets, install destination, release date, screenshots, technology, license, repository, and personal-problem story MUST remain unresolved placeholders until the owner supplies them.
- **FR-005**: The hero actions MUST be "Explore Digital Labs" and "How We Build". "How We Build" leads to Development Approach.
- **FR-006**: Development Approach MUST be the only section that lists the path from a problem to a released product. Its heading is "Thoughtful development, from idea to release." Its stages are Discover, Define, Design, Build, Validate, and Deliver, with the meaning given in `SECTION-SUGGESTED.md`. The section MUST say these stages are a recommended framework, not a rigid sequence for every project.
- **FR-007**: Digital Labs MUST list only real projects and the status the product spec already allows. Today those statuses are released and in progress. A project MUST NOT be given a destination, category, stack, or license that is still unresolved.
- **FR-008**: The homepage MUST NOT add a contact form, a booking flow, a pricing block, a blog, a team block, an About section, or an FAQ section.
- **FR-009**: The footer MUST stay as it is. Its purpose line MAY remain "Building useful software, tools, and digital solutions." Unresolved Email and GitHub labels MUST stay labeled unresolved.
- **FR-010**: The homepage content order MUST be Hero, Development Approach, Digital Labs, Services, Open Source, a closing call to action, then the current footer.
- **FR-011**: Services MUST use the heading "Turning your ideas into practical digital solutions." and the description "From early concepts to working products, QNR Labs helps turn ideas and real-world challenges into practical digital solutions through thoughtful development and iterative experimentation." Web Development, Digital Product Development, Custom Software, and Technical Solutions MAY appear only as unconfirmed examples. They MUST NOT be presented as a verified catalog, a price list, or evidence of past clients. The section MUST NOT be the contact path.
- **FR-012**: The open-source section MUST say that QNR publishes selected projects and MUST NOT say that every project is open source. A project MAY be called open source only when its public repository is confirmed. Account Switcher MUST NOT be called open source while its repository is unresolved. The homepage MUST NOT show a blanket "Open source" statistic.
- **FR-013**: The closing call to action MUST be the only invitation to contact QNR directly. It MUST offer the existing public channels, keep unknown addresses unresolved, and MUST NOT include a form or repeat the six stages or the example service categories.

### Key Entities

- **Published project**: A real piece of work in Digital Labs. A visitor may see its name, summary, status, one verified highlight, and a destination. For Account Switcher, the verified highlight is "100+ installs". Summary, problem, solution, destination, technology, license, and repository may be unresolved.
- **Homepage section**: One visitor-facing block in the order in FR-010, with the heading and supporting statement named in this spec. Layout references in the section notes are not part of the section.

## Success Criteria *(mandatory)*

### Measurable Outcomes

- **SC-001**: A visitor can read the approved hero headline and description, and can also point to the words that say the studio is founder-led, without finding a team claim.
- **SC-002**: A visitor can find Account Switcher and the "100+ installs" fact in Digital Labs, and can find zero other install or audience metrics.
- **SC-003**: The six development stages appear in one section. A second copy of that sequence is a failure.
- **SC-004**: Every unresolved project, license, technology, or contact value that is visible remains labeled unresolved. None have been replaced by the sample card text.
- **SC-005**: A visitor looking for prices, testimonials, client names, the phrase "our team", a contact form, About, or FAQ finds none of them on the homepage.
- **SC-006**: A visitor cannot find a sentence that says every QNR project is open source, and cannot find Account Switcher labeled open source.
- **SC-007**: A visitor who wants to contact QNR finds that invitation only in the closing call to action.
- **SC-008**: A visitor can list the content sections in this order: Hero, Development Approach, Digital Labs, Services, Open Source, call to action, footer.

## Assumptions

- `specs/specs.md` remains the product specification. This feature records a later homepage decision. It does not edit that file. The product spec's older homepage sequence, and its deferral of a capabilities section, differ from this approved page. That difference stays recorded here until the owner updates the product spec.
- The audience remains people who use released work, people who might ask QNR to build something, and people who might collaborate later.
- English is the language of the homepage.
- This feature changes words and which messages appear. It does not add pages or a new visual system. Layout links in `SECTION-SUGGESTED.md` are references only and are not requirements.
- "Experimental" is not added as a project status.
- The four service names are the owner's hypotheses from `SECTION-SUGGESTED.md`. They are not confirmed offers.
- About and FAQ stay off the homepage. They remain separate pages in the product spec, outside this feature.
- The previous candidate steps Notice, Define, Build, Test, Release, and Share are replaced by the six stages in FR-006.
