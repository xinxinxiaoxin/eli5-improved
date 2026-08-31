# ELI5 Improved: Chinese Visual Explainer

**English** | [简体中文](README.zh-CN.md)

A reusable agent skill adapted from [DreambigOu/ELI5](https://github.com/DreambigOu/ELI5). It turns complex topics, code, documents, and errors into audience-aware explanations, with Chinese visual HTML as the default output. It is manual-only: it is never invoked automatically. When no audience is specified, it defaults to a 5-year-old style.

## What It Adds

- Uses Simplified Chinese except where code, source text, proper nouns, or technical terms should remain unchanged.
- Generates a complete, responsive HTML visual explainer by default.
- Changes both writing style and visual design for different ages, education levels, professions, and relationships.
- Switches to Markdown, plain text, Word, PDF, email, or another document format when the user explicitly requests it.
- Preserves technical accuracy while adapting vocabulary, examples, information density, diagrams, and interaction patterns.
- Runs only when explicitly called as `$eli5-improved`; it does not activate from ordinary explanation requests. Codex users get this behavior from `agents/openai.yaml`; other agents should enable their equivalent explicit-only setting.
- Defaults to a 5-year-old audience when the invocation does not specify an audience.

## Installation

This repository is a self-contained skill folder. The easiest way to install it is to send one of the following instructions directly to your agent.

### Codex Install Command

```text
请从 GitHub 安装这个 skill：https://github.com/xinxinxiaoxin/eli5-improved
将它安装到你的 skills 目录，刷新 skill 列表，并确认我可以通过 $eli5-improved 手动调用它。安装完成后告诉我安装路径和验证结果。
```

### General Agent Install Command

```text
请安装 GitHub 仓库 https://github.com/xinxinxiaoxin/eli5-improved 中的 Agent skill。
请根据你支持的 skill 安装机制把它注册到可用 skills 中，确认根目录包含 SKILL.md，并启用仅显式调用模式。安装完成后重新加载 skills，并确认可以通过 $eli5-improved 手动调用。
```

如果 Agent 支持直接从 GitHub 安装，它会自动选择合适的本地目录和安装方式；如果不支持，请让 Agent 说明所需的安装方式，而不要把仓库文件放到任意工作目录。

## Audience and Visual Style Guide

Read the public [Audience and Visual Style Guide](references/audience-styles.md) before writing a detailed invocation. It lists the available age, education, profession, and relationship profiles, including their vocabulary, analogy sources, information density, and visual direction.

Choose one or more profiles in your request, for example:

```text
Use $eli5-improved for a 10-year-old.
Use $eli5-improved for a college-level junior engineer.
Use $eli5-improved for a 45-year-old engineering director.
```

If you omit these profiles, the skill uses the 5-year-old profile by default.

## Usage Examples

### Explain a Concept to a Child

```text
Use $eli5-improved to explain database indexes to a 10-year-old. Generate the default HTML visual explainer and use a school library analogy.
```

Expected behavior: a playful but not childish HTML page with a simple lookup flow, before-and-after comparison, and age-appropriate language.

### Produce a Document for a Product Manager

```text
Use $eli5-improved to explain API rate limiting to a product manager. Return a Markdown document covering user impact, peak-hour failure risk, implementation options, and the decision that needs to be made.
```

Expected behavior: the skill uses a product-management perspective but follows the explicit Markdown request instead of generating HTML.

### Diagnose a Production Error for a Junior Engineer

```text
Use $eli5-improved to read the attached stack trace and authentication middleware. Explain the root cause to a junior engineer at college level. Generate an HTML explainer containing the request timeline, the state transition that triggers the failure, a minimal reproduction, two fix options with trade-offs, and the relevant code identifiers unchanged.
```

Expected behavior: a technical learning page with accurate terminology, a request-flow diagram, progressive detail, and practical debugging guidance.

### Explain an Architecture Decision to an Engineering Director

```text
Use $eli5-improved to read architecture.md and the deployment cost data. Explain the proposed migration from a monolith to an event-driven architecture to a 45-year-old engineering director. Generate a Chinese HTML briefing with the current and proposed architecture flows, a phased migration roadmap, a risk matrix, cost and timeline comparisons, and a final recommendation. Keep Kafka, idempotency, and eventual consistency as technical terms and define them on first use.
```

Expected behavior: a restrained, decision-focused HTML briefing that combines the readability needs of the age group with the strategic priorities of the role.

## Output Modes

| User request | Output |
| --- | --- |
| No format specified | Complete audience-specific HTML visual explainer |
| HTML, webpage, visual explanation | Complete HTML visual explainer |
| Document style without a file type | Structured Markdown |
| Markdown or plain text | Requested text format |
| Word, PDF, email, report, or memo | Requested document format |

## Repository Structure

```text
eli5-improved/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
`-- references/
    |-- audience-styles.md
    `-- html-output-spec.md
```

## License and Attribution

Released under the MIT License. The original audience classification and explanation framework come from [DreambigOu/ELI5](https://github.com/DreambigOu/ELI5). This repository adds Chinese localization, output-mode routing, and multi-audience visual design guidance.
