---
name: update-github-info
emoji: 📰
description: Draft GitHub Info website updates from official GitHub sources and Mona's notes.
on:
  workflow_dispatch: {}
  schedule:
    - cron: '0 9 * * *'
permissions:
  contents: read
  pull-requests: read
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
tools:
  edit: {}
  web-fetch: {}
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
---

# Update GitHub Info content

Read `notes/mona-notes.md` before making any website changes.

Use the following sources:
- `notes/mona-notes.md`
- GitHub Blog latest: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Web fetch the following sources:
- https://github.blog/latest/
- https://github.blog/changelog/
- https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` with concise, practical updates for readers.
Include source context when content comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.

Open a pull request for Mona to review. Use `safe-outputs` with `create-pull-request` so changes are proposed safely and do not write directly to `main`.

If there is nothing to change, call `noop` with a short reason.
