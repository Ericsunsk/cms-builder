# CMS Builder Red Flags

Run this scan before finalizing the model. If multiple red flags appear, simplify first and only add complexity when there is clear editorial or governance value.

## Speculative Future-Proofing

Anti-pattern:
Creating entities, fields, or relationships for hypothetical future scenarios with no current owner, workflow, or reuse case.

Simplify by:
Model only confirmed needs now, and capture possible future expansion as a note or `defer`.

## Presentation-Model Leakage

Anti-pattern:
Turning page regions, tabs, cards, carousels, or layout slots directly into durable content entities just because they appear on a screen.

Simplify by:
Group by content ownership and lifecycle, and keep display-only structure embedded or outside the durable content model.

## Premature Component Extraction

Anti-pattern:
Extracting a reusable component after one or two repeated field groups even though reuse, ownership, and lifecycle are still unstable.

Simplify by:
Keep the structure local until reuse is stable or independent editing, permissions, or scheduling clearly justify extraction.

## Defaulting Every Entity to SEO, Localization, or Workflow Complexity

Anti-pattern:
Adding slug rules, SEO fields, localization support, approval states, or versioning expectations to every entity by default.

Simplify by:
Add each concern only where there is a real current requirement, and mark unsupported decisions `unknown` or `defer`.

## Relationship Complexity Without Governance Value

Anti-pattern:
Adding references, join-like structures, or reusable block layers because they look more flexible, even though the content is edited together and has no independent reuse, ownership, or lifecycle.

Simplify by:
Embed the structure until reuse, permissions, independent publishing, or clearer governance boundaries actually justify the relationship.

## Forcing Transactional or Authoritative Business Data into CMS

Anti-pattern:
Storing inventory, price truth, order state, payment state, or other operational truth in the CMS because one screen needs to display it.

Simplify by:
Keep authoritative business data in the proper source system, and let the CMS hold only the authored copy, curation, or references around it.

## Quick Scan

Ask these before you finalize:

- Are we modeling a future possibility instead of a current editorial need?
- Are we naming entities after page sections instead of governance boundaries?
- Are we extracting components before reuse and ownership are proven?
- Are we assuming every entity needs SEO, localization, and workflow complexity?
- Are we putting business-system truth in the CMS for convenience?
