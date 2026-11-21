---
name: update-github-info
description: Propose practical, sourced updates to the GitHub Info page.
intent: Keep the GitHub Info page useful and current with concise, source-backed guidance from official GitHub updates, reviewed by Mona before publication.
strict: true
on:
  schedule: daily
  workflow_dispatch:
  skip-if-match: 'is:pr is:open in:title "[GitHub Info]"'
permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
checkout:
  ref: main
engine:
  id: copilot
  copilot-sdk: true
network:
  allowed:
    - github.blog
    - github.com
tools:
  bash: false
  cli-proxy: false
  edit: true
  web-fetch:
safe-outputs:
  create-pull-request:
    title-prefix: "[GitHub Info] "
    branch-prefix: "github-info/"
    base-branch: main
    draft: true
    max: 1
    max-patch-files: 1
    allowed-files:
      - site/content/github-info.md
---

# Update GitHub Info

Keep `site/content/github-info.md` useful for developers and consistent with
Mona's editorial direction.

1. Read `notes/mona-notes.md` and the current `site/content/github-info.md`.
2. Use web-fetch to read both:
   - https://github.blog/latest/
   - https://github.blog/changelog/
3. Select up to three recent, verifiable updates that are useful to developers
   and relevant to the page. Prefer items not already covered. Do not invent
   details; include a concise practical summary, the publication date when
   available, and a direct link to the official source for every selected item.
4. Make the smallest useful edit to `site/content/github-info.md`, preserving
   its existing format, voice, and useful content. Do not edit any other file.
5. Review the resulting change. If it contains a meaningful update, open one
   draft pull request for Mona to review. Use a concise title and a body that
   summarizes the change and links to the sources.
6. Use `noop` with a brief reason if neither source has a useful new update,
   the sources cannot be verified, the page needs no meaningful change, or
   there is otherwise no safe proposal to make.

Only propose content changes through the configured create-pull-request
safe output. Never write directly to `main` or use another mechanism to publish
the change.
