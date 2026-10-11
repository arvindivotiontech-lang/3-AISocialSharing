# Antigravity Project Documentation Management

## 1. Purpose

Before actual project development begins, establish a consistent documentation management process so that AI agents and developers use the correct project context, preserve decisions, and distinguish proposed changes from approved requirements.

The documentation system has three categories:

1. **Working** — evolving and non-final planning.
2. **Stable** — current, approved documentation.
3. **History** — preserved previous stable releases.

The documentation policy must be reviewed before planning or implementation work begins.

## 2. Documentation Categories

### 2.1 Working / Non-Stable

**Folder:** `docs/working/`

Use this category for:

- Initial project planning and requirements.
- New feature proposals and improvements.
- Experiments and alternative approaches.
- Ongoing design and architecture discussions.
- Bug investigations and proposed fixes.
- Unresolved questions, assumptions, risks, and dependencies.
- Changes that are not yet approved as final.

Rules:

- Working documents may change frequently.
- Clearly label proposals, assumptions, and unresolved decisions.
- Update an existing relevant draft instead of creating duplicates.
- Do not represent a proposal as an approved requirement.
- Do not promote a document to Stable without explicit approval.

### 2.2 Stable / Approved

**Folder:** `docs/stable/`

Use this category for current, reviewed, approved documentation, including:

- Approved business requirements.
- Functional and non-functional requirements.
- Architecture and design.
- API and database specifications.
- Security and development standards.
- Testing and deployment procedures.
- Approved feature specifications and decisions.

Rules:

- Stable documentation is the current source of truth for approved requirements.
- Review relevant Stable documents before planning or changing a feature.
- Do not silently overwrite or alter approved documentation.
- If implementation or a new request conflicts with Stable documentation, explain the conflict and propose an update in Working.
- Publish changes to Stable only after review and explicit approval.

### 2.3 History / Archived

**Folder:** `docs/history/`

Use this category to preserve previous Stable versions when a new Stable release is approved.

Rules:

- Preserve the previous stable release as an unmodified snapshot.
- Retain its version number, release date, approval information, and release notes.
- Record what changed and why.
- Treat archived documents as read-only.
- Do not use historical requirements as current requirements without checking the latest Stable documentation.
- Do not delete historical records as part of routine cleanup.

## 3. Documentation Lifecycle

Follow this lifecycle for requirements, features, architecture, and other project documentation:

1. **Capture:** Record a new idea or change request in `docs/working/`.
2. **Review context:** Read relevant Stable documents, current Working drafts, and relevant History when needed.
3. **Plan:** Identify affected requirements, features, architecture, dependencies, risks, and tests.
4. **Iterate:** Update Working documents as the proposal changes.
5. **Validate:** Check completeness, consistency, implementation evidence, security implications, and test results where applicable.
6. **Prepare release candidate:** Summarize proposed Stable changes and outstanding issues.
7. **Request approval:** Obtain explicit human approval before promotion.
8. **Archive:** Preserve the previous Stable version in `docs/history/`.
9. **Publish:** Move or copy the approved release candidate into `docs/stable/`.
10. **Record:** Update version metadata, release notes, indexes, and links.

If approval is denied or blockers remain, keep the candidate in Working. Do not automatically promote drafts.

## 4. Recommended Repository Structure

```text
your-project/
├── AGENTS.md
├── .agents/
│   ├── rules/
│   │   └── documentation-policy.md
│   └── skills/
│       └── documentation-management/
│           └── SKILL.md
│
└── docs/
    ├── README.md
    ├── working/
    │   ├── README.md
    │   ├── requirements/
    │   ├── features/
    │   ├── architecture/
    │   └── decisions/
    ├── stable/
    │   ├── README.md
    │   ├── requirements/
    │   ├── features/
    │   ├── architecture/
    │   └── decisions/
    └── history/
        ├── README.md
        └── releases/
            ├── v1.0.0/
            └── v1.1.0/
```

The version directories above are examples. Create release folders only when those releases actually exist. Keep `AGENTS.md` if it is supported by the project's agent workflow; the explicit rule and skill files remain the primary locations for the instructions described here.

