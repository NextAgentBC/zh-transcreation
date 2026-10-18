# zh-transcreation：让英文变成像中文写的中文

一句话：zh-transcreation 是给 AI 代理用的中文创译方法，英文只当素材，中文按中文的习惯重写，读着不像译文。

English: [README.md](README.md)

## 同一句话，两种中文

> English：Ready to unlock your business's full potential? Our comprehensive solutions empower you to maximize local visibility.
>
> 逐句翻译：准备好释放您业务的全部潜力了吗？我们全面的解决方案赋能您最大化本地可见性。
>
> 创译：想让附近的人搜得到你？网站、Google 商家、小红书，我们一起帮你做。

逐句翻译那版，每个词都对得上，可没有哪个老板会这么说话。创译只留下意思：让附近的客人找到你。英文的句子形状、抽象名词、推销口气，统统不带过来。

## 为什么要这样做

英文好文章逐句翻过来，多半是坏中文。大模型也一样，它顺着英文的句子走，被动句、长定语、满篇的「您」就跟着来了。提示词里只写「要地道」，几乎没用。

有用的是三件事：

1. 先写纲要：读者是谁，读完要他做什么，哪些事实不能动。这时还不写中文。
2. 让模型只看纲要写中文，不给英文句子。没有句子可照着译，只能用中文想。
3. 拿具体的清单审一遍，再删一遍多余的字。

研究也指向这里：先译后润色，能把 GPT-4 英译中稿子里翻译腔明显的比例从 43% 降到 25%（Li 等，ACL 2025）。写出具体的语言学指令，比让模型自己判断更好（Kunilovskaya 等，EAMT 2024）。

## 仓库里有什么

| 位置 | 内容 |
|---|---|
| [`skills/zh-transcreation/SKILL.md`](skills/zh-transcreation/SKILL.md) | 代理技能本体：总框架、六步流程、30 条去翻译腔清单、文案与合规规范、中文 SEO 和 GEO |
| [`skills/zh-transcreation/method.md`](skills/zh-transcreation/method.md) | 完整方法：从严复、傅雷到奈达、纽马克的译论，英汉对比十条，每条清单带例句，附全部来源 |
| [`prompts/`](prompts/) | 三段提示词：抽纲要、只看纲要写、审校打分。哪个模型都能用 |
| [`adapters/`](adapters/) | Cursor 规则、Codex 的 `AGENTS.md` 片段、通用系统提示词 |
| [`examples/`](examples/) | 改写前后对照，来自真实页面（nextagent.ca，2026-10） |

## 安装

**Claude Code 插件**

```bash
/plugin marketplace add NextAgentBC/zh-transcreation
/plugin install zh-transcreation@nextagent
```

在终端里也可以写成 `claude plugin marketplace add NextAgentBC/zh-transcreation`，再 `claude plugin install zh-transcreation@nextagent`。

**Claude Code 独立技能**

```bash
git clone https://github.com/NextAgentBC/zh-transcreation.git
cp -r zh-transcreation/skills/zh-transcreation ~/.claude/skills/
```

**Cursor**：把 [`adapters/cursor/zh-transcreation.mdc`](adapters/cursor/zh-transcreation.mdc) 放进项目的 `.cursor/rules/`。

**Codex**：把 [`adapters/codex/AGENTS.md`](adapters/codex/AGENTS.md) 的内容接在项目的 `AGENTS.md` 后面。

**其他模型**：把 [`adapters/generic-system-prompt.md`](adapters/generic-system-prompt.md) 整段贴进系统提示词。想拆开跑，就按 [`prompts/`](prompts/) 分三次调用，最后用代码做校验。

## 怎么用

对代理说清三件事：英文原稿，中文读者是谁，读完要他做什么。再补一句发在哪（网站、博客、小红书、随笔）。

「帮我写中文版」「创译一下」「去掉翻译腔」，这几句话都会触发技能。它先交一份纲要给你看，你点头，再写正文。

写完它还会逐条对照清单，改一遍，删一遍。删到读着局促就停。

## 换成你的市场

默认场景是大温哥华讲中文的小企业老板：金额写加元，地名用中文，渠道是 Google 加小红书。你要写给别的地方的读者，只需换掉货币、地名、节日和选词渠道，其余照用。

## 这份方法的边界

- 只管简体中文。繁体只讲怎么照顾港台读者的说法，以及什么时候值得单做一版。
- 合规用语表是写作建议，不是法律意见。发布前请按当地法规和平台规则再核对。
- 小红书的做法来自公开资料和实际经验，平台规则常改，请自己核实。

## 致谢

方法站在许多人肩上：严复、傅雷、钱锺书、许渊冲、杨绛、余光中、思果、连淑能，还有奈达、纽马克、韦努蒂、弗米尔、赖斯和诺德。引文只留一句半句，注明出处；完整来源在 method.md 末尾。

## 许可

方法、提示词、适配器和例子用 [CC BY 4.0](LICENSE)。仓库里没有程序代码。

转载或改写时，请保留这一行：

> zh-transcreation by NextAgent (nextagent.ca) — 宋尧 Yao Song

想补例子、提清单新条目，看 [CONTRIBUTING.md](CONTRIBUTING.md)。
