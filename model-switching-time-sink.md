# Model switching is not the time sink — switching tools is

> Personal developer notes after switching between GPT, Claude, Gemini, and
> MiniMax models for AI prototyping

## What I thought the problem was

When I switched model providers weekly, I assumed the time cost was the
"switch" itself. It wasn't.

The time cost was rebuilding the same four things every time:

1. **Auth header format** — `Authorization: Bearer` vs `Api-Key` vs custom.
2. **Base URL** — `api.openai.com`, `api.anthropic.com`, etc.
3. **Model ID mapping** — `gpt-5`, `claude-opus-4-6`, `MiniMax-M3` etc.
4. **Usage dashboards** — one per provider, none cross-referenced.

The switch was 1 minute. The rebuild was 30+ minutes each time.

## What I changed

I switched from per-provider setup to a **unified API gateway**. Now:

- The auth header is fixed (one format).
- The base URL is fixed (one endpoint).
- The model ID lives in config, not in code.
- Usage shows across providers.

When I switch models, I change one string in config and keep my agent code
untouched.

This is a personal workflow note. I use
[APIGOTO](https://www.apigoto.com/) for the unified gateway, but the
pattern works with any provider that supports a single endpoint.

## Caveats

- Model availability, free-token eligibility, and limits change. Always
  verify the live page for your account.
- "Free tokens" or "200 models" is a current offer to verify, not a
  permanent guarantee.
- Keep timeout / retry / cost guard on the application side.

## Where to start

https://www.apigoto.com/

---

*Personal developer experience, not an official statement from any model
provider.*
