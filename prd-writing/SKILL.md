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
4. During requirement confirmation and alignment, explicitly follow the brainstorming style:
   - ask one question at a time
   - prefer multiple-choice questions
   - use the answers to narrow scope before writing
5. If the input includes prototypes, screenshots, or existing pages, extract page flow, controls, states, and validation points from them.
6. Combine prototype evidence with the user's requirement description to infer PRD structure and content.
7. If inputs are incomplete, do not jump straight to the PRD. First run a requirement-alignment pass and collect missing decisions.
8. If unresolved items remain after alignment, draft the document anyway and mark them as `待确认`.
9. Unless the user explicitly asks for discussion only, create the Feishu doc directly with Feishu CLI.
10. If prototype screenshots or page-layout images are available, insert them into the final Feishu doc after the matching `页面布局` heading when the available Feishu CLI flow supports it.
11. If a process diagram is needed and Feishu native whiteboard tooling is available, prefer embedding a native whiteboard block over leaving only text-based flow notes.

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
4. the matching prototype image insertion when images are available and the toolchain supports it

Do not stop at "analysis only" unless the user explicitly asks for analysis only.

## Requirement Alignment Mode

Before writing the PRD, the default behavior is to run a requirement-alignment stage.

This stage should follow the brainstorming interaction pattern:

1. understand the materials first
2. ask one question at a time
3. prefer multiple-choice questions over broad open questions
4. use the conversation to narrow:
   - scope
   - target users
   - page boundaries
   - rules
   - open decisions
5. if the PRD may need diagrams, decide the diagram type before drafting:
   - normal flowchart
   - decision flowchart
   - state diagram
   - pseudo-swimlane diagram
   - formal swimlane diagram

Only after that alignment should the skill move into PRD drafting, unless the user explicitly skips alignment.

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
- 页面布局图片或原型截图
- 核心流程
- 关键规则
- 本期不做

If the user gives only screenshots plus a short requirement note, still proceed.

When asking for missing information during alignment:

- ask one question at a time
- prefer options such as `A / B / C`
- avoid dumping a long list of questions in a single message
- use the user's answer to update the next question

## Feishu Rules

- If the user asks to "look at my Feishu doc first", use Feishu CLI to fetch the existing doc content before drafting when the CLI environment supports it.
- If Feishu auth expires, get the user to re-authorize and resume.
- Use Feishu CLI as the default and preferred toolchain for:
  - creating Feishu docs
  - reading existing Feishu docs as style references
  - inserting local prototype or screenshot images after drafting
  - placing images under the matching `页面布局` heading when the PRD structure is clear enough
  - creating or updating native Feishu whiteboards for process diagrams
- Do not claim you can place docs into a Feishu knowledge-base tree unless the available toolchain actually supports that operation.
- If the user asks for final output, prefer returning the Feishu doc link rather than only pasting the PRD in chat.

When using Feishu CLI for image insertion:

1. generate the PRD body first
2. map each prototype image to the matching page section
3. insert each image under the corresponding `页面布局` heading
4. if exact placement is ambiguous, ask one focused question or state the inferred placement briefly

When using Feishu CLI for process diagrams:

1. prefer native whiteboard blocks for Mermaid-based flowcharts, decision diagrams, and state diagrams
2. if native whiteboard is unavailable, fall back to structured `流程图说明` or a static image
3. do not promise formal swimlane rendering unless the chosen toolchain truly supports it

## Diagram Rules

If the PRD should include process expression:

- add `流程图说明` for single-thread user flow
- add `泳道图说明` for multi-role or multi-system collaboration
- default diagram direction is vertical unless the user asks otherwise
- prefer Feishu native whiteboard plus Mermaid for:
  - normal flowcharts
  - decision flowcharts
  - state diagrams
- prefer a pseudo-swimlane structure for multi-role or multi-system flows when Mermaid is still sufficient
- if the process clearly involves many roles, systems, or parallel responsibilities, call out that a formal swimlane diagram is more suitable than a plain flowchart
- do not force every need into the same diagram type; choose based on process shape
- if the diagram can live as a native Feishu whiteboard, prefer that over a static screenshot

Before drafting a diagram, classify the need using these defaults:

1. `普通流程图`
   - use when a single user or single role drives the main flow
   - use when the main value is step order, page transitions, or action sequence
2. `决策流程图`
   - use when conditional branches are the core of the process
   - use when the flow contains repeated `是否` or rule-based branching
3. `状态图`
   - use when the core question is how an object changes state over time
   - use for drafts, approvals, generation states, order states, and similar lifecycle needs
4. `伪泳道图`
   - use when multiple roles, clients, or systems participate
   - use when Mermaid can still express responsibility boundaries clearly enough through grouped sections
5. `正式泳道图`
   - use when more than three participants or systems are involved
   - use when ownership boundaries, parallel tracks, or cross-system handoffs are central
   - if the toolchain is still light-weight, explain that the requirement is better suited to a formal swimlane diagram even if the current output remains a pseudo-swimlane

The default diagram strategy is:

1. first check whether the process is primarily a state problem
2. then check whether it is multi-role or multi-system
3. if yes, decide whether pseudo-swimlane is enough
4. if not, choose between normal flowchart and decision flowchart
5. only skip diagrams when the requirement is too trivial to benefit from one

Do not claim you can create a Feishu whiteboard unless a tool explicitly supports it. If needed, provide structured diagram content inside the PRD first.

## Image And Layout Rules

When the user provides prototype images or screenshots:

1. treat them as evidence for page structure and layout
2. map each image to the matching page section in the PRD
3. after the PRD text is generated, insert the image under the corresponding `页面布局` heading when Feishu CLI is available
4. if multiple screenshots belong to one page, preserve their order and use short captions when helpful
5. if an image only illustrates part of a page, still place it near the matching page section instead of dropping it at the end of the doc

Default layout-image strategy:

1. generate PRD body
2. identify each `页面布局` section
3. insert the matching image under that section
4. then add any process whiteboard or flowchart content

## Style Priority

If the user has already edited a generated Feishu PRD and asks you to learn from it, treat that edited version as the latest style source of truth.

Current preferred child PRD style is:

1. short structure
2. page-first organization
3. minimal narrative explanation
4. most interaction details embedded in the element table
5. page layout represented by the provided prototype or screenshot

## Brainstorming Dependency

This skill depends on the behavior of the `brainstorming` skill during requirement confirmation.

That means:

1. requirement confirmation should be conversational
2. questions should be sequential, not dumped all at once
3. multiple-choice questions are preferred when practical
4. the PRD should only be written after the requirement has been aligned enough to avoid obvious ambiguity

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
