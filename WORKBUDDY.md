# WorkBuddy Safe Installation Guide

This document explains how to install `prd-writing-skill` in WorkBuddy without using `rm -rf`.

## Why This Exists

Some installers use a pattern like:

```bash
rm -rf /tmp/prd-writing-skill && git clone <repo>
```

This may trigger a high-risk warning because `rm -rf` is treated as a destructive shell operation.

For this skill, that cleanup step is not required.

## Important Note

This repository contains documentation files only:

1. `prd-writing/SKILL.md`
2. `prd-writing/references/templates.md`
3. `README.md`

There are no install scripts, binaries, or system-level operations required to use the skill.

## Recommended Installation Options

### Option 1: Read Repository Files Directly

If WorkBuddy can import a skill from repository contents, read these files directly:

1. `prd-writing/SKILL.md`
2. `prd-writing/references/templates.md`

This is the safest option and does not require shell cleanup at all.

### Option 2: Clone Into a Fresh Temporary Directory

If WorkBuddy must use `git clone`, use a fresh temp directory instead of deleting a fixed directory.

Example:

```bash
tmpdir=$(mktemp -d)
git clone https://github.com/kbRings/prd-writing-skill.git "$tmpdir"
```

This avoids `rm -rf` while preserving the same repository content.

### Option 3: Download ZIP Instead of Cloning

If WorkBuddy supports downloading archives, use the GitHub ZIP archive instead of a clone-and-delete workflow.

Repository:

- https://github.com/kbRings/prd-writing-skill

## What WorkBuddy Actually Needs

To consume the skill, WorkBuddy only needs access to the markdown files inside the repository.

It does not need:

1. shell cleanup
2. forced directory deletion
3. any install script execution

## Suggested WorkBuddy Handling

If WorkBuddy supports custom install logic, prefer one of these:

1. direct file fetch from GitHub
2. ZIP download and extract
3. clone into a unique temp directory

Avoid using:

```bash
rm -rf <dir>
```

unless the platform has no safer alternative.

## Feishu Output Reminder

This skill can generate Feishu PRD documents only when the runtime environment already has a working Feishu MCP server with valid authentication.

Without Feishu MCP, the skill can still help with:

1. requirement understanding
2. requirement alignment
3. PRD drafting

but it cannot create the final Feishu document directly.