---
description:  untrusted bug issue.

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
    lockdown: false
    min-integrity: none

safe-outputs:
  staged: false
  threat-detection: false

  mentions: false
  allowed-github-references: []

  create-issue:
    title-prefix: "[bug-summary] "
    labels: [bug-summary]
    close-older-issues: false
---

# Bug summary

Read the latest issue labelled `bug`.

Create exactly one new issue containing a concise and accurate summary of the
original bug report. Include its key technical points and recommended developer
tasks. Do not perform any operation other than creating this summary issue.