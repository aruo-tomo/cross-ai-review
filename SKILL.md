---
name: cross-ai-review
description: Independently review documents, ideas, plans, or code with a second AI chat or an optional authenticated model CLI. Use when asked to fact-check, critique, improve, or stress-test an article, proposal, project review, strategy, plan, ideation output, or code review; when the user mentions cross-AI or cross-model review; or when a draft needs a second perspective before sharing.
---

# Cross-AI Review

## Overview

Use one AI chat as the author and a separate, fresh AI chat as the reviewer. This workflow helps expose blind spots, unclear reasoning, unsupported claims, and implementation risks. It does not guarantee accuracy, eliminate hallucinations, or replace expert review.

## Choose the handoff method

Ask the user to choose before preparing the review packet:

1. **Manual handoff (default)** — copy the packet into a separate, fresh AI chat and return its response here.
2. **CLI relay (advanced)** — pass the packet to an installed, authenticated CLI for another model. Use only when the user has active access to both services and explicitly consents to the transfer and any required installation or sign-in.

For the CLI relay, ask which executor and reviewer the user wants to use. `Claude executor → Codex reviewer` and `Codex executor → Claude reviewer` are examples only; allow any compatible, separately authenticated model CLIs. If the user does not choose, use manual handoff.

## Workflow

1. Identify the review mode: `article`, `proposal`, `project-review`, `ideation`, or `code-review`. Ask for the audience, intended decision, relevant constraints, and what must not change.
2. Before sharing content with a second AI, warn the user that it will leave the current chat. Call out confidential business information, personal data, credentials, unpublished material, and client details. Let the user decide whether to redact or proceed.
3. Create a self-contained review packet using the applicable template in [references/review-templates.md](references/review-templates.md). Preserve uncertainty; do not fill gaps with assumptions.
4. Complete the selected handoff:
   - **Manual:** ask the user to paste the packet into a separate AI chat. Encourage a different provider or model when available, but do not claim independence if the underlying model is unknown.
   - **CLI relay:** follow [references/cli-relay.md](references/cli-relay.md). Send only the review packet to the reviewer CLI; keep the executor's working context and unrelated files out of the handoff.
5. Incorporate the review: fix clear errors, preserve intentional choices, and ask the user to decide unresolved tradeoffs. Repeat only for material changes or high-impact claims, within the review-round limit.
6. Return the final artifact with a short change summary and any remaining risks or questions.

## Review-round limits

- Allow at most **five** review rounds for non-code work: articles, proposals, project reviews, and ideation.
- Allow at most **eight** review rounds for `code-review`.
- Count each complete reviewer handoff as one round, whether it is manual or CLI-based.
- At the limit, stop the loop. Summarize unresolved issues and ask the user for a decision, manual approval, or a new scope before any additional review.

## Review requirements

- Tailor criteria to the selected mode; use the mode checklists in the reference file.
- For `code-review`, assess correctness, security, data handling, performance, maintainability, tests, and unintended behavior changes.
- Require source links for material factual claims when practical. Never invent, infer, or decorate citations.
- Classify each material claim as `verified`, `partially supported`, `unverified`, or `contradicted`. State the reason and source link when one exists.
- Prioritize issues by impact: `must fix`, `should improve`, or `optional`.
- Separate factual findings from editorial preferences and strategic judgement.
- Preserve the user's voice, objectives, and stated constraints. Do not rewrite around a decision that only the user can make.

## Required reviewer output

Require this exact structure from the reviewer:

1. **Decision summary** — whether the artifact is ready, needs revision, or needs human input.
2. **Must-fix issues** — only high-impact inaccuracies, omissions, contradictions, or unsafe claims.
3. **Improvements** — clarity, tone, structure, and usefulness suggestions.
4. **Open questions** — decisions or missing context that the reviewer cannot resolve.
5. **Evidence status** — a compact table for material factual claims.
6. **Safe revision** — a revised passage or artifact only for changes that do not require a human decision.

## Human judgement gate

Pause and ask the user for direction instead of making a final claim or decision when the work involves:

- Legal, medical, financial, safety, employment, or other high-stakes guidance.
- Missing, unreachable, or conflicting evidence for a material claim.
- Confidential or personal information the user has not explicitly chosen to share.
- A strategic tradeoff, approval, promise, budget, timeline, or public statement that needs an accountable owner.
- Ambiguous goals, audience, or success criteria.

## Completion checklist

- The reviewer used the required output structure.
- Every material factual claim has an evidence status; unsupported claims remain labeled.
- The final artifact distinguishes verified information from assumptions and recommendations.
- The user has answered all open decisions, or they remain explicitly listed as risks.
- No claim says this process guarantees truth, factual accuracy, or the absence of hallucinations.
