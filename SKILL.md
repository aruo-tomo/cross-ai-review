---
name: cross-ai-review
description: Independently review non-engineering work with a second AI chat. Use when asked to fact-check, critique, improve, or stress-test an article, proposal, project review, strategy, plan, or ideation output; when the user mentions cross-AI or cross-model review; or when a draft needs a second perspective before sharing.
---

# Cross-AI Review

## Overview

Use one AI chat as the author and a separate, fresh AI chat as the reviewer. This workflow helps expose blind spots, unclear reasoning, and unsupported claims. It does not guarantee accuracy, eliminate hallucinations, or replace expert review.

## Workflow

1. Identify the review mode: `article`, `proposal`, `project-review`, or `ideation`. Ask for the audience, intended decision, relevant constraints, and what must not change.
2. Before sharing content with a second AI, warn the user that it will leave the current chat. Call out confidential business information, personal data, credentials, unpublished material, and client details. Let the user decide whether to redact or proceed.
3. Create a self-contained review packet using the applicable template in [references/review-templates.md](references/review-templates.md). Preserve uncertainty; do not fill gaps with assumptions.
4. Ask the user to paste the packet into a separate AI chat. Encourage a different provider or model when available, but do not claim independence if the underlying model is unknown.
5. Incorporate the review: fix clear errors, preserve intentional choices, and ask the user to decide unresolved tradeoffs. Repeat the handoff once for material changes or high-impact claims.
6. Return the final artifact with a short change summary and any remaining risks or questions.

## Review requirements

- Tailor criteria to the selected mode; use the mode checklists in the reference file.
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