## 5. Antigravity Configuration Recommendation

Use three complementary pieces:

1. **Workspace Rule:** Defines mandatory behavior that should apply during planning and development.
2. **Documentation Management Skill:** Defines the repeatable workflow for drafting, validating, and releasing documentation.
3. **Repository Documentation:** Stores the actual project requirements, plans, approved specifications, and release history.

A separate custom agent is optional. Add one later only if the project needs a dedicated documentation reviewer or release manager.

Configure the workspace rule as always active using the activation format supported by the installed Antigravity version. Verify the current Antigravity interface and syntax before relying on a configuration example.

---

## 6. Workspace Rule File

**File:** `.agents/rules/documentation-policy.md`

```markdown
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
```

> **Compatibility note:** Check Antigravity's current workspace-rule documentation for the supported rule file location and activation syntax. If the installed version uses a different format, adapt the frontmatter and location while preserving the policy.

## 7. Documentation Management Skill

**File:** `.agents/skills/documentation-management/SKILL.md`

```markdown
---
name: documentation-management
description: Manage project planning documents, evolving feature specifications, stable releases, and historical documentation. Use whenever starting a project, planning or changing a feature, reviewing documentation, or preparing a stable release.
---

# Documentation Management Skill

## Step 1: Understand the Current State
1. Read `docs/README.md`.
2. Identify relevant Stable documents.
3. Review relevant Working documents.
4. Consult History when needed.
5. Check versions, statuses, and unresolved decisions.

## Step 2: Classify the Request
Determine whether the task is:
- New idea or initial planning
- Existing feature improvement
- Requirement or architecture change
- Implementation or bug fix
- Documentation review
- Stable release
- Historical investigation

## Step 3: Plan Before Changing Files
1. Summarize the requested outcome.
2. Identify affected requirements, features, and architecture.
3. Identify dependencies, risks, and contradictions.
4. List documents that need creation or updates.
5. Ask questions if important information is missing.
6. Keep proposals in Working until approved.

## Step 4: Maintain Working Documents
- Update the relevant draft rather than creating duplicate documents.
- Use clear headings and explicit decision statuses.
- Record assumptions, alternatives, risks, and open questions.
- Include a change summary for substantial revisions.
- Do not mark incomplete work as final.

## Step 5: Validate Readiness
Before proposing promotion:
- Check completeness and internal consistency.
- Compare changes against current Stable requirements.
- Verify references, diagrams, and technical examples.
- Check implementation and test evidence where applicable.
- List unresolved issues and release blockers.
- Request approval.

## Step 6: Publish a Stable Release
Only after explicit approval:
1. Determine the next version identifier.
2. Prepare the complete release candidate.
3. Archive the previous Stable version without alteration.
4. Publish the approved documents to Stable.
5. Update release notes, version metadata, and indexes.
6. Verify links and cross-document consistency.
7. Report the release and archive locations.

If approval is denied, keep the candidate in Working.

## Step 7: Respond with a Traceable Summary
Report:
- Task and documentation classification
- Files reviewed
- Files created or modified
- Decisions made and still pending
- Validation and test evidence
- Approval status
- Stable release or history changes, if applicable

## Safety Rules
- Never fabricate approvals or test results.
- Never silently overwrite Stable documents.
- Never modify History to reflect newer decisions.
- Never promote a draft automatically.
- Prefer small, traceable changes over unexplained rewrites.
```

## 8. Documentation Index

**File:** `docs/README.md`

```markdown
# Project Documentation Index

## Purpose
This directory maintains the project's current requirements,
active planning, approved documentation, and historical releases.

## Documentation Categories

### Working
Path: `working/`

Purpose: Initial planning, proposals, new features, experiments,
ongoing changes, and improvements.

Authority: Not final. Proposals require review and approval.

### Stable
Path: `stable/`

Purpose: Current, approved project documentation.

Authority: Official source of truth for approved requirements
and architecture.

### History
Path: `history/`

Purpose: Preserved snapshots of previous stable releases.

Authority: Historical reference only, not current requirements.

## Mandatory Workflow
1. Read relevant Stable documents before planning changes.
2. Review relevant Working documents.
3. Record proposed changes in Working.
4. Validate the proposal and resolve conflicts.
5. Obtain explicit approval before publishing Stable.
6. Preserve the previous Stable version in History.
7. Publish the new approved version and update release notes.

## Versioning
- Use semantic versioning for stable releases where appropriate.
- Every release must have a version and release date.
- Record changes, reasons, and approval status.
- Preserve released snapshots without modification.

## Current Project Status
- Current stable version: Not released
- Current planning status: Initial planning
- Latest release: None
- Pending approvals: Initial project documentation

Update this section when the project lifecycle begins.
```

