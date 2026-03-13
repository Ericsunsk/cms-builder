# CMS Builder Output Template

Use Phase 1 when domains, ownership, relationships, or field detail are still assumption-driven. Use Phase 2 when the CMS purpose, main domains, core entities, major relationships, and CMS ownership boundary are stable enough to support field-level specs with only limited `unknown` or `defer`.

If a template detail matters but the input does not support it, mark it `unknown` or `defer` instead of guessing or silently omitting it. Use `unknown` when the answer should exist but is not yet known. Use `defer` when the decision should be made later during implementation or governance alignment.

## Phase 1 Draft Template

Use this compact form for a first-pass model. Keep it useful, bounded, and assumption-aware. Do not fabricate a full field catalog.

### Objective and Scope
- What the CMS is likely meant to support:
- What is in scope for this draft:
- What is clearly out of scope:

### Assumptions
- Assumption 1:
- Assumption 2:
- Contradictions or missing inputs that could materially change the model:

### Suggested Content Domains
- Domain:
- Why this domain exists:
- Main responsibility:

### Candidate Entities
- Entity:
- Purpose:
- Why it should exist now:
- Why it should stay embedded or separate for now:

### CMS-in vs CMS-out Notes
- Belongs in CMS:
- Should stay outside CMS:
- Boundary note:

### Must-Confirm Questions
- Question 1:
- Question 2:
- Question 3:

### Mini Example
- Objective and Scope: Support marketing pages and brand storytelling. Inventory and pricing stay out of CMS.
- Assumptions: Product data already exists elsewhere. Editors own brand copy and campaign blocks.
- Suggested Content Domains: Brand content, marketing pages, global settings.
- Candidate Entities: Brand, marketing page, reusable CTA block.
- CMS-in vs CMS-out Notes: Brand story and hero copy in CMS; live inventory out.
- Must-Confirm Questions: Should CTAs be managed globally? Do pages need localized slugs now?

## Phase 2 Full Template

Use this form only when the model is stable enough for field-level implementation-prep detail. Stay platform-agnostic. Do not invent unsupported workflow, localization, SEO, or relationship complexity.

## Scope and Objective

State what the CMS is intended to support, what is in scope now, and what is intentionally out of scope. Keep this about business and editorial purpose, not platform syntax.

- CMS purpose:
- In scope now:
- Out of scope now:

## Input Summary and Assumptions

Summarize confirmed facts from the input, then list assumptions used to move forward and missing details that could change the model. Call out contradictions plainly.

- Confirmed facts:
- Assumptions used to proceed:
- Material unknowns or conflicts:

## Suggested Content Domains

Group content by governance, ownership, lifecycle, and editorial responsibility. Do not group by page regions or screen layout alone.

- Domain:
- Why this domain exists:
- Main responsibilities:
- Notes on ownership or governance:

## Content Entities and Responsibilities

For each entity, explain what it represents, why it should exist, why it should not simply be merged into something else, and what governance or reuse value it adds.

- Entity:
- Represents:
- Why it exists:
- Governance or reuse value:
- Why not merged with another entity:
- Notes on ownership or lifecycle:

## Field-Level Specification

List only fields you can support from the input. Every field should have a real editorial purpose. If a required detail is unsupported, write `unknown` or `defer`.

Base field contract for every field:

- Entity:
- Field name:
- Field purpose:
- Data type:
- Required vs optional:
- Ownership or placement note if boundary is non-obvious:

Conditional attributes, only when relevant:

- Enum or constrained values:
- Default value:
- Localization need:
- Slug need:
- SEO extension need:
- Relationship reference:
- Publishing/state implications:
- Editorial usage notes:

For each conditional attribute, write `yes`, `no`, `unknown`, `not needed`, or `defer` when that makes the decision clearer than omission.

## Relationships, Reusable Components, and Boundaries

Describe entity relationships, reusable block candidates, embed-versus-split decisions, and what data should remain outside the CMS. Only recommend relationships or reusable components when the governance value is clear.

- Relationship:
- Why it exists:
- Reuse or governance benefit:
- What should remain embedded:
- What should stay outside CMS:
- Boundary notes:

## Risks and Over-Design Review

Scan for unnecessary splits, speculative abstraction, presentation-model leakage, premature componentization, and complexity with weak governance value. Prefer the simpler model unless complexity is clearly justified.

- Risk:
- Why it is a risk:
- Simpler alternative:
- What would justify added complexity later:

## Implementation Notes

Recommend a minimum viable rollout, note complexity that can be deferred, list cross-team questions, and leave handoff notes for later platform-specific execution. Do not write product-specific schema syntax here.

- Minimum viable rollout:
- Deferred complexity:
- Open questions for frontend, backend, search, or operations:
- Notes for future platform-specific implementation:
