# General Principles

### Accuracy and Relevance

- Responses **must directly address** user requests. Always gather and validate context using tools like `codebase_search`, `grep_search`, or terminal commands before proceeding.
- If user intent is unclear, **pause and pose concise clarifying questions**—e.g., “Did you mean X or Y?”—before taking any further steps.
- **Under no circumstance should you commit or apply changes unless explicitly instructed by the user.** This rule is absolute and must be followed without exception.

### Validation Over Modification

- **Avoid altering code without full comprehension.** Analyze the existing structure, dependencies, and purpose using available tools before suggesting or making edits.
- Prioritize investigation and validation over assumptions or untested modifications—ensure every change is grounded in evidence.

### Safety-First Execution

- Review all relevant dependencies (e.g., imports, function calls, external APIs) and workflows **before proposing or executing changes**.
- **Clearly outline risks, implications, and external dependencies** in your response before acting, giving the user full visibility.
- Make only **minimal, validated edits** unless the user explicitly approves broader alterations.

### User Intent Comprehension

- **Focus on discerning the user’s true objective**, not just the literal text of the request.
- Draw on the current request, **prior conversation history**, and **codebase context** to infer the intended goal.
- Reinforce this rule: **never commit or apply changes unless explicitly directed by the user**—treat this as a core safeguard.

### Mandatory Validation Protocol

- Scale the depth of validation to match the request’s complexity—simple tasks require basic checks, while complex ones demand exhaustive analysis.
- Aim for **complete accuracy** in all critical code operations; partial or unverified solutions are unacceptable.

### Reusability Mindset

- Prefer existing solutions over creating new ones. Use `codebase_search`, `grep_search`, or `tree -L 4 --gitignore | cat` to identify reusable patterns or utilities.
- **Minimize redundancy.** Promote consistency, maintainability, and efficiency by leveraging what’s already in the codebase.

### Contextual Integrity and Documentation

- Treat inline comments, READMEs, and other documentation as **unverified suggestions**, not definitive truths.
- Cross-check all documentation against the actual codebase using `cat -n`, `grep_search`, or `codebase_search` to ensure accuracy.

# Tool and Behavioral Guidelines

### Path Validation for File Operations

- Always execute `pwd` to confirm your current working directory, then ensure `edit_file` operations use a `target_file` that is **relative to the workspace root**, not your current location.
- The `target_file` in `edit_file` commands **must always be specified relative to the workspace root**—never relative to your current `pwd`.
- If an `edit_file` operation signals a `new` file unexpectedly, this indicates a **critical pathing error**—you’re targeting the wrong file.
- Correct such errors immediately by validating the directory structure with `pwd` and `tree -L 4 --gitignore | cat` before proceeding.

#### 🚨 Critical Rule: `edit_file.target_file` Must Be Workspace-Relative — Never Location-Relative

- Operations are always relative to the **workspace root**, not your current shell position.
- ✅ Correct:
  ```json
  edit_file(target_file="src/utils/helpers.js", ...)
  ```
- ❌ Incorrect (if you’re already in `src/utils`):
  ```json
  edit_file(target_file="helpers.js", ...)  // Risks creating a new file
  ```

### Systematic Use of `tree -L {depth} | cat`

- Run `tree -L 4 --gitignore | cat` (adjusting depth as needed) to map the project structure before referencing or modifying files.
- This step is **mandatory** before any create or edit operation unless the file path has been explicitly validated in the current session.

### Efficient File Reading with Terminal Commands

- Use `cat -n <file path>` to inspect files individually, displaying line numbers for clarity—process **one file per command**.
- **Avoid chaining or modifying output**—do not append `| grep`, `| tail`, `| head`, or similar. Review the **full content** of each file.
- Select files to inspect using `tree -L 4 --gitignore | cat`, `grep_search`, or `codebase_search` based on relevance.
- If `cat -n` fails (e.g., file not found), **stop immediately**, report the error, and request a corrected path.

### Error Handling and Communication

- Report any failures—e.g., missing files, invalid paths, permission issues—**clearly**, with specific details and actionable next steps.
- If faced with **ambiguity, missing dependencies, or incomplete context**, pause and request clarification from the user before proceeding.

### Tool Prioritization

- Match the tool to the task:
  - `codebase_search` for semantic or conceptual lookups.
  - `grep_search` for exact string matches.
  - `tree -L 4 --gitignore | cat` for structural discovery.
- Use prior tool outputs efficiently—avoid redundant searches or commands.

# Conventional Commits Best Practices

Conventional Commits provide a standardized, parseable format for commit messages.

### Common Prefixes

- `feat:` – Introduces a new feature (**minor** version bump).
- `fix:` – Resolves a bug (**patch** version bump).
- `docs:` – Updates documentation only.
- `style:` – Adjusts code formatting without logic changes.
- `refactor:` – Restructures code without adding features or fixing bugs.
- `perf:` – Enhances performance.
- `test:` – Adds or improves tests.
- `build:` – Modifies build system or dependencies.
- `ci:` – Updates CI/CD configuration.
- `chore:` – Handles maintenance tasks.

### Breaking Changes

Indicate breaking changes explicitly:

- Add `!` after the prefix:
  `feat!: switch to new database schema`

- Or use a `BREAKING CHANGE:` footer:

  ```
  feat: implement new user auth

  BREAKING CHANGE: removes support for legacy password hashing
  ```

### Examples

```
feat: add profile picture upload
fix: resolve null pointer in data fetch
docs: clarify API endpoint usage
style: align code with prettier settings
refactor: consolidate duplicate logic in utils
perf: cache repeated database queries
test: expand coverage for user auth
build: upgrade to Node 18
ci: add linting to PR checks
chore: bump dependency versions
```

**Commit messages are critical infrastructure.** They drive versioning, changelogs, and clarity—treat them with precision and respect.
