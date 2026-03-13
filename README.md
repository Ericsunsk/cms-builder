# cms-builder

Platform-agnostic skill for AI agents that need to design backend CMS content models from mixed requirements.

It helps an agent:

- turn business goals, page lists, and draft entities into a usable CMS model
- decide what should live in the CMS and what should stay in other systems
- avoid over-design, speculative abstractions, and weak relationship complexity
- produce either a first-pass draft or a fuller implementation-ready handoff

## What This Skill Does

`cms-builder` is not tied to Strapi, Directus, Sanity, Contentful, or a custom CMS implementation.

It focuses on method:

- normalize mixed inputs
- resolve contradictions
- define content domains, entities, fields, and relationships
- separate CMS-managed content from business-system truth
- produce a clear handoff package for downstream implementation

## What It Does Not Do

- generate vendor-specific schema syntax
- configure a CMS product or plugin system
- design pure navigation / UX information architecture with no CMS-modeling question
- replace database, API, or frontend implementation work

## Workflow

### Phase 1

Use when the request is still assumption-driven.

Output:

- likely content domains
- core entities
- CMS-in vs CMS-out boundary notes
- assumptions
- must-confirm questions

### Phase 2

Use when the CMS purpose, major domains, core entities, and ownership boundaries are stable enough for field-level design.

Output:

1. Scope and Objective
2. Input Summary and Assumptions
3. Suggested Content Domains
4. Content Entities and Responsibilities
5. Field-Level Specification
6. Relationships, Reusable Components, and Boundaries
7. Risks and Over-Design Review
8. Implementation Notes

## Repository Structure

```text
.
├── SKILL.md
├── README.md
├── agents/
│   └── openai.yaml
└── references/
    ├── modeling-heuristics.md
    ├── output-template.md
    └── red-flags.md
```

## Example Prompts

- `帮我设计后端 CMS 架构`
- `帮我梳理网站内容类型和字段结构`
- `帮我判断哪些数据应该进 CMS，怎么建模`
- `帮我把这些页面需求整理成 CMS schema`

## Key Design Rules

- Prefer the simpler model unless complexity has clear governance or reuse value.
- Do not force transactional or operational source-of-truth data into the CMS.
- Do not model page layout slots as durable content structures by default.
- Mark missing details as `unknown` and postponed choices as `defer`.

## Validation

This repository is a single skill package at the repo root.

Validation command:

```bash
python /path/to/quick_validate.py /path/to/cms-builder
```

## Notes

- If you need platform-specific mapping, pair this skill with separate platform-specific tools or MCP integrations.
- The repo root is the skill package root.
