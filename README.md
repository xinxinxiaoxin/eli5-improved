# ELI5 中文图文增强版

这是基于 [DreambigOu/ELI5](https://github.com/DreambigOu/ELI5) 改编的 Codex skill。

它保留了原版按年龄、教育程度、职业和关系调整解释方式的能力，并增加：

- 除必要技术术语外，默认使用简体中文。
- 默认生成完整、响应式的 HTML 图文解释。
- 不同年龄和职业使用不同的信息密度、类比方式与页面视觉风格。
- 用户明确要求文档、Markdown、纯文本、Word 或 PDF 时，遵循指定格式。

## 安装

将仓库克隆到 Codex skills 目录：

```powershell
git clone https://github.com/xinxinxiaoxin/eli5-improved.git "$env:USERPROFILE\.codex\skills\eli5-improved"
```

也可以下载仓库 ZIP，解压后确保目录结构为：

```text
~/.codex/skills/eli5-improved/
|-- SKILL.md
|-- agents/
`-- references/
```

重新启动或刷新 Codex 后即可使用。

## 示例

```text
用 ELI5 给 10 岁孩子解释数据库索引。
```

默认生成适合 10 岁读者的 HTML 图文页。

```text
给一位产品经理解释 API 限流，用 Markdown 文档返回。
```

此时会使用产品经理视角，但按用户要求返回 Markdown，而不是 HTML。

## 许可与归属

本项目使用 MIT License。原始受众分类和解释框架来自 [DreambigOu/ELI5](https://github.com/DreambigOu/ELI5)，本仓库进行了中文化、输出形式和多受众视觉规范扩展。
