# zh-transcreation

**Turn English into Chinese that reads like it was written in Chinese.**
A transcreation skill for AI agents (Claude Code, Cursor, Codex, or any LLM).

中文说明：[README.zh-CN.md](README.zh-CN.md)

## Same sentence, two Chinese versions

| | |
|---|---|
| English | Ready to unlock your business's full potential? Our comprehensive solutions empower you to maximize local visibility. |
| Literal translation | 准备好释放您业务的全部潜力了吗？我们全面的解决方案赋能您最大化本地可见性。 |
| zh-transcreation | 想让附近的人搜得到你？网站、Google 商家、小红书，我们一起帮你做。 |

Every word of the literal version is "correct", and no Chinese owner would say it. The second keeps the intent (be found locally) and drops the English sentence shape, the abstract nouns and the sales voice. More pairs, with the reasoning, are in [examples/](examples/).

## Why

Models translate English into Chinese sentence by sentence, so the output keeps English syntax: passives, long modifiers, pronouns everywhere, abstract nouns. Telling a model to "sound natural" barely helps. What helps:

1. Write a **brief** first (reader, desired action, fact list). Do not write Chinese yet.
2. Have the model write Chinese from the brief **without seeing the English sentences**, so there is nothing to copy.
3. Review against a concrete checklist, then trim.

Published research points the same way: a translate-then-polish pass cut the share of obviously translationese GPT-4 documents from 43% to 25% (Li et al., ACL 2025), and specific linguistic instructions work better than asking for fluency (Kunilovskaya et al., EAMT 2024).

## What is inside

| Path | What |
|---|---|
| [`skills/zh-transcreation/SKILL.md`](skills/zh-transcreation/SKILL.md) | The agent skill: framework, six-step workflow, 30-point checklist, copy and compliance rules, Chinese SEO/GEO |
| [`skills/zh-transcreation/method.md`](skills/zh-transcreation/method.md) | The full method, in Chinese: translation theory (Yan Fu to Nida, Newmark, Skopos), English-Chinese contrast, 30 fixes with examples, SEO/GEO, prompts, sources |
| [`prompts/`](prompts/) | Outline extraction, write-from-outline, review and trim. Model-agnostic |
| [`adapters/`](adapters/) | Cursor rule, Codex `AGENTS.md` snippet, generic system prompt |
| [`examples/`](examples/) | Before/after pairs from real pages (nextagent.ca, 2026-10) |

## Install

**Claude Code plugin**

```bash
/plugin marketplace add NextAgentBC/zh-transcreation
/plugin install zh-transcreation@nextagent
```

Or from a shell: `claude plugin marketplace add NextAgentBC/zh-transcreation` then `claude plugin install zh-transcreation@nextagent`.

**Claude Code, standalone skill**

```bash
git clone https://github.com/NextAgentBC/zh-transcreation.git
cp -r zh-transcreation/skills/zh-transcreation ~/.claude/skills/
```

**Cursor**: copy [`adapters/cursor/zh-transcreation.mdc`](adapters/cursor/zh-transcreation.mdc) to `.cursor/rules/`.

**Codex**: append [`adapters/codex/AGENTS.md`](adapters/codex/AGENTS.md) to your project's `AGENTS.md`.

**Any other LLM**: paste [`adapters/generic-system-prompt.md`](adapters/generic-system-prompt.md) into the system prompt, or run the four steps in [`prompts/`](prompts/) as separate calls.

## Use

Give the agent the English source plus three things: who the Chinese reader is, what you want them to do, and which channel it is for (website, blog, Xiaohongshu, essay). Phrases like "write the Chinese version", "transcreate", "remove the translationese" trigger the skill.

The skill's default setting is Chinese-speaking small-business owners in Metro Vancouver (CAD, local place names, Xiaohongshu plus Google). For another market, swap currency, place names, holidays and keyword sources; the rest of the method is general.

## Scope and limits

- Simplified Chinese. Traditional Chinese guidance is limited to wording for Hong Kong and Taiwan readers and when to build separate pages.
- Compliance wording rules (banned superlatives, guarantees) are writing guidance, not legal advice.
- The method.md is in Chinese because the method is about Chinese.

## Credits

Built on the work of Yan Fu, Fu Lei, Qian Zhongshu, Xu Yuanchong, Yang Jiang, Yu Guangzhong, Si Guo, Lian Shuneng and others, and on Nida, Newmark, Venuti, Vermeer, Reiss and Nord. Quotations are kept to a phrase and attributed; full sources are listed at the end of method.md.

## License

Content (method, prompts, adapters, examples): [CC BY 4.0](LICENSE). There is no program code in this repository.

Attribution line:

> zh-transcreation by NextAgent (nextagent.ca) — 宋尧 Yao Song

Contributions welcome: see [CONTRIBUTING.md](CONTRIBUTING.md).
