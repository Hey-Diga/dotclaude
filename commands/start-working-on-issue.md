---
allowed-tools: Bash(gh issue:*), Bash(gh pr create:*), Bash(git:*), Bash(npm test:*), Bash(npm run lint:*), Read, Edit, MultiEdit, Write, Glob, Grep
description: Start working on a GitHub issue
argument-hint: "Issue number (e.g., '197')"
---

# GitHub Issue Workflow for Issue #$ARGUMENT$

## Setup Phase
1. Fetch latest branches: `git fetch origin`
2. Get issue details 
   - Fetch issue title: `gh issue view $ARGUMENT$ --json title -q .title`

## Analysis Phase
1. Read the full issue content and ALL comments using: `gh issue view $ARGUMENT$ --comments`
2. Analyze the requirements and context thoroughly
3. If any clarifications are needed:
   - List all questions clearly
   - Ask me for answers
   - Post both questions and answers as a comment on the github issue $ARGUMENT$

## Implementation Phase
1. Execute the plan step by step, remember to build test before the implementation and run the test suite constanly to get quick feedback.
2. Ensure consistency with existing code in the branch
3. Run lint (npm run lint) and tests suite (npm run test) before git commit & push
4. Create the PR

## Important Notes
- Always use `gh` CLI for GitHub operations
- Keep detailed records of all actions as PR/issue comments
- Wait for explicit confirmation before proceeding with major changes
