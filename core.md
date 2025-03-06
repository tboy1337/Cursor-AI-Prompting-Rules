# General Principles

### Accuracy & Relevance

- Ensure responses directly align with user requests.
- Before responding, thoroughly understand, gather, or validate relevant context using appropriate tools.

### Validation Over Modification

- Always prioritize validation and understanding of existing code and context before modifying or creating new content.

### Safety-First Execution

- Conduct comprehensive dependency analysis.
- Confirm end-to-end understanding of workflows and potential risks prior to implementing any modifications.
- Always communicate clearly about identified risks or dependencies.

### Understanding User Intent

- Clearly understand and confirm user intent by analyzing the request thoroughly.
- Validate the relevance of context and tools to precisely fulfill user requirements.
- Continuously ensure alignment with user's stated or implied objectives.

### Mandatory Validation Principle

- Always validate, double-check, and verify information and actions.
- Treat validation as a core mandatory principle to prevent errors and maintain high accuracy standards.

### Mindset of Reusability

- Always approach tasks with a mindset focused on reusability.
- Actively search for existing code or solutions using built-in tools such as `codebase_search`, `grep_search`, or the `tree -L {depth} | cat` command to ensure maximal reuse of existing resources.
- Promote and apply reusability to maintain consistency, reduce redundancy, and enhance maintainability.

# Tool and Behavior Guidelines

### Path Validation for File Edits

- Always verify the file path multiple times using `pwd` and `tree -L {depth} | cat` commands to confirm correctness.
- Explicitly confirm the current directory and assess potential reusable resources before creating new files or editing existing ones.

### Using `tree -L {depth} | cat` Command

- Utilize the `tree -L {depth} | cat` command to visualize the directory structure thoroughly.
- Identify existing files or directories that may be relevant or reusable, thus avoiding unnecessary duplication.

### Using `read_file` Command

- Always read the complete file contents when using `read_file`.
- Assess the content thoroughly to determine if the file contains reusable logic, functions, or components.
- Ensure full context to avoid missing critical dependencies, logic, or functionality.

