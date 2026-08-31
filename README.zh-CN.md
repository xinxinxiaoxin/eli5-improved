# ELI5 中文图文增强版

[English](README.md) | **简体中文**

这是基于 [DreambigOu/ELI5](https://github.com/DreambigOu/ELI5) 改编的通用 Agent skill。它能把复杂主题、代码、文档和错误信息转换成适合目标受众理解的解释，并默认生成中文 HTML 图文页面。它是手动调用型 skill，不会自动触发；如果没有指定受众，默认按 5 岁儿童风格生成。

## 主要增强

- 除代码、原文、专有名词和必要技术术语外，默认使用简体中文。
- 默认生成完整、响应式的 HTML 图文解释。
- 根据年龄、教育程度、职业和关系，同时调整文字风格与视觉设计。
- 用户明确要求 Markdown、纯文本、Word、PDF、邮件或其他文档格式时，切换为指定输出。
- 在降低理解门槛的同时，保留技术准确性、关键边界和必要术语。
- 只有显式调用 `$eli5-improved` 时才运行，不会因为普通的解释请求自动介入。Codex 通过 `agents/openai.yaml` 实现这一点；其他 Agent 请启用对应的“仅显式调用”设置。
- 调用时未指定受众，默认使用 5 岁儿童受众风格。

## 安装

本仓库本身就是一个完整的 skill 文件夹。最简单的安装方式是直接把下面的命令发送给你的 Agent。

### Codex 安装命令

```text
请从 GitHub 安装这个 skill：https://github.com/xinxinxiaoxin/eli5-improved
将它安装到你的 skills 目录，刷新 skill 列表，并确认我可以通过 $eli5-improved 手动调用它。安装完成后告诉我安装路径和验证结果。
```

### 通用 Agent 安装命令

```text
请安装 GitHub 仓库 https://github.com/xinxinxiaoxin/eli5-improved 中的 Agent skill。
请根据你支持的 skill 安装机制把它注册到可用 skills 中，确认根目录包含 SKILL.md，并启用仅显式调用模式。安装完成后重新加载 skills，并确认可以通过 $eli5-improved 手动调用。
```

如果 Agent 支持直接从 GitHub 安装，它会自动选择合适的本地目录和安装方式；如果不支持，请让 Agent 说明所需的安装方式，不要把仓库文件放到任意工作目录。

## 受众与视觉风格指南

开始编写具体调用语句前，请先阅读公开的[受众与视觉风格指南](references/audience-styles.md)。文件列出了年龄、教育程度、职业和关系等受众类型，以及对应的词汇、类比来源、信息密度和视觉方向。

可以在调用中选择一个或多个受众条件：

```text
使用 $eli5-improved 给 10 岁孩子解释。
使用 $eli5-improved 给大学水平的初级工程师解释。
使用 $eli5-improved 给 45 岁的工程总监解释。
```

如果省略这些条件，skill 默认使用 5 岁儿童风格。

## 使用示例

### 给儿童解释概念

```text
使用 $eli5-improved 给 10 岁孩子解释数据库索引。生成默认 HTML 图文解释，并使用学校图书馆作为核心类比。
```

预期效果：生成活泼但不过度幼稚的 HTML 页面，包含简单的查找流程、使用索引前后的对比，以及适合该年龄的语言。

### 给产品经理生成文档

```text
使用 $eli5-improved 给一位产品经理解释 API 限流。使用 Markdown 文档返回，包含用户影响、高峰期失败风险、可选实现方案以及需要做出的产品决策。
```

预期效果：使用产品经理关心的业务视角，但遵循明确的 Markdown 要求，不生成 HTML。

### 为初级工程师诊断生产错误

```text
使用 $eli5-improved 阅读我提供的错误堆栈和身份验证中间件代码，向大学水平的初级工程师解释根因。生成 HTML 图文解释，包含请求时间线、触发故障的状态变化、最小复现、两种修复方案及其取舍，并保持相关代码标识符不变。
```

预期效果：生成技术学习页面，包含准确术语、请求流程图、渐进展开的细节和可执行的调试建议。

### 向工程总监解释架构决策

```text
使用 $eli5-improved 阅读 architecture.md 和部署成本数据，向一位 45 岁的工程总监解释从单体架构迁移到事件驱动架构的方案。生成中文 HTML 决策简报，包含当前与目标架构流程、分阶段迁移路线、风险矩阵、成本与时间对比以及最终建议。保留 Kafka、idempotency 和 eventual consistency 等技术术语，并在第一次出现时解释。
```

预期效果：生成克制、面向决策的 HTML 简报，同时结合该年龄群体的可读性需求和工程总监关注的战略重点。

## 输出模式

| 用户要求 | 输出结果 |
| --- | --- |
| 未指定格式 | 完整、匹配受众的 HTML 图文解释 |
| HTML、网页、图文解释 | 完整 HTML 图文解释 |
| 只说文档样式，未指定文件类型 | 结构化 Markdown |
| Markdown 或纯文本 | 用户指定的文本形式 |
| Word、PDF、邮件、报告或备忘录 | 用户指定的文档形式 |

## 仓库结构

```text
eli5-improved/
|-- SKILL.md
|-- agents/
|   `-- openai.yaml
`-- references/
    |-- audience-styles.md
    `-- html-output-spec.md
```

## 许可与归属

本项目使用 MIT License。原始受众分类和解释框架来自 [DreambigOu/ELI5](https://github.com/DreambigOu/ELI5)。本仓库增加了中文化、输出形式路由和多受众视觉设计规范。
