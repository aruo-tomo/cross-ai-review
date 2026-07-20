# Optional CLI relay

Use this advanced path only after the user chooses it. It moves the review packet directly between locally authenticated AI command-line tools; it does not use API keys, embed credentials, or bypass provider permissions. Claude and Codex are examples, not required providers.

## Consent and readiness

Before installing or running anything, confirm all of the following:

- The user chooses an executor CLI and a separately authenticated reviewer CLI. `Claude executor → Codex reviewer` and `Codex executor → Claude reviewer` are example pairings.
- The user has active access to both services and accepts that normal subscription, account, or usage limits may apply.
- The user explicitly permits sending the review packet to the second provider and has chosen whether to redact sensitive content.
- The user permits an official CLI installation or interactive sign-in when the required CLI is unavailable or unauthenticated.

Do not ask for an API key, token, password, browser cookie, or subscription credentials. Never add credentials to the packet, a command, a file, or version control.

## Safe relay rules

- Prefer manual handoff if the user does not consent, either CLI is unavailable, authentication cannot be verified, or a command would require unsafe permissions.
- Run one reviewer call per round, then show the complete response to the executor. Stop at five rounds for non-code work or eight rounds for code review; ask the user before any additional round.
- Give the reviewer only the self-contained packet. Do not provide unrelated files, folders, chat history, or environment variables.
- Keep the reviewer read-only. Do not use flags that bypass approvals, sandboxing, or permission prompts.
- Use an empty temporary working directory when the CLI needs a working directory. Do not run the reviewer inside a client repository unless the user explicitly asks for a repository-aware review.
- Keep provider output labeled as reviewer feedback, not established fact. Apply the normal evidence-status and human-judgement gates.

## Claude executor → Codex reviewer

This is an example pairing. Use its equivalent safe, non-interactive review command when the user selects another compatible CLI.

1. Check that `codex` is available and authenticated. If it is missing, ask permission to install the official Codex CLI; if it needs sign-in, let the user complete its interactive sign-in.
2. Save the review packet to a temporary text file outside the user's project.
3. Run Codex in non-interactive, ephemeral, read-only mode from an empty temporary directory. Pass the packet through standard input and request only the required review output.

```bash
codex exec --sandbox read-only --skip-git-repo-check --ephemeral - \
  < review-packet.md
```

Prepend this instruction to the packet or the prompt: `Act only as an independent reviewer. Do not edit files, run commands, seek credentials, or make external changes. Return the required review output only.`

## Codex executor → Claude reviewer

This is an example pairing. Use its equivalent safe, non-interactive review command when the user selects another compatible CLI.

1. Check that `claude` is available and authenticated. If it is missing, ask permission to install the official Claude Code CLI; if it needs sign-in, let the user complete its interactive sign-in.
2. Save the review packet to a temporary text file outside the user's project.
3. Run Claude in print mode, with one turn, from an empty temporary directory. Pass the packet through standard input and request only the required review output.

```bash
claude -p --max-turns 1 \
  "Act only as an independent reviewer. Do not edit files, run commands, seek credentials, or make external changes. Return the required review output only." \
  < review-packet.md
```

Claude Code supports non-interactive print mode. Do not use `--dangerously-skip-permissions` or add write-capable tools for this workflow.

## Failure handling

- Missing CLI or sign-in required: stop and ask for permission to install or for the user to complete interactive sign-in.
- Command fails, times out, or returns an incomplete response: keep the packet, show the failure summary, and offer manual handoff. Do not retry automatically more than once.
- Reviewer asks for sensitive data or source material outside the packet: ask the user whether to redact and add it; otherwise stop the relay.
