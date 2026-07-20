# Cross-AI Review

Independent AI review for articles, proposals, project reviews, and ideation.

Use this skill when you want a second AI to challenge a draft or code change before you share it. It needs no API key, token, script, or special integration for its default manual workflow. One AI creates the work; a fresh second chat reviews a complete packet; the first AI applies clear fixes and asks you to make the remaining decisions.

## Quick start

1. Add `cross-ai-review` to a compatible AI workspace, or open `SKILL.md` and paste its instructions into your preferred AI tool.
2. Ask the author chat to use Cross-AI Review for your article, proposal, project review, idea, or code change.
3. Choose the handoff method:
   - **Manual (default):** paste the generated review packet into a separate AI chat, then bring its review back to the author chat.
   - **CLI relay (advanced):** with active access to both services, let the executor use another model's installed, authenticated CLI as the reviewer.

The manual workflow works with ChatGPT, Claude, Codex, Gemini, and similar AI tools. A different provider or model can offer a more independent perspective, but this repository does not claim to identify the underlying model used by any service.

## Advanced: CLI relay

For a direct model-to-model handoff, choose any compatible executor and separately authenticated reviewer CLI. Examples include:

- Claude as executor → Codex as reviewer
- Codex as executor → Claude as reviewer

The skill asks for explicit consent before installing a CLI, beginning an interactive sign-in, or sending the packet to another provider. It uses the subscription or account access you already have; it never asks for or stores an API key. Reviewer commands are limited to a read-only review of the packet. See [the CLI relay guide](references/cli-relay.md) for requirements and safety rules.

To limit cost and token use, the skill stops after five rounds for non-code work and eight rounds for code review. A user must explicitly decide whether to continue beyond the limit.

## What it checks

- Articles: factual claims, missing context, clarity, readability, and tone.
- Proposals: problem definition, evidence, feasibility, risks, and decision readiness.
- Project reviews: scope, milestones, dependencies, ownership, and success measures.
- Ideation: user value, assumptions, constraints, alternatives, and small experiments.
- Code review: correctness, security, maintainability, tests, and unintended behavior changes.

Material factual claims receive an evidence status: `verified`, `partially supported`, `unverified`, or `contradicted`. The reviewer must never invent citations.

## Privacy

Before pasting content into a second AI chat, consider whether it contains personal data, credentials, client information, internal strategy, unpublished work, or other confidential information. Redact it if appropriate. You decide whether to share it; this skill does not transmit anything itself.

The same warning applies to the CLI relay: it sends the packet to the reviewer provider under the account that is signed in locally.

## Important limitations

Cross-AI review can reveal blind spots and unsupported claims. It cannot guarantee that a result is correct, complete, unbiased, or free from hallucinations. Use accountable human or professional review for legal, medical, financial, safety, employment, or similarly high-stakes decisions.

## Repository contents

- `SKILL.md` — the operational skill.
- `references/review-templates.md` — copy/paste templates and review criteria.
- `references/cli-relay.md` — optional Claude/Codex CLI relay instructions.
- `examples/` — fictional, non-sensitive packets for the four modes.

## Contributing

See [CONTRIBUTING.md](CONTRIBUTING.md). Do not submit secrets, tokens, API keys, private drafts, personal data, or confidential material.

## License

MIT. See [LICENSE](LICENSE).
