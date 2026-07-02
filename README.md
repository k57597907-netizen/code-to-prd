# code-to-prd

Codex skill for reverse-engineering a GitHub repository, local checkout, frontend app, backend service, or fullstack codebase into a Product Requirements Document (PRD).

This fork is optimized for Codex usage, especially Chinese prompts such as "拆解 GitHub 代码并生成 PRD". It keeps the original Code -> PRD workflow, scripts, reference files, and examples, while adding clearer Codex defaults for repository inspection, local path handling, Chinese output, and large-repo batching.

## What It Does

- Scans project structure, framework, routes, pages, APIs, models, enums, permissions, and data flows.
- Distinguishes real API integrations from mock data and fixtures.
- Generates a PRD directory structure with system overview, page-level docs, API inventory, enum dictionary, and page relationships.
- Works for frontend, backend, and fullstack projects.
- Writes business-readable requirements while preserving implementation details needed by engineers or coding agents.

## Repository Layout

```text
.
├── README.md
├── LICENSE
├── NOTICE.md
└── skills/
    └── code-to-prd/
        ├── SKILL.md
        ├── assets/
        ├── expected_outputs/
        ├── references/
        └── scripts/
```

The installable Codex skill lives at:

```text
skills/code-to-prd
```

## Install In Codex

Use Codex's built-in skill installer:

```bash
python3 ~/.codex/skills/.system/skill-installer/scripts/install-skill-from-github.py \
  --repo k57597907-netizen/code-to-prd \
  --path skills/code-to-prd \
  --ref main
```

After installation, restart Codex so the new skill metadata is loaded.

If you already have an older local copy, remove it first:

```bash
rm -rf ~/.codex/skills/code-to-prd
```

Then run the install command again.

## Use In Codex

Example prompts:

```text
使用 code-to-prd 分析这个项目，生成 PRD。
```

```text
使用 code-to-prd 拆解这个 GitHub 仓库，并输出中文 PRD：https://github.com/example/app
```

```text
使用 code-to-prd 分析 /path/to/project，生成 prd/ 目录，包含 README、页面文档、API inventory、枚举字典和页面关系图。
```

For Chinese requests, the skill is configured to write the PRD in Chinese while preserving route paths, API paths, enum keys, file names, and code identifiers exactly.

## Direct Script Usage

The skill includes two stdlib-only Python scripts. From inside `skills/code-to-prd`:

```bash
python3 scripts/codebase_analyzer.py /path/to/project -o analysis.json
python3 scripts/codebase_analyzer.py /path/to/project -f markdown
python3 scripts/prd_scaffolder.py analysis.json -o prd/ -n "My App"
```

Recommended workflow:

1. Run `codebase_analyzer.py` to build the route/API/model/enum map.
2. Review the generated analysis summary.
3. Run `prd_scaffolder.py` to create a PRD skeleton.
4. Use Codex with this skill to fill in detailed page, endpoint, interaction, and business-rule documentation.

## Output

By default, generated product documentation should be placed under the target project's `prd/` directory:

```text
prd/
├── README.md
├── pages/
│   └── ...
└── appendix/
    ├── api-inventory.md
    ├── enum-dictionary.md
    └── page-relationships.md
```

## Attribution

This repository is based on the MIT-licensed `code-to-prd` skill from [alirezarezvani/claude-skills](https://github.com/alirezarezvani/claude-skills/tree/main/product-team/code-to-prd). See [NOTICE.md](./NOTICE.md) for details.
