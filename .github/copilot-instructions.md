# Project instructions

## Repository purpose

- This repository is an educational GitHub Agentic Workflows exercise for Mona's GitHub Info Astro site.
- Keep changes focused on the exercise, the website, or the agentic-workflow setup.
- Preserve the review-first workflow: generated website changes and workflow changes should use pull requests rather than write directly to protected branches.

## Project layout

- Run the Astro application from `site/`.
- Put reusable page layout in `site/src/layouts/`; keep the homepage in `site/src/pages/index.astro`.
- Put shared CSS in `site/src/styles/global.css`.
- Keep website data and editorial content in `site/content/github-info.md`.
- Keep Mona's editorial rules in `notes/mona-notes.md`.
- Use `site/assets/` for image assets.
- Keep exercise instructions and support images in `.github/steps/` and `.github/images/`.
- VS Code launch and task configuration is in `.vscode/`.

## Astro development

- Use the existing npm scripts and package lock; do not replace npm or manually add dependencies.
- Install dependencies with `cd site && npm ci`.
- Start local development with `cd site && npm run dev -- --host 0.0.0.0 --port 4321`.
- Build the site with `cd site && npm run build`.
- Preview the built site with `cd site && npm run preview -- --host 0.0.0.0 --port 4321`.
- Use Node.js 22 or newer, matching `site/package.json`.
- Validate content and UI changes with the Astro build and inspect the homepage over HTTP when port 4321 is available.

## Website conventions

- Follow the existing bright, approachable Mona/GitHub visual style and reuse components and CSS patterns already in `BaseLayout.astro`, `index.astro`, and `global.css`.
- Keep summaries concise and practical.
- Preserve official source attribution for GitHub Blog and GitHub Changelog content.
- Keep external links official and add `target="_blank"` with `rel="noreferrer"` for off-site links.
- Keep Markdown content compatible with the existing section and `Source:` parsing in `site/src/pages/index.astro`.
- Do not add or expose secrets in source files, prompts, comments, pull requests, or logs.

## Agentic workflow conventions

- Author agentic workflows as Markdown under `.github/workflows/` (for example, `update-github-info.md`).
- Compile Markdown workflows with `gh aw compile <workflow>.md`; keep the generated `<workflow>.lock.yml` alongside it and commit both files.
- Do not compile a workflow while only authoring or editing its Markdown, unless the task explicitly asks for compilation.
- Preserve `workflow_dispatch` and scheduled triggers when extending existing workflows.
- Preserve a restricted `network.allowed` list and add domains only when the workflow's task requires them.
- Preserve `safe-outputs` review controls, especially `create-pull-request`, and never bypass the pull-request review flow.
- Before changing a workflow, inspect existing frontmatter, tools, network policy, engine configuration, and safe-outputs.
- After editing a workflow, validate it with `gh aw compile <workflow>.md` when compilation is required, and inspect both the Markdown and generated lock file.
- Do not write real credentials or tokens into workflow files or documentation.

## GitHub Actions conventions

- Keep exercise workflows under `.github/workflows/`.
- Reuse existing workflow names and permissions patterns instead of expanding permissions without a clear requirement.
- Use GitHub Actions secrets through the repository Actions UI or encrypted secret interfaces, never through committed files or prompts.
- Avoid broad or name-based process termination; use exact PIDs when managing local server processes.

## Change discipline

- Inspect nearby files and existing patterns before editing.
- Make focused changes and leave generated build output and dependencies ignored unless a task explicitly requires them.
- Do not modify `.github/steps/` or exercise grading workflows unless the task directly concerns them.
- Run the smallest relevant validation: the Astro build for site changes and workflow compilation for agentic-workflow changes.
- Report which validation ran and any environment or tooling limitation if verification could not be completed.
