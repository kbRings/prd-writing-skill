# prd-writing-skill

A PRD writing skill for generating Feishu PRD documents from requirements, prototypes, screenshots, and meeting transcripts.

## What This Skill Is For

This skill is intended for a workflow where the user provides:

1. requirement description
2. prototype link or prototype screenshots
3. optional meeting notes or transcript content
4. optional existing Feishu PRD docs as style references

The skill should then:

1. understand and organize the requirement first
2. align on scope and open questions before writing
3. generate a PRD in the user's established style
4. output the final result to Feishu when Feishu MCP is available
5. insert matching prototype images into the PRD when Feishu CLI image insertion is available
6. use Feishu native whiteboards for suitable process diagrams when the toolchain supports it

## Default Flow

1. input materials
2. requirement understanding
3. requirement alignment
4. PRD writing
5. Feishu doc output

## Requirement Alignment Mode

Before writing the PRD, this skill should first run a requirement-alignment stage.

This stage should follow a brainstorming-style interaction pattern:

1. ask one question at a time
2. prefer multiple-choice questions when practical
3. use each answer to narrow scope before asking the next question
4. avoid dumping a long list of questions in a single message

This is intended to make requirement confirmation easier for the user and reduce ambiguity before drafting the PRD.

## Writing Style

This skill follows a two-layer documentation style:

1. version overview docs
2. child PRD docs

The current preferred child PRD style is light and page-first:

1. `一、功能列表`
2. `二、功能详细说明`
3. page section such as `首页` or `应用市场页面说明`
4. `页面布局`
5. `页面元素说明`
6. `交互元素说明`

The latest manually corrected Feishu PRD should be treated as the style source of truth.

## Repository Structure

- `prd-writing/SKILL.md`
- `prd-writing/references/templates.md`
- `README.md`

## Using This In OpenClaw Cloud

If your OpenClaw environment is cloud-hosted, local skill folders on your laptop will usually not be visible to it.

That means the practical approach is:

1. keep this skill in a GitHub repository
2. make sure OpenClaw can access that repository
3. install or import the skill from the cloud-side workflow supported by OpenClaw

Whether the repository must be public depends on how your OpenClaw cloud instance imports skills:

1. if it only supports public repository install or public hub install, the repo must be public
2. if it supports authenticated GitHub access to private repositories, the repo can stay private

This repository is public so it is easier to consume from cloud tools.

## Using This In WorkBuddy

If WorkBuddy installs the skill by executing shell commands such as:

1. `rm -rf <dir>`
2. `git clone ...`

it may label the install flow as high risk.

This warning is usually caused by the installer command, not by the content of this skill repository.

This repository contains documentation files only:

1. `SKILL.md`
2. reference markdown files
3. `README.md`

It does not include install scripts, shell execution logic, or binary payloads.

### Recommended safer install approach for WorkBuddy

If WorkBuddy supports custom install behavior, prefer:

1. cloning into a new temporary directory instead of deleting with `rm -rf`
2. downloading repository files directly without shell cleanup
3. importing the skill from repository contents instead of running destructive shell commands

For example, using a temp directory is usually safer than:

```bash
rm -rf /tmp/prd-writing-skill && git clone ...
```

A safer pattern is:

```bash
tmpdir=$(mktemp -d)
git clone <repo> "$tmpdir"
```

This keeps the install behavior lower risk while preserving the same repository contents.

## Feishu MCP Requirement

This skill can work in two modes.

### Mode 1: With Feishu MCP

If Feishu MCP is configured and authenticated, the skill can:

1. read existing Feishu PRD docs as style references
2. read wiki or doc content before drafting
3. generate final Feishu docx output directly

This is the intended final-delivery mode.

### Mode 2: Without Feishu MCP

If Feishu MCP is not available, the skill can still:

1. understand requirements
2. organize prototypes and screenshots
3. draft PRD content in chat or markdown

But it will not be able to create the final Feishu document directly.

## What Needs To Be Configured For Feishu Output

To generate Feishu documents directly, you need:

1. a working Feishu MCP server
2. valid Feishu authentication
3. permission to read target Feishu docs if the skill needs to learn existing style
4. permission to create new Feishu docx files

In practice, that means your runtime environment must already have Feishu MCP installed and authenticated.

## Feishu CLI Enhancement

If Feishu CLI is also configured and authenticated, this skill can go beyond plain doc creation:

1. insert prototype or screenshot images under the matching `页面布局` heading
2. keep page-layout evidence inside the final Feishu PRD instead of leaving image placeholders only
3. create or update native Feishu whiteboards for normal flowcharts, decision diagrams, state diagrams, and light pseudo-swimlane diagrams

This means the most complete workflow is:

1. Feishu MCP for reading existing docs and creating the new doc
2. Feishu CLI for post-processing the doc with layout images and native whiteboard diagrams

## Expected Inputs

The skill should proceed even if the user only gives part of the information.

Preferred inputs:

- 需求名称
- 所属版本
- 需求背景
- 需求目标
- 原型链接或截图
- 核心流程
- 关键规则
- 本期不做
- 会议纪要或录音转录

## Expected Outputs

Depending on available tools and the user's request, this skill should produce one of the following:

1. requirement understanding summary
2. alignment draft with open questions
3. version overview doc
4. child PRD doc
5. Feishu PRD document link
6. Feishu PRD with inserted prototype images
7. Feishu PRD with native whiteboard process diagrams

## Notes

This skill is intended to output Feishu PRD docs directly when the user wants final delivery.

It should not claim Feishu knowledge-base placement or Feishu whiteboard generation unless the available MCP tools actually support those operations.
