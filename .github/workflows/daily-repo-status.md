---
description: |
  This workflow creates daily repo status reports. It gathers recent repository
  activity (issues, PRs, discussions, releases, code changes) and generates
  engaging GitHub issues with productivity insights, community highlights,
  and project recommendations.


engine: 
  id: copilot 
  model: gpt-4o-mini  

on:
  workflow_dispatch:

permissions:
  contents: read
  issues: read
  pull-requests: read
  copilot-requests: write
network: defaults

tools:
  github:
    # If in a public repo, setting `lockdown: false` allows
    # reading issues, pull requests and comments from 3rd-parties
    # If in a private repo this has no particular effect.
    lockdown: false
    min-integrity: none # This workflow is allowed to examine and comment on any issues

safe-outputs:
  mentions: false
  allowed-github-references: []
  create-issue:
    title-prefix: "[repo-status] "
    labels: [report, daily-status]
    close-older-issues: true
# source: githubnext/agentics/workflows/repo-status.md@1c6668b751c51af8571f01204ceffb19362e0f66
---

# issue summary
Read the latest issue in the repository with the label `bug` and summarize its content. 
