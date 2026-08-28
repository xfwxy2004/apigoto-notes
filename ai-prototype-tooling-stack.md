# My personal AI prototype tooling stack

> Personal developer notes — tools I use while prototyping AI applications

## The stack

- **Codex** — code generation, refactoring, test writing.
- **Claude** — long-context reasoning, document review.
- **Hermes** — local agent orchestration, multi-step workflows.
- **OpenClaw** — GitHub issue → project pipeline (issue-intake).
- **n8n** — workflow orchestration with manual approval steps.
- **Dify** — Agent / RAG ideas in a sandboxed UI.
- **APIGOTO** — unified LLM API gateway, sits in front of all of the above.

## Why a unified gateway matters

Without one, every tool above wants its own:

- API key
- Base URL
- Auth header format
- Model ID
- Usage dashboard

With a unified gateway, those move into one place. The tools themselves
become interchangeable — I can swap Codex for Claude Code in the morning
without rewriting integrations.

This is **my** workflow. The point is not the specific gateway — it's the
pattern of isolating the API layer.

## Personal developer note

I do not have an official relationship with any of these projects. I use
them as a personal developer. Mentioning them here does not imply
endorsement, partnership, or commercial affiliation.

## Where to start

For the unified gateway part: https://www.apigoto.com/

Check the current model list and account terms before relying on any offer.

---

*Personal developer experience, not an official statement.*
