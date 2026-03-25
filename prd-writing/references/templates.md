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

- draft the structure
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
