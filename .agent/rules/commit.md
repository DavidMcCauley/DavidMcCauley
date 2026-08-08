---
trigger: always_on
---

# Redleaf Studio Enterprise Git Commit Rule

Always generate Git commit messages adhering to Conventional Commits and the 50/72 rule.

## Structure

```
<type>(<scope>): <imperative summary, 50 characters or fewer>

<optional body wrapped at 72 characters>

<optional footer(s)>
```

## Rules & Standards

### Header Rules
1. **Conventional Prefix**: Start with a valid Conventional Commit type:
   - `feat`: A new feature
   - `fix`: A bug fix
   - `docs`: Documentation only changes
   - `style`: Formatting, missing semi-colons, etc (no code change)
   - `refactor`: Code change that neither fixes a bug nor adds a feature
   - `perf`: Code change that improves performance
   - `test`: Adding or correcting tests
   - `build`: Changes affecting build system or external dependencies
   - `ci`: Changes to CI configuration scripts and workflows
   - `chore`: Other changes that don't modify src or test files
2. **Scope**: Include an optional component/module scope in parentheses, e.g., `fix(auth):` or `feat(rates):`.
3. **Length**: The header must be 50 characters or fewer whenever possible, and must NEVER exceed 72 characters.
4. **Imperative Mood**: Use imperative, present tense verbs (e.g., "add", "fix", "change", NOT "added", "fixes", "changing").
5. **No Trailing Period**: Do not place a period at the end of the header line.
6. **Separation**: A blank line MUST separate the header from the body.

### Body Rules
7. **Character Wrap**: Wrap body lines at 72 characters.
8. **What & Why**: Explain *what* changed and *why* (motivation, context, risk, behavior changes). Avoid raw low-level implementation details unless necessary.
9. **When to Include**: Include a body for non-obvious motivations, behavioral modifications, migration steps, or security implications. Omit for simple self-explanatory changes.
10. **Issue / Project References**: Reference relevant GitHub issues or board cards when applicable (e.g., `Closes #123`, `Fixes #456`, `Ref #789`).

### Enterprise Safeguards & Multi-Agent Rules
11. **Anti-Polling Compliance**: Never inline GitHub API polling patterns (e.g., `gh pr checks` in loops) in commit messages or PR descriptions. Put large text payloads in files and reference them via `--body-file`.
12. **Fleet-Only Testing**: Reference fleet runner verification (`notify-poll wait-ci`) for test results. Do not run heavy local test suites.
13. **Python 3.14 Floor**: Ensure all Python code changes conform to Python 3.14+ floor standards across Redleaf Studio services.
14. **Multi-Agent Coordination**: When collaborating on open PRs or issues, include breadcrumbs with head SHA, current status, and next steps to avoid competing PR thrashing.
