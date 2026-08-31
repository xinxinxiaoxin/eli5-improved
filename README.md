# ELI5 Improved: Chinese Visual Explainer

**English** | [简体中文](README.zh-CN.md)

A reusable agent skill adapted from [DreambigOu/ELI5](https://github.com/DreambigOu/ELI5). It turns complex topics, code, documents, and errors into audience-aware explanations, with Chinese visual HTML as the default output. It is manual-only: it is never invoked automatically.

## What It Adds

- Uses Simplified Chinese except where code, source text, proper nouns, or technical terms should remain unchanged.
- Generates a complete, responsive HTML visual explainer by default.
- Changes both writing style and visual design for different ages, education levels, professions, and relationships.
- Switches to Markdown, plain text, Word, PDF, email, or another document format when the user explicitly requests it.
- Preserves technical accuracy while adapting vocabulary, examples, information density, diagrams, and interaction patterns.
- Runs only when explicitly called as `$eli5-improved`; it does not activate from ordinary explanation requests. Codex users get this behavior from `agents/openai.yaml`; other agents should enable their equivalent explicit-only setting.

## Installation

This repository is a self-contained skill folder. It can be used by Codex and by other general-purpose agents that support directory-based skills with a `SKILL.md` entrypoint.

### Codex

macOS or Linux:

```bash
mkdir -p "${CODEX_HOME:-$HOME/.codex}/skills"
git clone https://github.com/xinxinxiaoxin/eli5-improved.git "${CODEX_HOME:-$HOME/.codex}/skills/eli5-improved"
```

Windows PowerShell:

```powershell
$skillsDir = if ($env:CODEX_HOME) { Join-Path $env:CODEX_HOME "skills" } else { Join-Path $env:USERPROFILE ".codex\skills" }
New-Item -ItemType Directory -Force -Path $skillsDir | Out-Null
git clone https://github.com/xinxinxiaoxin/eli5-improved.git (Join-Path $skillsDir "eli5-improved")
```

### Other Compatible Agents

Clone the repository into the skills directory recognized by your agent:

```bash
git clone https://github.com/xinxinxiaoxin/eli5-improved.git /path/to/your-agent/skills/eli5-improved
```

The final folder must contain `SKILL.md` at its root. Refresh or restart the agent after installation if it does not automatically rediscover skills.

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
