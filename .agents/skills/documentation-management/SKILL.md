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
- Add the metadata block below to important planning and specification documents.

### Document Metadata Convention

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

Status values: `working`, `in_review`, `approved`, `superseded`, `archived`.

- Use `approved` only for approved Stable documentation.
- History snapshots retain the status and version they had at release time;
  archive metadata can separately identify the snapshot as archived.
- Replace date placeholders with real dates. Do not invent owners or approval records.

## Step 5: Validate Readiness
Before proposing promotion:
- Check completeness and internal consistency.
- Compare changes against current Stable requirements.
- Verify references, diagrams, and technical examples.
- Check implementation and test evidence where applicable.
- List unresolved issues and release blockers.
- Request approval.

### Stable Release Checklist
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

## Step 6: Publish a Stable Release
Only after explicit approval:
1. Determine the next version identifier.
2. Prepare the complete release candidate.
3. Archive the previous Stable version without alteration
   (to `docs/history/releases/v<previous-version>/`).
4. Publish the approved documents to Stable.
5. Update release notes, version metadata, and indexes
   (`docs/README.md`, `docs/stable/README.md`, `docs/history/README.md`).
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
