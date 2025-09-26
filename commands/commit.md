---
allowed-tools: Bash(git add:*), Bash(git status:*), Bash(git commit:*), Bash(git branch:*), Bash(git diff:*), Bash(git log:*)
description: Create a git commit
---
# Commit Changes

You are tasked with creating git commits for the changes made during this session.

## Process:

1. **Think about what changed:**
   - Review the conversation history and understand what was accomplished
   - Run `git status` to see current changes
   - Run `git diff` to understand the modifications
   - Consider whether changes should be one commit or multiple logical commits

2. **Plan your commit(s):**
   - Identify which files belong together
   - Draft clear, descriptive commit messages
   - Use imperative mood in commit messages
   - Focus on why the changes were made, not just what

3. **Add changes to the staging area:**
   - Add files that you want to commit to the staging area using: `git add "<file-path>"`. Always use the exact file path with quotes to avoid any errors.
   - Confirm the changes were added to the staging area with `git status`

4. **Create commit with proper format:**
   - Get current branch name: `git branch --show-current`
   - Extract issue number from branch name (first part before the dash, e.g., from `123-user-dashboard` get `123`)
   - Format: `#{issue-number} {descriptive-message}`
   - Create a descriptive and extensive commit message based on the git diff changes
   - The `#` prefix will create a reference link to the GitHub issue
   - Examples: 
     - `#123 Add comprehensive user dashboard component with profile management and settings`
     - `#45 Fix media upload validation to handle multiple file types and size limits`
   - NEVER add "Generated with Claude Code" or similar AI attribution

5. **Execute commit:**
   - Create the commit using: `git commit -m "FORMATTED_MESSAGE"`
   - Confirm the commit was successful with `git status`

6. **Repeat steps 3-5 for each change:**
   - If changes should be committed separately, repeat steps 2-4 for each change.
   - If changes should be committed in the same commit, repeat steps 2-4 for each change.
   - Confirm there are no changes left to commit with `git status`
   - If there are no changes, exit with `echo "No changes to commit"`

## Important:
- **NEVER add co-author information or Claude attribution**
- Always follow the exact format: `#{issue-number} {descriptive-message}`
- Message should be descriptive and extensive, explaining what was changed and why
- Commits should be authored solely by the user
- Do not include any "Generated with Claude" messages
- Do not add "Co-Authored-By" lines
- Write commit messages as if the user wrote them

## Remember:
- You have the full context of what was done in this session
- Group related changes together
- Keep commits focused and atomic when possible
- The user trusts your judgment - they asked you to commit
