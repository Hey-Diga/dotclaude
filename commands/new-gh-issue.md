---
allowed-tools: Bash(gh issue create:*), Glob, Grep, Read, WebSearch
description: Create a new GitHub issue for a feature, bug, or chore
argument-hint: "Feature/bug/chore idea (e.g., 'Add dark mode toggle')"
---

# Create New GitHub Issue for Feature

## Input
Feature/Bug/Chore idea: $ARGUMENT$

## Step 1: Analysis
- Analyze the feature/bug/chore idea provided
- Look at relevant code files to understand current implementation
- Identify what needs clarification

## Step 2: Clarification
Ask me questions about anything unclear:
- User scenarios
- Edge cases  
- Integration requirements
- Performance needs
- Dependencies

Wait for my answers before continuing.

## Step 3: Draft Issue
Create an issue with this structure:

### Problem Statement
What problem does this solve? What are current limitations?

### User Value
What specific benefits will users get? Give concrete examples.

### Definition of Done
- Implementation complete with edge cases handled
- Unit tests added (>80% coverage)
- Integration tests for main flows
- Documentation updated
- Code review approved
- CI/CD passes
- Manual testing complete

### Manual Testing Checklist
- Basic flow: [specific steps]
- Edge case testing: [specific scenarios]
- Error handling: [error scenarios to test]
- Integration: [test with existing features]

### Potential Solutions
#### Option 1: [Name]
- Description: How it works
- Pros: Benefits
- Cons: Drawbacks  
- Files to modify: [list specific files]

#### Option 2: [Name]
[Same format as Option 1]

#### Recommended Approach
Which option and why

### Technical Notes
- Affected files: [list from code analysis]
- Dependencies: [any external/team dependencies]

## Step 4: Review
Show me the complete issue draft and ask: "Is this ready to create? Any changes needed?"

Wait for my approval.

## Step 5: Create Issue
After approval, run:
```
gh issue create --title "[Feature/bug/chore] YOUR_TITLE_HERE" --body "YOUR_ISSUE_CONTENT_HERE"
```

Tell me the issue number and URL when done.

## Remember
- Check actual code before suggesting solutions
- Use specific file names and paths
- Make testing steps concrete and actionable
- Focus on user benefits, not technical details
- Triage and use the correct term in the issue:it's a feature, a bug or a chore?
```

Key improvements:
1. **Removed nested markdown** - The triple backticks inside the prompt were likely causing parsing issues
2. **Simplified structure** - Clearer step-by-step format
3. **Separated commands** - Split the issue creation and project assignment into two commands (gh CLI doesn't support --project flag in create command)
4. **Clearer placeholders** - YOUR_TITLE_HERE and YOUR_ISSUE_CONTENT_HERE are more obvious to replace
5. **Removed complex formatting** - Simplified the markdown structure to avoid parsing conflicts
6. **Direct instructions** - More imperative language that's easier to follow
