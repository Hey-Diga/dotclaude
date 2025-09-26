---
allowed-tools: Bash(gh pr:*), Bash(git:*), Bash(npm test:*), Bash(npm run lint:*), Bash(npm run typecheck:*), Read, Glob, Grep
description: Create a pull request from the current branch
---

# Create Pull Request

You are tasked with creating a pull request from the current branch.

## Process:

### 1. Pre-flight Checks
- Run `git status` to check for uncommitted changes
- If there are uncommitted changes:
  - Show the uncommitted changes clearly
  - Tell the user: "You have uncommitted changes. Please either:"
    - "1. Exit and run `/commit` to commit your changes first (recommended)"
    - "2. Stash the changes temporarily with `git stash`"
    - "3. Continue anyway if these changes aren't meant for this PR"
  - Wait for user's decision
- Run `git branch --show-current` to get the current branch name
- Verify we're not on main/master branch

### 2. Code Quality Verification
Run the following checks in parallel:
- `npm run lint` - Check for linting issues
- `npm run typecheck` - Check for TypeScript errors
- `npm test` - Run the test suite

If any checks fail:
- Show me the errors
- Ask if I want to fix them before creating the PR
- If yes, help fix the issues and re-run the checks

### 3. Analyze Changes
- Run `git log origin/main..HEAD --oneline` to see commits that will be in the PR
- Run `git diff origin/main...HEAD --stat` to see changed files summary
- Run `git diff origin/main...HEAD` to understand the full changes
- Identify the type of changes (feature, bugfix, refactor, chore, etc.)

### 4. Extract Context
- If branch name contains an issue number (e.g., "123-feature-name"), extract it
- Look for related issue by checking recent commits for issue references
- Understand the purpose and scope of the changes

### 5. Draft PR Description
Create a comprehensive PR description with:

```markdown
## Summary
[2-3 bullet points describing what this PR does]

## Related Issue
Closes #[issue-number] (if applicable)

## Changes Made
- [Detailed list of changes]
- [Include technical decisions if relevant]
- [Mention any breaking changes]

## Testing
- [ ] Unit tests pass
- [ ] Integration tests pass
- [ ] Manual testing completed
- [ ] Linting and type checking pass

## Screenshots
[If UI changes, include before/after screenshots]

## Checklist
- [ ] Code follows project style guidelines
- [ ] Self-review completed
- [ ] Tests added/updated for changes
- [ ] Documentation updated if needed
- [ ] No console.log or debug code left
- [ ] Translations added for new text (if applicable)
```

### 6. Review with User
- Show me the draft PR title and description
- Ask: "Does this look good? Any changes needed?"
- Wait for approval or make requested changes

### 7. Push Changes
- Run `git push -u origin HEAD` to push the branch to remote
- This ensures the branch exists on GitHub before creating the PR

### 8. Create the PR
After approval, create the PR using:
```bash
gh pr create \
  --title "[Type] Clear, descriptive title" \
  --body "Full PR description from step 5" \
  --base main
```

### 9. Post-Creation
- Show me the PR URL
- Run `gh pr view --web` to open the PR in browser (optional)
- Suggest next steps:
  - Request reviews from team members
  - Add labels if needed
  - Link to project board if applicable

## Important Notes:
- Always ensure all tests pass before creating PR
- Use conventional commit style for PR titles when possible
- Include issue numbers for automatic linking
- Be thorough in the description - it helps reviewers
- Check for any .env or sensitive data in the diff

## PR Title Format Examples:
- `feat: Add user authentication system`
- `fix: Resolve date parsing issue in calendar`
- `refactor: Improve appointment service performance`
- `chore: Update dependencies to latest versions`
- `docs: Add API documentation for new endpoints`

Remember: A good PR description saves review time and provides context for future reference.