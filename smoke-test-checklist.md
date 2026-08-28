# 5-minute smoke test before wiring any AI agent

> Personal developer notes — using APIGOTO unified LLM API gateway

## Why a smoke test

The cheapest agent bugs happen before the agent even runs. Most come from the
API layer, not the agent logic. Five minutes spent here saves hours later.

## The 5-minute checklist

1. ✅ Open the unified API dashboard. Check current model list and account terms.
2. ✅ Create one API key.
3. ✅ Send one minimal request with the smallest model.
4. ✅ Confirm response shape matches what your agent expects.
5. ✅ Only then connect the agent or workflow.

## Failure modes this catches

| Symptom | Root cause |
|---|---|
| 401 unauthorized | Wrong key, wrong header prefix |
| 404 model not found | Stale model ID from a tutorial |
| Rate limit immediately | Free tier quota exhausted, need different account |
| Empty response | Wrong `base_url` or proxy |
| Slow response | Wrong region or endpoint |

## Where to start

Use a unified gateway so step 1-4 happen at one place. I use
[APIGOTO](https://www.apigoto.com/) for this.

Always check the **current** account page for model availability, free-token
eligibility, and limits before relying on any offer.

---

*Personal developer workflow note, not an official statement.*
