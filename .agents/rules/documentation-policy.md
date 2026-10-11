---
trigger: always_on
description: "Mandatory project documentation lifecycle, working drafts, stable releases, and historical archives."
---

# Project Documentation Policy

## 1. Mandatory First Step
- Before planning, designing, implementing, modifying, testing, or reviewing a feature, read `docs/README.md`.
- Read the relevant documents in `docs/stable/` first.
- Read relevant documents in `docs/working/` to understand ongoing plans.
- Consult `docs/history/` only when previous decisions, releases, or changes are relevant.
- Never assume an archived document describes current requirements.

## 2. Documentation Categories

### Working — docs/working/
- Use for new ideas, initial planning, proposed requirements,
  feature development, experiments, and ongoing improvements.
- Working documents may change frequently.
- Mark unapproved decisions and assumptions clearly.
- Do not represent a proposal as an approved requirement.

### Stable — docs/stable/
- Contains the current approved source of truth.
- Promote documentation only after review and explicit approval.
- Keep requirements, architecture, implementation, and testing
  documentation consistent with one another.
- Never silently overwrite an approved version.

### History — docs/history/
- Preserve previous stable versions when a new stable version
  is approved and released.
- Retain original content, version, release date, and context.
- Do not edit historical records to make them match current behavior.
- Treat historical documentation as read-only.

## 3. Planning and Implementation
- Identify affected documentation before starting a task.
- Record new requirements and proposed changes in Working.
- Check for conflicts with existing Stable requirements.
- If requirements conflict or are unclear, explain the conflict
  and ask for clarification instead of guessing.
- Update Working documentation as decisions and implementation
  details evolve.
- Do not change Stable documentation merely because code changed.

## 4. Stable Release Process
- Prepare the proposed release and change summary.
- Validate requirements, architecture, implementation, tests,
  dependencies, security, and cross-document consistency.
- Request explicit human approval before promotion.
- Preserve the previous Stable version in History.
- Publish the approved replacement in Stable.
- Update version numbers, release notes, dates, and document links.
- Keep the archive and current documentation synchronized.

## 5. Version and Traceability
- Give each stable release a version identifier.
- Record status, owner, last-updated date, and approval status.
- Maintain a changelog explaining what changed and why.
- Link significant requirements to related features and tests.
- Never fabricate approval, test results, or release dates.

## 6. Agent Restrictions
- Do not promote drafts, archive versions, or release documentation
  without explicit approval.
- Do not delete historical documentation as part of routine cleanup.
- Do not start implementation when a blocking requirement is unclear.
- If a requested change affects Stable requirements, explain the
  impact and propose Working-document updates first.
- Before finishing, report which documents were read, created,
  modified, or proposed for approval.

## 7. Completion Requirement
Every planning or implementation task must state:
1. Relevant documentation reviewed.
2. Working documents changed or created.
3. Stable documents affected, if any.
4. Unresolved questions and assumptions.
5. Tests or validation performed.
6. Any approval needed before promotion.
