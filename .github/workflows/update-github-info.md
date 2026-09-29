---
name: update-github-info
description: Keep the GitHub Info site current with practical updates from official GitHub sources.
on:
  schedule: daily
  workflow_dispatch:
permissions:
  contents: read
engine:
  id: copilot
  model: copilot/auto
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
    - awesome-copilot.github.com
safe-outputs:
  create-pull-request:
    base-branch: main
    draft: true
    fallback-as-issue: false
---

# Update GitHub Info

Read `notes/mona-notes.md` and the current `site/content/github-info.md` before making changes.

Fetch and review both official sources:

- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` with concise, practical GitHub guidance that fits Mona's editorial angle. Prioritize useful updates for developers, preserve relevant existing material, and avoid duplicating content already on the page. Clearly cite the GitHub Blog or Changelog source for every new announcement or claim. Do not add unsupported claims or unrelated content.

If there are meaningful updates, propose the changes in one draft pull request targeting `main` for Mona to review. Describe the updates and link their sources in the pull request body. Do not commit or push changes directly to `main`. If there are no meaningful updates, leave the page unchanged and do not open an empty pull request.
