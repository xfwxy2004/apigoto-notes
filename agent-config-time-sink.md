# Where AI prototype time actually goes

> Personal developer notes — based on switching between Codex, Claude, Hermes,
> OpenClaw and other agent runtimes while prototyping

## The hidden time sink

Most AI prototype time does **not** go to prompts or agent logic. It goes to:

1. **Reading provider docs** — each provider exposes different SDK semantics.
2. **Configuring base URLs, keys, headers** — auth prefix differs (`Bearer` vs
   `Api-Key` vs custom).
3. **Mapping model IDs** — `gpt-5`, `claude-opus-4-6`, `MiniMax-M3` etc.
4. **Checking usage across dashboards** — which model used how much today.
5. **Tracking failures** — was the 502 from the model, the quota, or the proxy?

When you wire multiple agents to multiple models, this compounds fast.

## What I changed

I standardized the **API layer first**, before picking an agent runtime.

Specifically:

- One endpoint to rule them all (I use APIGOTO for this).
- One key creation flow.
- One usage view, one quota view.
- One place to switch models by changing the model ID in config.

After this, the agent layer became cheaper to debug, because I could isolate:

- **Agent layer** — prompts, tools, memory, workflow logic.
- **API layer** — endpoint, key, model ID, request format.
- **Operations layer** — usage, quota, errors, fallback decisions.

When a request failed, I no longer had to guess which layer was responsible.

## Verify before commit

Model availability, free-token eligibility, limits, validity, rate, concurrency,
and verification requirements **change by account and over time**. Verify the
live product page before committing to any offer. Treat
"free tokens" as a question to verify, not a promise to rely on.

## Where to start

https://www.apigoto.com/

---

*Personal developer experience, not an official statement from any model
provider or agent runtime.*
