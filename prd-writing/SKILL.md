---
name: prd-writing
description: Use when the user provides requirements plus prototypes or screenshots and wants a PRD generated directly in Feishu docs, following an established version-overview plus child-PRD structure and writing style
---

# PRD Writing

Write PRDs to match the user's existing documentation system, not a generic product template.

The default target is not an outline or discussion draft. The default target is a usable Feishu PRD document.

## When to Use

Use this skill when the user wants any of the following:

- a new PRD from rough requirements
- a PRD from prototypes or screenshots
- an existing Feishu PRD analyzed and copied in the same style
- a version overview doc plus one or more child PRDs
- a PRD generated directly into Feishu docs

Do not use this skill for technical design docs, implementation plans, or code architecture docs unless the user explicitly wants them written as PRDs.

## Workflow

1. If the user references existing Feishu docs, read those docs first and extract both structure and writing style.
2. Decide whether the deliverable is:
   - version overview doc
   - child PRD
   - both
3. Prefer the user's established hierarchy over a generic template.
4. If the input includes prototypes, screenshots, or existing pages, extract page flow, controls, states, and validation points from them.
5. Combine prototype evidence with the user's requirement description to infer PRD structure and content.
6. If inputs are incomplete, draft the document anyway and mark unresolved items as `待确认`.
7. Unless the user explicitly asks for discussion only, create the Feishu doc directly with Feishu MCP.

## Default Two-Layer Structure

When the user's system matches the Lingxi AI pattern, use two levels:

1. Version overview doc
2. Child PRD doc

Read [references/templates.md](references/templates.md) for the default structure and writing rules.

## Default Input Pattern

Assume the standard input is:

1. prototype link or prototype screenshots
2. requirement description

From that input, produce:

1. the PRD structure
2. the written PRD content
3. the Feishu doc output

Do not stop at "analysis only" unless the user explicitly asks for analysis only.

## Writing Rules

- Preserve the user's heading style and tone if reference docs exist.
- For child PRDs, keep the main line as page flow, not system architecture.
- Prefer a light structure when the user's docs are light.
- Split the child PRD directly by page or section instead of adding extra summary sections.
- Use tables for `元素 / 类型 / 说明` whenever the page has multiple controls.
- Treat prototypes and screenshots as primary evidence for page layout, flow, states, and controls.
- Treat requirement text as primary evidence for business goals, rules, constraints, and scope.
- Put interaction details into the element table when possible instead of creating too many standalone sections.
- Default child PRD shape should be close to:
  - `一、功能列表`
  - `二、功能详细说明`
  - feature or page section such as `首页`
  - `页面布局`
  - `页面元素说明`
  - `交互元素说明`
- Only add extra sections such as `工作流程` `流程图说明` `泳道图说明` `接口说明` `校验与限制说明` when the requirement complexity clearly needs them.
- If the original doc system is light-weight, do not force a heavy template.

## Inputs to Request or Infer

Prefer inferring from prototypes, screenshots, and existing docs. If information is missing, ask only when needed. Otherwise proceed and mark:

- 需求名称
- 所属版本
- 需求背景
- 需求目标
- 原型链接或截图
- 核心流程
- 关键规则
- 本期不做

If the user gives only screenshots plus a short requirement note, still proceed.

## Feishu Rules

- If the user asks to "look at my Feishu doc first", use Feishu MCP to search, resolve the node, and read the raw content before drafting.
- If Feishu auth expires, get the user to re-authorize and resume.
- You can create Feishu docs directly.
- Do not claim you can place docs into a Feishu knowledge-base tree unless the available MCP actually supports that operation.
- If the user asks for final output, prefer returning the Feishu doc link rather than only pasting the PRD in chat.

## Diagram Rules

If the PRD should include process expression:

- add `流程图说明` for single-thread user flow
- add `泳道图说明` for multi-role or multi-system collaboration

Do not claim you can create a Feishu whiteboard unless a tool explicitly supports it. If needed, provide structured diagram content inside the PRD first.

## Style Priority

If the user has already edited a generated Feishu PRD and asks you to learn from it, treat that edited version as the latest style source of truth.

Current preferred child PRD style is:

1. short structure
2. page-first organization
3. minimal narrative explanation
4. most interaction details embedded in the element table
5. page layout represented by the provided prototype or screenshot

## Output Standard

A good result should leave the user with either:

1. a Feishu version overview doc
2. a Feishu child PRD doc
3. both, written in the same style as their existing docs

If style fidelity is uncertain, say what matched and what was inferred.

## Success Standard

When the user provides prototype material plus requirement text, success means:

1. you extracted the main page flow correctly
2. you translated that into the user's PRD style
3. you generated a Feishu doc the user can review and move manually
