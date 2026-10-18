# Prompts

Four-step pipeline, model-agnostic. Run each file as its own call.

| Step | File | Sees English? |
|---|---|---|
| 1 | [1-outline-extraction.md](1-outline-extraction.md) | yes, and outputs a JSON brief only |
| 2 | [2-write-from-outline.md](2-write-from-outline.md) | **no**, only the brief |
| 3 | [3-review-and-trim.md](3-review-and-trim.md) | no, Chinese draft + fact list |
| 4 | code checks, see "E.4" in [method.md](../skills/zh-transcreation/method.md) | no |

[optional-personal-essay.md](optional-personal-essay.md) adds a first-person column variant.

The prompts are written in Chinese on purpose: the instructions are linguistic ones about Chinese syntax. The default audience in the examples is Chinese-speaking small-business owners in Metro Vancouver; change `{audience}` and `{locale}` for your market.
