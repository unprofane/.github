A profanity and toxicity API that is hard to fool. One call says whether to allow a text, with the evidence: which words, where, how they were disguised, how severe, and a censored copy. It is also a drop-in for Google's Perspective API, which stops answering after December 31, 2026.

```bash
curl https://api.unprofane.com/v1/check \
  -H "Authorization: Bearer $UNPROFANE_API_KEY" \
  -H "Content-Type: application/json" \
  -d '{"text":"sh1tH3ad_69","context":"username","policy":"teen"}'
```

```json
{
  "allowed": false,
  "action": "block",
  "severity": "strong",
  "evasion": ["leetspeak"],
  "censored": "********_69",
  "reason": "Blocked under the teen policy for swearing in the wording and an insult: \"sh1tH3ad\" (shithead), typed with leetspeak."
}
```

**[The Scunthorpe Test](https://github.com/unprofane/scunthorpe-test)**, the public dev split, 15,550 items, 2026-10-24. Trap FPR is the share of innocent items (Scunthorpe, cockatoo, breast cancer) a filter blocked.

| System | F1 | Trap FPR |
|---|---|---|
| unprofane-fast | 0.920 | 0.0% |
| openai-moderation | 0.553 | 3.2% |
| obscenity | 0.364 | 20.2% |
| perspective | 0.314 | 3.0% |
| bad-words | 0.142 | 12.5% |
| 2toad-profanity | 0.128 | 11.5% |
| leo-profanity | 0.057 | 8.7% |

| Repository | |
|---|---|
| [unprofane-js](https://github.com/unprofane/unprofane-js) | `npm install @unprofane/sdk` |
| [unprofane-python](https://github.com/unprofane/unprofane-python) | `pip install unprofane` |
| [moderate-action](https://github.com/unprofane/moderate-action) | A GitHub Action that hides abusive issue, pull request and discussion comments |
| [scunthorpe-test](https://github.com/unprofane/scunthorpe-test) | The benchmark: the dev split, the runner and adapters for open-source filters |
| [perspective-api-client](https://github.com/unprofane/perspective-api-client) | Perspective's Node client with the host configurable |
| [discourse-perspective-api](https://github.com/unprofane/discourse-perspective-api) | Discourse's Perspective plugin with the host as a setting |

[Docs](https://unprofane.com/docs/) · [Playground](https://unprofane.com/playground/) · [Pricing](https://unprofane.com/pricing/) · [Moving off Perspective](https://unprofane.com/perspective/)
