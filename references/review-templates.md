# Review templates

Use a fresh reviewer chat and paste one complete packet. Replace bracketed text; do not add invented context.

## Shared packet

```markdown
# Independent AI review request

## Mode
[article | proposal | project-review | ideation | code-review]

## Purpose and audience
[Who will use this, and what should they decide, learn, or do?]

## Constraints
[Tone, length, deadline, facts that must remain, information that must not be shared]

## Draft or working material
[Paste the complete artifact]

## Review instructions
Review independently. Do not invent citations or missing facts. Label material factual claims as verified, partially supported, unverified, or contradicted. Return: decision summary; must-fix issues; improvements; open questions; evidence status; and safe revision only where no human decision is needed.
```

## Article mode

Add: `Check factual accuracy, source quality, misleading certainty, missing context, structure, readability, tone, and whether the headline matches the body.`

Treat numbers, dates, causal statements, quotations, named policies, and comparative claims as material claims. Prefer a primary source or an authoritative source. If no source is supplied or found, mark the claim `unverified`; do not replace it with a guess.

## Proposal mode

Add: `Check the problem definition, evidence, intended outcome, alternatives, feasibility, costs, risks, owners, dependencies, and decision requested.`

Call out promises that lack an owner, measurable outcome, budget basis, timeline basis, or stakeholder approval.

## Project-review mode

Add: `Check goals, scope boundaries, milestones, dependencies, risks, assumptions, decision log, ownership, and success measures.`

Flag contradictory timelines, unnamed decision owners, missing dependency plans, and outcomes that cannot be measured.

## Ideation mode

Add: `Check user value, originality, assumptions, constraints, likely failure modes, alternatives, smallest useful experiment, and how the idea would be evaluated.`

Do not falsely fact-check speculative ideas. Classify evidence only for factual premises; keep creative judgement separate.

## Code-review mode

Add: `Check correctness, security, privacy and data handling, performance, error handling, maintainability, tests, compatibility, and unintended behavior changes. Identify issues by priority and include a concise reproduction or reasoning path when possible.`

Do not claim a test passed unless the reviewer actually ran it and reports the result. Keep code review within the eight-round limit; all other modes use a five-round limit.

## Evidence-status table

Use this format for material factual claims:

| Claim | Status | Evidence / reason | Needed action |
| --- | --- | --- | --- |
| [claim] | verified / partially supported / unverified / contradicted | [link or short reason] | [keep, qualify, source, remove, or resolve] |

## Revision checklist

- Resolve every `must fix` issue, or explicitly preserve it with the user's approval.
- Keep uncertainty visible; use qualified language where evidence is incomplete.
- Remove fabricated citations, precise figures without support, and claims that exceed the evidence.
- Retain the author's intended audience, tone, and scope.
- List remaining questions and high-stakes decisions for a human owner.
- Stop at five review rounds for non-code work or eight rounds for code review; ask the user before starting another loop.
