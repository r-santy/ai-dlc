Overview
This repository contains a cloud‑native web application with a modular architecture organized by domain.

Primary languages: TypeScript/JavaScript for frontend (React) and backend (Node.js/Express or NestJS), with Infrastructure as Code and CI/CD definitions in the repo.

Documentation and AI-driven lifecycle (AI‑DLC) artifacts live under aicd-docs/. The assistant must always propose a plan before editing code or docs.

High-level structure
aicd-docs/

plans/ — step-by-step plans with checkboxes that require human approval.

requirements/ — high-level requirements and changes.

story-artifacts/ — user stories and acceptance criteria.

design-artifacts/ — architecture, domain models, ADRs.

prompts.md — references to reusable prompts and conventions.

app/ — application source (frontend and backend).

infra/ — IaC, deployment scripts, and environment configuration.

.github/ — automation, workflows, and these Copilot instructions.

Goals for the assistant
Always work in a branch and open a pull request for any multi-file change.

Before making edits, draft a plan in aicd-docs/plans/<task>.md with checkboxes, then wait for explicit approval in the PR or chat thread.

Generate user stories and acceptance criteria following INVEST; place them in aicd-docs/story-artifacts/.

For design work, write/upsert docs in aicd-docs/design-artifacts/ and keep diagrams or models alongside markdown.

Keep the repo buildable and the tests green; prefer small, reviewable diffs aligned to the approved plan.

Non-functional expectations
Target clear SLOs for build time and unit test execution; avoid adding heavy dependencies without justification.

Maintain security hygiene: no secrets in code, use environment variables, and update dependency locks via PR with changelogs.

Coding and documentation conventions
Follow existing lint/format rules; run format:fix and lint before pushing.

Document decisions as short ADRs in aicd-docs/design-artifacts/adrs/.

Prefer test-first or test-augmented changes; add or update tests for each story.

Workflow the assistant must follow
Propose

Create or update a plan markdown under aicd-docs/plans/ with: context, objectives, file-level change list, test updates, and verification steps.

Include checkboxes for each step. Do not modify source files yet.

Await approval

Pause until an explicit “Approve. Proceed.” comment or PR review approval is provided.

Execute

Implement steps in small commits tied to the plan; update checkboxes in the plan as steps complete.

Keep edits scoped to the approved file list unless a follow-up mini-plan is proposed and approved.

Validate

Run lint, unit tests, and any security or type checks; capture results in the PR description.

If validation fails, revert the step or propose a revised mini-plan.

Document

Update user stories, acceptance criteria, and design docs as artifacts of the change.

Record any deviations or assumptions directly in the plan file.

Paths and file placement rules
Plans: aicd-docs/plans/<short-task-name>.md

User stories: aicd-docs/story-artifacts/<scope>_user_stories.md

Design/domain models: aicd-docs/design-artifacts/<domain>_model.md

Requirements or change requests: aicd-docs/requirements/<ticket-or-brief>.md

Branch and PR policy
Create feature/<short-task-name> branches.

Every multi-file change is delivered via PR with the plan attached; enable required checks.

What not to do
Do not make critical decisions or broad refactors without an approved plan.

Do not bypass tests, linters, or branch protections.

Do not store secrets, sample tokens, or credentials in the repository.

Acceptance checklist for each task
 Plan file created/updated under aicd-docs/plans/ and approved.

 User stories and acceptance criteria written/updated under story-artifacts/.

 Design/domain documentation updated under design-artifacts/.

 Code, tests, and docs changed according to plan; all checks pass.

 Plan checkboxes updated to reflect completion and any deviations recorded.

