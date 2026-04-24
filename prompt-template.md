# PD.md Generation Prompt

> Copy this entire prompt and paste it into your coding tool (Claude Code, Cursor, Lovable, v0, Bolt, etc.).
> The tool will generate a `product_details.md` file describing your project in a format compatible with Kickoo and other PD.md tools.
>
> **将以下完整 prompt 复制粘贴到你的 coding 工具里**（Claude Code / Cursor / Lovable / v0 / Bolt 等），AI 会帮你生成一份 PD.md 格式的产品说明文档。

---

## Prompt (copy below this line 复制以下内容)

```
请为当前这个项目生成一份完整的、全面的、详细的 `product_details.md`（简称 PD.md）文档，作为后续 AI 驱动的推广内容生成的标准输入。

要求严格按照 PD.md Protocol v0.1 的结构，包含以下 8 个 Part：

---

### Frontmatter（YAML 格式，放在文件最顶部）

```yaml
---
name: <项目名>
slug: <URL 友好的短名>
tagline: <一句话描述>
url: <项目 URL，如果还没上线写 "not-launched">
version: <你当前的版本号>
pd_md_version: "0.1.0"
primary_language: <zh-CN / en>
tags: [<关键标签 3-5 个>]
---
```

---

### Part I · 愿景与起源

1. **一句话定位**：不超过 50 字，说清楚"这是什么 + 对谁"
2. **为什么此时做这个**：技术成熟度、市场变化、个人动机——至少 3 条
3. **北极星目标**：短期（3 个月）、中期（12 个月）、长期（24 个月+）各写一条

### Part II · 洞察与假设

写 3-5 条**关键用户洞察**，每条格式：
- 洞察标题（H/M/L 置信度）
- 1-2 段展开说明

再写 3-5 条**关键业务假设**，每条格式：
- 假设标题（H/M/L 置信度）
- 风险是什么
- 依赖哪些动作去验证

不确定的内容标记 `[speculation · review needed]`，由我后续审阅。

### Part III · 产品形态

1. **用户角色**：列出产品涉及的所有用户类型（通常 1-3 种），每种写清楚入口、行为、核心需求
2. **核心价值主张**：对每类用户写一句"承诺"
3. **Wow moment** ⭐（最重要字段）：用户用产品最"哇"的那 30 秒是什么？请具体描述这个瞬间的用户状态、视觉、情绪。这个字段会被下游 AI 工具用来设计 playable 可玩内容。

### Part IV · 功能全景

按用户角色分别列出已实现功能，用表格或列表。每个功能标注：
- 路由/入口
- 用途
- 实现状态（已完成 / 进行中 / 未开始）

### Part V · 技术架构

1. **技术栈总览**（前端/后端/存储/部署，一段 ASCII 图最佳）
2. **关键技术决策**（D1, D2, D3 ...）—— 每个决策包含：ID、决策内容、理由
3. **数据模型**：列出主要表和用途
4. **部署方式**：单机/多机、服务商、域名状态（含 ICP 备案状态如果在中国）

### Part VI · 运营思路

1. **目标用户画像**：具体到"他们平时出没在哪里"
2. **冷启动策略**：你现在的计划是什么？（定向邀请 / 开放注册 / 社区种子）
3. **已尝试的推广动作**：做过什么、效果如何——如实写，包括失败的
4. **变现模式假设**：阶段 1/2/3 的假设，标记 H/M/L

### Part VII · 路线图

1. **已实现**（打钩列表 ✅）
2. **下一步（当季度）**
3. **中长期愿景（6-12 个月后）**

### Part VIII · 附录

1. **决策日志**：时间逆序，关键决策 + 日期
2. **已知坑 / 技术债**：诚实列出
3. **术语表**：项目特有词汇解释

---

### 生成要求

- **字数目标**：8,000–15,000 字，宁可详细不要简略
- **风格**：专业、具体、有数字、有细节、承认不确定性
- **语言**：主语言用中文，技术词汇保留英文（比如 RSC、SSR、OTP 不需要翻译）
- **事实来源**：优先基于代码和已有文档提取，推测内容明确标记 `[speculation · review needed]`
- **诚实度**：写真实状态而不是理想状态。"0 付费用户"就写 0，"还没写完"就写还没写完
- **交付**：直接在项目根目录创建 `product_details.md`，不要在对话里输出，写完告诉我"已写入 product_details.md"

请开始。
```

---

## Tips 使用技巧

1. **第一次生成后，人工审阅 Part II 和 Part VI**——这两部分最容易被 AI 编造，需要你亲自核对
2. **保持 PD.md 和代码同步**——每次重大功能更新后重新跑一次 prompt，AI 会基于最新代码更新文档
3. **把 PD.md 提交到 Git**——它是你的产品"宪法"，值得版本控制
4. **对多人项目**：建议每位核心成员都审阅一遍 PD.md，形成共识

---

## Troubleshooting

**AI 生成的 PD.md 太短？**
- 明确告诉它"字数不少于 10000 字"
- 让它一次只写一个 Part，分 8 次生成

**Part II 洞察部分感觉被编造？**
- 这是 AI 常见问题，Part II 的洞察来自产品 session 上下文和代码注释
- 审阅时把不符的删掉，AI 不会记恨

**技术栈部分不够准确？**
- 让 AI 先 `cat package.json` 再生成 Part V
- 对于后端项目，让它先看 Dockerfile / docker-compose

---

© Kickoo · MIT License · [github.com/kickoo/pd-md](https://github.com/kickoo/pd-md)
