# Step 1 / 抽纲要

Input: the English article. Output: JSON brief, no Chinese body text. Use any model that can follow a JSON schema.

Variables to fill in: {business}, {business_description}, {audience}, {locale}, {zh_keywords}, {title_en}, {content_en_md}

```text
你是 {business}（{business_description}）的中文内容策划。
下面是一篇英文文章。你的任务不是翻译，而是为一位中文作者写一份「写作纲要」。
不要输出任何中文正文句子。

目标中文关键词（由编辑提供）：{zh_keywords}
目标读者：{audience}
（例：大温哥华讲中文的小企业老板，不懂技术，重实际，讨厌夸大）。

请输出一个 JSON：
{
  "skopos": {
    "reader": "<具体是谁，一句话>",
    "reader_question": "<他搜索或提问时的原话，中文>",
    "desired_action": "<读完要他做什么：下单 / 预约 / 咨询 / 只建立信任>",
    "channel": "<网站博客 / 服务页 / 小红书 / 个人随笔>"
  },
  "core_message_zh": "<一句话核心观点，用中文意思写，不要逐字译英文>",
  "facts": [
    {"fact": "<事实、数字、价格、日期、出处、承诺范围>", "source": "<原文出处或链接>"}
  ],
  "not_promised": ["<原文明确不承诺的事项，例如排名、流量>"],
  "drop_or_replace": [
    {"item": "<原文中不适合中文读者的内容：美式比喻、美国数据、夸大说法、与本地无关的例子>",
     "action": "删 / 换成本地例子 / 换成加拿大数据 / 弱化为可证实说法"}
  ],
  "outline_zh": [
    {"h2": "<中文读者会问的问题，作为小标题>", "points": ["<要点，用中文意思写>"]}
  ],
  "local_examples": ["<可替换的本地场景，例如 {locale} 的餐厅、会计所>"],
  "faq_questions_zh": ["<4 个客人真会问的问题>"]
}

规则：
- facts 只能来自原文或编辑提供的资料，不得补充。
- 原文里的「最好、唯一、保证、彻底改变、无与伦比」之类说法，放进 drop_or_replace，不要进 facts。
- outline 的顺序按中文读者的提问顺序排，不必跟英文段落顺序一致。

英文标题：{title_en}
英文正文：
<<<ARTICLE>>>
{content_en_md}
<<<END>>>
```

Part of [zh-transcreation](https://github.com/NextAgentBC/zh-transcreation) by NextAgent (nextagent.ca), 宋尧 Yao Song. CC BY 4.0.
