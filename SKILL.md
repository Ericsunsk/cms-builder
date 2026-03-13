---
name: cms-builder
description: Use when designing backend CMS content structures, CMS information architecture, content types, entities, fields, relationships, or deciding what should and should not live in a CMS from mixed product, page, or content requirements
---

# CMS Builder

## Overview

Turn mixed product, page, and editorial inputs into a CMS content model that is useful, minimal, and implementation-ready. Keep the model platform-agnostic, separate CMS-owned content from business-system truth, and prevent over-design. If little or no data belongs in the CMS, say so explicitly.

## Trigger Boundaries

Use this skill to:

- define content domains, entities, fields, and relationships
- decide what should live in the CMS versus code, commerce, search, or other systems
- shape a CMS model from mixed inputs such as business goals, page lists, and draft entities

Do not use this skill to:

- map the model to vendor-specific CMS schema syntax, plugins, or configuration
- design pure navigation trees or UX information architecture with no real CMS-modeling question
- define database schemas, API payloads, frontend rendering logic, or migrations

If the request is mostly pure navigation or page-tree work, narrow the answer to the CMS-relevant subset instead of forcing a full content model. Platform-specific mapping belongs to other tools or skills.

## Non-Goals

- Do not model every UI section as CMS content by default.
- Do not move transactional or operational source-of-truth data into the CMS without clear editorial ownership.
- Do not invent speculative entities, fields, or taxonomies.
- Do not silently hide missing required detail; use `unknown`.
- Do not silently hide postponed decisions; use `defer`.
- Do not optimize for a specific platform before the content model is stable.

## Core Workflow

### Phase 0: Normalize Input

- extract business goals, page or surface inventory, editorial needs, draft entities, reuse signals, governance needs, and unknowns
- separate explicit facts from inferred structure

### Phase 0.5: Resolve Conflicts

- explicit user facts and constraints override inferred structure
- repeated signals can strengthen a conclusion, but never override explicit user facts or constraints
- inferred structure must be labeled as assumption
- when conflicts affect entity boundaries, CMS ownership, or reuse strategy, prefer the simpler model and surface a must-confirm question
- do not silently merge contradictions into a larger schema
- call out contradictions plainly
- state the assumption used to proceed
- identify what answer would materially change the model

### Phase 1: First-Pass Model

Use this when the model is still assumption-driven. Produce:

- likely content domains
- core entities
- obvious reusable blocks or components
- high-confidence relationships
- CMS-in versus CMS-out notes
- explicit assumptions
- must-confirm questions

Use the compact Phase 1 structure from `references/output-template.md`. Do not fabricate a full field catalog or reuse the Phase 2 headings.

### Phase 2: Full Handoff Package

Use this when the model is stable enough for field-level implementation-prep detail. Stay platform-agnostic. Mark unsupported details as `unknown` or `defer` instead of guessing.

## Phase Selection

Stay in Phase 1 when one or more of these are true:

- core content domains are still uncertain
- entity boundaries are still heavily assumption-driven
- CMS-versus-non-CMS ownership is materially unclear
- editorial workflow or governance expectations are unknown
- field-level detail would mostly be fabricated rather than inferred

Move to Phase 2 only when all of these are true:

- the primary CMS purpose is understood
- the main domains and core entities are stable enough to name
- the major relationships are understandable at a high level
- the CMS ownership boundary is mostly clear
- enough context exists to produce field-level specs with only limited `unknown` or `defer`

When uncertain, default to Phase 1 and state what is still needed to complete Phase 2.

## Output Contract

When you enter Phase 2, use these exact headings in this order:

1. Scope and Objective
2. Input Summary and Assumptions
3. Suggested Content Domains
4. Content Entities and Responsibilities
5. Field-Level Specification
6. Relationships, Reusable Components, and Boundaries
7. Risks and Over-Design Review
8. Implementation Notes

In that output:

- distinguish confirmed facts from assumptions
- require a real editorial or governance purpose for each entity and field
- make `Field-Level Specification` include at minimum: field name, field purpose, data type, required vs optional, and an ownership or placement note when the boundary is non-obvious
- represent conditional field attributes explicitly as `yes`, `no`, `unknown`, `not needed`, or `defer` when relevant, instead of leaving them implicit
- make `Relationships, Reusable Components, and Boundaries` justify every relationship or reusable block with governance or reuse value
- make `Risks and Over-Design Review` name the risk, the simpler alternative, and what would justify complexity later
- make `Implementation Notes` recommend a minimum viable rollout and defer platform-specific execution detail
- use `unknown` instead of silent omission for missing required detail
- use `defer` for decisions that should be postponed
- surface must-confirm questions when they change boundaries, ownership, or reuse strategy
- keep recommendations platform-agnostic

## Guardrails

- Prefer the simpler model unless complexity has clear governance, reuse, or lifecycle value.
- Model durable content, not component trees or page layout slots.
- Keep high-churn business truth out of the CMS unless editors truly own it.
- Reuse structures when content intent matches; do not fork early for cosmetic differences.
- If the simplest correct answer is "this should not live in the CMS," state it directly.

## Reference File Usage

- `references/output-template.md`: use for the compact Phase 1 structure, the Phase 2 headings, and a short worked example
- `references/modeling-heuristics.md`: use for embed-versus-split, CMS-in-versus-CMS-out, and relationship-complexity decisions
- `references/red-flags.md`: use before finalizing the model to scan for over-design and simplification opportunities
