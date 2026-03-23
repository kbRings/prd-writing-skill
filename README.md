# prd-writing-skill

A Codex skill for generating PRD documents from requirements, prototypes, and screenshots.

## What It Does

This skill is designed for a workflow where the user provides:

1. requirement description
2. prototype link, prototype screenshots, or existing page screenshots

From that input, the skill should:

1. extract page flow, controls, states, and validation points
2. follow the user's established PRD writing style
3. generate a Feishu PRD document directly

## Target Output

The default output is not a discussion draft.

The default output is a usable Feishu PRD document.

Depending on the user's documentation system, the skill can produce:

1. a version overview doc
2. a child PRD doc
3. both

## Writing Style Assumption

This skill was shaped around a two-layer PRD structure similar to:

1. version overview docs for release-level background and targets
2. child PRD docs for page flow, controls, rules, and output behavior

The skill prefers the user's existing documentation structure over a generic PRD template.

## Feishu Workflow

When the user asks for Feishu output, the skill should:

1. read referenced Feishu docs first if they are part of the user's style reference
2. infer structure from existing docs, prototypes, and screenshots
3. generate the final PRD directly into Feishu docs

## Typical Input

The skill should proceed even if the user only gives partial information.

Preferred inputs:

- 需求名称
- 所属版本
- 需求背景
- 需求目标
- 原型链接或截图
- 核心流程
- 关键规则
- 本期不做

If details are incomplete, unresolved items should be marked as `待确认` instead of blocking progress.

## Repository Structure

- `prd-writing/SKILL.md`: main skill definition
- `prd-writing/references/templates.md`: default reference structure and writing rules

## Notes

This skill is intended to help generate Feishu PRD docs, but it should not claim to place documents into a Feishu knowledge-base tree unless the available MCP tools actually support that operation.
