# CMS Builder Heuristics

Use these defaults unless the input gives a strong reason to do otherwise.

## Separate by Governance, Not by Screen Layout

Do not create separate entities just because content appears in different places on a screen. Split only when ownership, lifecycle, permissions, or reuse are meaningfully different.

## Model Core Content Before Support Configuration

Start with the primary authored content: articles, guides, campaigns, brands, FAQs, case studies, or other core editorial objects. Add support configuration such as navigation, SEO settings, labels, and global options only after the core content model is stable.

## Require Real Editorial Purpose for Each Field

Every field should answer three questions:

- Who edits this?
- Why do they edit it?
- Where is it actually used?

If a field does not serve a real editorial, operational, or delivery purpose, remove it or defer it.

## Use Relationships Only When Governance Value Is Clear

Separate entities and relationships are justified when they improve reuse, permissions, independent publishing, lifecycle management, or long-term editorial clarity. If content is always edited together and not reused, embedding is usually the better default.

## Treat CMS as Content Source, Not Business-System Source of Truth

Use the CMS for authored content, curated messaging, and structured editorial data. Do not make it the authoritative source for transactional, real-time, computed, or operational business data unless the use case clearly requires CMS ownership.

## Four-Question Complexity Test

Before splitting an entity, extracting a reusable component, or adding a relationship, ask:

1. Is this managed independently?
2. Is it reused across multiple contexts?
3. Does it have a distinct lifecycle or permission boundary?
4. Will keeping it simple create near-term duplication or governance problems?

If the answer is mostly "no" or "not yet," prefer the simpler model.

## Embed vs Split Example

Example: a campaign landing page has a CTA with label, URL, disclaimer, and optional badge.

Embed when:

- the CTA is only used on that page
- the same editor manages it with the page
- it has no independent lifecycle

Split into a separate entity or reusable block when:

- the same CTA is reused across multiple pages
- it is scheduled or approved independently
- a different team owns it

## CMS-in vs CMS-out Example

Belongs in CMS:

- homepage hero copy
- article body content
- brand story and positioning text
- help-center articles
- campaign legal copy curated by editors

Should stay outside CMS:

- inventory counts
- live pricing truth
- order status
- payment state
- fulfillment state

If editors need to influence how business data is presented, keep the authoritative data in the business system and let the CMS store the surrounding copy, labels, or curated display rules.
