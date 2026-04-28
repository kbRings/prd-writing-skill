# PRD Writing Templates

Use these only as defaults. Existing user docs take precedence.

## 1. Version Overview Doc

Use a light structure when the user's existing docs look like Lingxi AI version docs:

1. `版本信息`
2. `变更日志`
3. `需求背景与目标`
4. `需求预计上线时间`
5. `需求文档`

Keep this doc short. It answers:

- why this version exists
- what major needs are included
- when they are expected to launch
- where the prototype and PRD links live

## 2. Child PRD Doc

Use a light page-first structure when the user's existing docs look like Lingxi AI child PRDs:

1. `一、功能列表`
2. `二、功能详细说明`
3. page or section title such as `首页` `应用市场页面说明` `智能画布`
4. prototype image or screenshot
5. `页面布局`
6. `页面元素说明`
7. `交互元素说明`

Add `需求内容及解决思路` `工作流程` `接口说明` `校验与限制说明` only when the complexity requires them.

## 3. Page Element Table Pattern

Use this when the page has more than one meaningful control:

| 元素 | 类型 | 说明 |
| --- | --- | --- |
|  |  |  |

The `说明` column should cover applicable details:

- when the element appears
- default state
- what happens after interaction
- dependencies on other controls
- availability limits
- validation or prompt behavior

Prefer embedding click behavior, hover behavior, and target page routing directly in this table.

## 4. Incomplete Inputs

If details are missing, keep momentum:

- first run a requirement-alignment pass
- ask one question at a time
- prefer multiple-choice clarification
- then draft the structure
- fill with known facts from prototype or existing docs
- mark unresolved details as `待确认`

Do not stop just because the user did not provide every field.

## 5. Current Preferred Style

Based on the latest corrected Feishu PRD examples, prefer:

1. fewer section headings
2. direct page splitting
3. short page summaries
4. interaction notes expressed inside the element table
5. using the supplied image as the `页面布局`

## 6. Requirement Alignment Questions

When materials are not enough for direct drafting, the preferred question style is:

1. one question at a time
2. multiple choice when practical
3. questions aimed at narrowing:
   - scope
   - user target
   - page ownership
   - business rules
   - open implementation decisions

## 7. Diagram Selection Defaults

When the requirement may need a process diagram, choose the lightest diagram that still explains the workflow clearly.

1. `普通流程图`
Use when a single role or single user drives the process and the core problem is action order.

2. `决策流程图`
Use when branching logic is the core of the requirement and multiple `是否` decisions drive the path.

3. `状态图`
Use when the main subject is object lifecycle or status transition rather than step-by-step user actions.

4. `伪泳道图`
Use when multiple roles, clients, or systems participate but the workflow can still be expressed clearly in Mermaid through grouped sections.

5. `正式泳道图`
Use when responsibility ownership, cross-system handoffs, or parallel tracks are central and a normal flowchart would become confusing.

## 8. Diagram Rendering Defaults

Default rendering direction is vertical.

Prefer Feishu native whiteboard plus Mermaid for:

1. normal flowcharts
2. decision flowcharts
3. state diagrams
4. light pseudo-swimlane diagrams

If the process is clearly more suitable for a formal swimlane diagram than Mermaid can express cleanly, say so explicitly instead of forcing a weak diagram.

## 9. Prototype Image Placement Defaults

When prototype screenshots or page-layout images are available:

1. generate the PRD text first
2. match each image to the corresponding page section
3. insert the image under that page section's `页面布局`
4. keep multiple images for one page in source order

If the toolchain supports Feishu CLI image insertion, prefer placing the image in the final Feishu doc instead of leaving only a placeholder filename.

## 10. Feishu Native Diagram Defaults

When the selected diagram type is a normal flowchart, decision flowchart, state diagram, or light pseudo-swimlane:

1. prefer Feishu native whiteboard blocks
2. use Mermaid as the default diagram source
3. keep the default orientation vertical unless the user asks otherwise

If a process diagram is too complex for Mermaid to remain clear, say that a formal swimlane diagram is more appropriate instead of forcing a weak whiteboard rendering.
