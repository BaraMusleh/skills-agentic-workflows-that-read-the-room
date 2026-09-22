---
name: update-github-info

on:
  schedule:
    - cron: "0 0 * * *"
  workflow_dispatch:

permissions:
  contents: read

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
    allowed-files:
      - site/content/github-info.md
    draft: false
---

# Update GitHub information

Read `notes/mona-notes.md` for Mona's guidance and existing context.

Use web fetch to read:

- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Update `site/content/github-info.md` with relevant current GitHub information,
following Mona's notes and preserving the existing style and structure.
Include source context when information comes from the GitHub Blog or GitHub
Changelog.

If the sources do not require a meaningful change, call `noop` with a short
reason.Otherwise, use the `create-pull-request` safe output to open a pull request for Mona to review.
The pull request must contain only the update to `site/content/github-info.md`.
Do not write directly to the default branch.