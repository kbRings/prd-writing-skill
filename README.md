# prd-writing-skill

A Codex skill for generating Feishu PRD documents from requirements, prototypes, screenshots, and meeting transcripts.

## What It Does

This skill supports a workflow where the user provides requirement text, prototype links or screenshots, and optionally meeting notes or transcripts.

The skill should:

1. understand and organize the requirement first
2. align on scope and open questions before writing
3. generate a Feishu PRD document in the user's established style

## Default Flow

1. input materials
2. requirement understanding
3. requirement alignment
4. PRD writing
5. Feishu doc output

## Writing Style

This skill follows a two-layer documentation style:

1. version overview docs
2. child PRD docs

The current preferred child PRD style is light and page-first:

1. 一、功能列表
2. 二、功能详细说明
3. page section such as 首页 or 应用市场页面说明
4. 页面布局
5. 页面元素说明
6. 交互元素说明

The latest manually corrected Feishu PRD should be treated as the style source of truth.

## Repository Structure

- prd-writing/SKILL.md
- prd-writing/references/templates.md
- README.md

## Notes

This skill is intended to output Feishu PRD docs directly when the user wants final delivery.
