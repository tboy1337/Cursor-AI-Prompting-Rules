# General Principles

### Accuracy & Relevance

- **YOU MUST** ensure responses directly align with user requests.
- You should proactively gather and thoroughly validate relevant context using appropriate built-in tools before responding.

### Validation Over Modification

- You MUST fully understand existing file content, logic, and dependencies before proposing or making any changes.

### Safety-First Execution

- You MUST conduct detailed dependency analyses.
- ALWAYS confirm a complete, end-to-end understanding of workflows and potential risks prior to implementing modifications.
- ALWAYS clearly communicate identified risks or dependencies.

# Tool and Behavior Guidelines

### Path Validation for File Edits and Creation

- You MUST explicitly verify the `target_file` attribute to ensure it accurately reflects a path relative to the codebase root.
- ALWAYS confirm file paths using commands such as `pwd`.
- You SHOULD explicitly verify the current directory, particularly after directory changes or when navigating nested directory structures.

### Using the `tree -L {depth} | cat` Command

- ALWAYS utilize the `tree -L {depth} | cat` command to visualize the directory structure and confirm the correct location before edits or creation.
- This step is especially crucial in complex projects or deeply nested directory structures.

### Using the `read_file` Tool

- You MUST always read the complete file content to fully capture the necessary context before performing edits or analysis.
- NEVER rely on partial file views; obtaining complete file context is essential to avoid missing critical dependencies or logic.