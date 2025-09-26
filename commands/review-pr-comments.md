---
allowed-tools: Bash(gh pr:*), Bash(gh api:*), Bash(git checkout:*), Bash(git pull:*), Read, Edit, MultiEdit, Write
description: Review and apply Claude's PR feedback interactively
argument-hint: "PR number (e.g., '123')"
---

# GitHub PR Workflow for PR #$ARGUMENT$

## Primary Task
Retrieve the latest Claude review comment from the specified pull request and initiate an interactive conversation to help me decide which feedback items to apply.

## Step-by-Step Instructions

### 1. Get PR Review Information
- Fetch the latest Claude review comment from the specified PR
- Parse and organize the feedback items clearly
- Identify the scope and nature of each suggestion

### 2. Get last changes and move to branch
- Go to main branch and fetch the latest changes.

```bash
git checkout main
git pull --rebase
```

- Checkout to the pull request branch.

```bash
git checkout PULL_REQUEST_BRANCH_NAME
```

### 3. Present Feedback Summary
Display the review feedback in a structured format:
- **Critical Issues**: Security, bugs, or breaking changes
- **Code Quality**: Performance, maintainability, best practices
- **Style/Convention**: Formatting, naming, documentation
- **Suggestions**: Nice-to-have improvements or alternatives

### 4. Interactive Discussion Framework
For each feedback item, ask me:
- Do you agree with this feedback? (Yes/No/Partially)
- What's your reasoning for applying or not applying it?
- Are there any constraints or context I should consider?
- Would you like me to help implement this change?

### 5. Decision Tracking
Keep track of:
- ✅ Feedback to implement
- ❌ Feedback to skip (with reasoning)
- ⚠️ Feedback that needs clarification
- 🔄 Feedback requiring further discussion

### 6. Implementation Planning
For accepted feedback:
- Prioritize changes by impact and effort
- Identify dependencies between changes
- Suggest implementation order
- Offer to help with code modifications

### 7. Document Decisions in PR
Write a summary comment in the PR that includes:
- Overview of review feedback received
- Decision rationale for each feedback item
- List of changes that will be implemented
- List of feedback items declined (with reasons)
- Timeline or next steps for implementation

## GitHub CLI Commands Reference

### Viewing PR Reviews
```bash
# List all reviews for a PR
gh pr review list $ARGUMENT$

# View specific review details
gh pr view $ARGUMENT$ --comments

# Get PR review comments in JSON format
gh api repos/:owner/:repo/pulls/[PR_NUMBER]/reviews
```

### Commenting on PRs
```bash
# Add a general comment to PR
gh pr comment $ARGUMENT$ --body "Your comment text"

# Add a comment from a file
gh pr comment $ARGUMENT$ --body-file comment.md

# Reply to a specific review thread
gh api repos/:owner/:repo/pulls/[PR_NUMBER]/reviews/[REVIEW_ID]/replies \
  --method POST \
  --field body="Reply text"
```

### Getting PR Information
```bash
# View PR details
gh pr view $ARGUMENT$

# Get PR status and checks
gh pr status

# List all PRs
gh pr list

# Get PR diff
gh pr diff $ARGUMENT$
```

### Additional Considerations
- Consider the PR's context (feature branch, hotfix, etc.)
- Respect team conventions and existing patterns
- Balance code quality with practical constraints

## Expected Workflow
1. Fetch and analyze the Claude review
2. Present organized feedback summary
3. Discuss each item interactively
4. Create action plan for accepted changes
5. Offer implementation assistance
6. Write summary comment in PR documenting all decisions
7. Update PR based on decisions
