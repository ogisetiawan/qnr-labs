# Data Model: Improve Landing Content

The homepage reads two kinds of content. Neither is a new stored record. There is no status workflow and no new collection.

## Published project

Source today: `src/data/labs.ts`. This feature does not add or rename fields.

| Field | Rule |
| --- | --- |
| title | Required. Confirmed value: Account Switcher. |
| category | Shown only when it is a confirmed project category. The sample word "Productivity" is not Account Switcher's category. |
| status | `Released` or `In Progress` only. "Experimental" is not a value. |
| summary | One sentence. Account Switcher stays `[TBD — short description]`. |
| highlight | The only confirmed highlight is `100+ installs`. No second metric is added. |
| install | Destination. Stays `[TBD]` until the owner supplies it. No guessed store link. |
| date | Stays `[TBD]`. |

Problem story, solution story, technology, license, repository, screenshots, and feature bullets are not fields in the current record. They are not added with invented values. A project may be called open source only when a confirmed repository exists. Account Switcher has none, so it is not open source in this model.

The homepage may show a count of released projects derived from these records. With one released project, the count is 1.

## Homepage section

Order is fixed. Copy that is approved is quoted in the feature spec. Copy that is not approved is not invented here.

| Order | Section | Required content | Must not contain |
| --- | --- | --- | --- |
| 1 | Hero | Approved headline and description. The words founder-led. Actions "Explore Digital Labs" and "How We Build". | An open-source identity for the studio. A team claim. |
| 2 | Development Approach | Heading "Thoughtful development, from idea to release." Stages Discover, Define, Design, Build, Validate, Deliver. A statement that the stages are a recommended framework. | A second copy of the stages elsewhere. A claim that every project follows all six. |
| 3 | Digital Labs | Real projects only, under the rules above. | A blanket "Open source" statistic. Sample-card values used as facts. |
| 4 | Services | Approved heading and description. Four names only as unconfirmed examples: Web Development, Digital Product Development, Custom Software, Technical Solutions. | Prices, clients, a verified catalog, or the contact invitation. |
| 5 | Open Source | Selected projects are published. Not every project is open source. | Account Switcher labeled open source. |
| 6 | Contact call to action | The only direct-contact invitation. Existing Email and GitHub channels. | A form. Guessed addresses. The six stages. The four service names. |
| 7 | Footer | Current purpose line and current unresolved channel labels. | New claims. |

## Relationships

- Digital Labs shows zero or more published projects. Today it shows one.
- "Explore Digital Labs" moves the visitor to Digital Labs on the same page.
- "How We Build" moves the visitor to Development Approach.
- Services does not link into the contact call to action as a list of offers. The contact call to action is a later section, not a child of Services.

## Validation

- A visible project value that the owner has not supplied is still a `[TBD]` label.
- Service names, when visible, are accompanied by the statement that they are not a confirmed offer.
- The six stage names appear in Development Approach and nowhere else on the homepage.
