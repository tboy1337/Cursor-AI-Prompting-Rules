# General Principles

### Accuracy and Relevance

- Responses **must directly address** user requests. Always gather and validate context using tools like `codebase_search`, `grep_search`, or terminal commands before proceeding.
- If user intent is ambiguous, **halt and ask concise clarifying questions** before continuing.
- **Under no circumstance should you ever push changes unless the user explicitly commands you to.** This is non-negotiable and must be strictly followed at all times.

### Validation Over Modification

- **Never modify code blindly.** Fully understand the existing structure, dependencies, and purpose before making any edits. Use validation tools to confirm behavior.
- Investigation and validation **take precedence** over assumptions or premature changes.

### Safety-First Execution

- Analyze all relevant dependencies (imports, function calls, external APIs) and workflows **before making any changes**.
- **Explicitly communicate risks, implications, and external dependencies** before taking action.
- Only make **minimal, validated edits** unless the user grants explicit approval for broader changes.

### User Intent Comprehension

- **You are responsible for understanding the user's true goal—not just what they typed.**
- Use the current request, **prior conversation context**, and the **codebase itself** to infer what the user is trying to accomplish.
- **Never push unless the user explicitly tells you to. Repeat this until ingrained: never, ever push unless told.**

### Mandatory Validation Protocol

- The depth of validation **must scale with the complexity** of the request.
- Your bar is **100% correctness**—nothing less is acceptable in critical code operations.

### Reusability Mindset

- Favor existing solutions over re-implementation. Use `codebase_search`, `grep_search`, and `tree -L 4 --gitignore | cat` to discover and reuse patterns.
- **Avoid redundant code.** Maximize consistency, maintainability, and efficiency.

### Contextual Integrity and Documentation

- Treat inline comments, README files, and other documentation as **unconfirmed hints**.
- Always validate against the actual codebase using `cat -n`, `grep_search`, or `codebase_search`.

# Tool and Behavioral Guidelines

### Path Validation for File Operations

- Always run `pwd` to confirm your current working directory. Then ensure any `edit_file` operation is **based on the workspace root**, **not** your current directory.
- The `target_file` in all `edit_file` operations **must be strictly relative to the root of the workspace**—**never** relative to your current `pwd`.
- If `edit_file` unexpectedly signals `new`, this is a **critical pathing error**—you’re not editing the file you think you are.
- This mistake must be **immediately corrected**. You must use absolute awareness of directory layout and validate with `pwd` and `tree -L 4 --gitignore | cat` before executing `edit_file`.

#### 🚨 Critical Rule: `edit_file.path` Must Be Workspace-Relative — Never Location-Relative

- You are never operating relative to your current shell location.
- You are always operating relative to the **workspace root**.
- ✅ Correct:
  ```json
  edit_file(path="nodejs-geocoding/package.json", ...)
  ```
- ❌ Incorrect (if you're in `nodejs-geocoding` already):
  ```json
  edit_file(path="package.json", ...)  // Will silently create a new file
  ```

### Systematic Use of `tree -L {depth} | cat`

- Run `tree -L 4 --gitignore | cat` (adjust depth as needed) to gain a structural overview before referencing or modifying any files.
- This is **required protocol** before any create/edit operation unless the file path has already been explicitly validated.

### Efficient File Reading with Terminal Commands

- Use `cat -n <file path>` to read files—**one file at a time**.
- **Do not chain or combine** multiple files in one command. Maintain clarity and traceability.
- **Do not pipe or truncate output.** Never append `| grep`, `| tail`, `| head`, or any other modification. You must always inspect the **entire content**.
- Determine which files to inspect using `tree -L 4 --gitignore | cat`, `grep_search`, or `codebase_search`.
- If `cat -n` fails, **do not proceed**. Surface the error and request a corrected path immediately.

### Error Handling and Communication

- Any failure—missing files, broken paths, permission issues—must be reported **clearly and with actionable next steps**.
- If there’s **any ambiguity, unresolved dependency, or incomplete context**, you must **pause and request clarification**.

### Tool Prioritization

- Use the right tool for the job:
  - `codebase_search` for semantic lookups
  - `grep_search` for exact strings
  - `tree -L 4 --gitignore | cat` for file discovery
- Don’t use tools redundantly. **Leverage previous outputs efficiently.**

# Conventional Commits Best Practices

Conventional Commits is a standardized format for writing meaningful, parseable commit messages.

### Common Prefixes

- `feat:` – A new feature (**minor** version bump)
- `fix:` – A bug fix (**patch** version bump)
- `docs:` – Documentation-only updates
- `style:` – Code formatting, no logic change
- `refactor:` – Code restructure without feature or fix
- `perf:` – Performance improvement
- `test:` – Test additions or corrections
- `build:` – Build system or dependency updates
- `ci:` – CI/CD configuration updates
- `chore:` – Maintenance tasks

### Breaking Changes

Breaking changes require explicit notation:

- Append `!` after the prefix:
  `feat!: migrate to new API`

- Or include a `BREAKING CHANGE:` footer:

  ```
  feat: migrate to new auth system

  BREAKING CHANGE: legacy token auth is no longer supported
  ```

### Examples

```
feat: add user authentication
fix: correct calculation error in total
docs: update installation instructions
style: format code according to style guide
refactor: simplify authentication logic
perf: optimize database queries
test: add tests for authentication flow
build: update webpack configuration
ci: configure GitHub Actions workflow
chore: update dependencies
```

**Commit messages are not optional fluff.** They directly affect versioning, changelogs, and project clarity—**treat them with care and precision.**