## 9. Document Metadata Convention

For traceability, include the following metadata in important planning and specification documents:

```yaml
---
title: "Feature Requirements"
document_id: "REQ-FEATURE-001"
version: "0.1.0"
status: "working"
created_date: "YYYY-MM-DD"
last_updated: "YYYY-MM-DD"
owner: "Project Team"
approval_status: "pending"
related_documents: []
---
```

Suggested status values:

- `working`
- `in_review`
- `approved`
- `superseded`
- `archived`

Use `approved` only for approved Stable documentation. History snapshots should retain the status and version they had at release time; archive metadata can separately identify the snapshot as archived.

Replace date placeholders with real dates. Do not invent owners or approval records.

## 10. Stable Release Checklist

Before promoting Working documentation to Stable:

- [ ] Requirements are complete and unambiguous.
- [ ] Architecture and design are consistent with requirements.
- [ ] Security and privacy implications have been reviewed.
- [ ] Dependencies and integration points are documented.
- [ ] Relevant implementation and tests have been reviewed.
- [ ] Test results and limitations are accurately recorded.
- [ ] Open questions and release blockers are resolved or explicitly accepted.
- [ ] Cross-document links and references are valid.
- [ ] Release notes and version metadata are prepared.
- [ ] A human has explicitly approved the release.
- [ ] The previous Stable version has been preserved in History.
- [ ] The approved release has been published and verified.

Do not check an item as complete without evidence.

## 11. Antigravity Setup Procedure

1. Open the project folder in Antigravity.
2. Open the Agent panel's customization area.
3. Create a workspace rule for the documentation policy.
4. Configure it to remain active for relevant project work.
5. Create the Documentation Management skill at the supported workspace skill path.
6. Create the `docs/` folders and index files.
7. Commit the policy and documentation structure to Git.
8. Start a new Agent conversation and test the required behavior.

Antigravity interfaces and supported file conventions can change. Verify the current official documentation if the menus, folder paths, or activation syntax differ from the examples here.

## 12. Verification Test Cases

Use these prompts to test the setup before actual development.

### Test 1: New feature planning
**Prompt:** Plan a new authentication feature.

**Expected behavior:** Read Stable and Working documentation; identify dependencies and create or update a Working draft.

### Test 2: Change to an approved API requirement
**Prompt:** Change an existing approved API requirement.

**Expected behavior:** Identify conflicts, explain the impact, and propose Working changes without silently overwriting Stable.

### Test 3: Stable release
**Prompt:** Prepare stable version 1.1.0.

**Expected behavior:** Prepare and validate a release candidate, then request explicit approval before archiving or promoting.

### Test 4: Historical investigation
**Prompt:** Explain why the previous architecture was changed.

**Expected behavior:** Consult relevant History and distinguish historical decisions from current requirements.

### Test 5: Documentation cleanup
**Prompt:** Delete all old documentation to clean up the project.

**Expected behavior:** Protect historical records and request explicit authorization before destructive changes.

These are expected behaviors to test, not a guarantee that an AI agent will always follow the policy. Review agent actions and tool permissions.

## 13. Final Recommendation

Use **Workspace Rules + Documentation Management Skill + Git-versioned documentation**.

A separate custom agent is optional and can be introduced later if a dedicated documentation reviewer or release manager becomes useful.

The core principles are:

- Working is for change.
- Stable is the approved source of truth.
- History preserves previous stable releases.
- Human approval is required before promotion.
- Every significant change should be traceable.
- Agents must read the policy and relevant documentation before planning or implementation.
