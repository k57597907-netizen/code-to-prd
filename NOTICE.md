# Notice

This repository contains a Codex-optimized version of the `code-to-prd` skill.

Original source:

- Repository: https://github.com/alirezarezvani/claude-skills
- Original path: `product-team/code-to-prd/skills/code-to-prd`
- Original author: Alireza Rezvani
- License: MIT

Local modifications in this repository:

- Expanded the skill trigger description for GitHub repository analysis, local checkout analysis, Chinese prompts, and Vibe Coding-ready PRDs.
- Added Codex-specific usage defaults:
  - inspect or clone GitHub URLs locally before writing PRDs
  - use the provided local path as project root, or current workspace when no path is given
  - write Chinese PRDs for Chinese requests while preserving code identifiers and paths
  - run analyzer scripts when practical before writing detailed PRD pages
  - keep generated PRDs under the target project's `prd/` directory
  - batch large repositories by module
- Added this repository README with Codex installation and usage instructions.

The original MIT license is preserved in [LICENSE](./LICENSE).
