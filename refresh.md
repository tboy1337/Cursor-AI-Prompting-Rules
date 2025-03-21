{my query (e.g., "the login button still crashes")}

---

Diagnose and resolve the issue described above with a systematic, validation-driven approach:

1. **Gather Comprehensive Context**:
   - Collect all relevant error messages, logs, and observed behaviors related to the issue.
   - Identify the affected components, files, and their dependencies using tools like `grep_search` for exact matches or `codebase_search` for semantic context.
   - Map the data flow and interactions leading to the issue to pinpoint its scope.

2. **Hypothesize and Investigate**:
   - Propose at least three potential root causes across different layers (e.g., code logic, dependencies, configuration).
   - Use `cat -n <file path>` to review file contents with line numbers and `tree -L 4 --gitignore | cat` to explore directory structure for related resources.
   - Validate each hypothesis by tracing execution paths and checking for inconsistencies or missing dependencies.

3. **Leverage Existing Solutions**:
   - Search the codebase with `codebase_search` for similar issues or patterns already resolved.
   - Identify reusable utilities, error-handling mechanisms, or abstractions that could address the problem.
   - Ensure consistency with existing conventions by cross-referencing current implementations.

4. **Analyze with Precision**:
   - Trace all dependencies (e.g., imports, function calls, APIs) impacted by the issue.
   - Assess whether the issue reflects a deeper design flaw or a localized bug.
   - Evaluate potential performance or maintainability impacts of both the issue and proposed fixes.

5. **Resolve Strategically**:
   - Propose targeted solutions with specific file paths and line numbers for changes.
   - Balance immediate resolution with improvements to code structure or reusability.
   - Explain the reasoning behind each fix, focusing on stability and alignment with system design.

6. **Validate Thoroughly**:
   - Define test scenarios, including edge cases, to confirm the issue is resolved.
   - Suggest validation methods (e.g., unit tests, manual checks) appropriate to the project.
   - Recommend monitoring or logging to ensure the fix holds over time and prevents regressions.

This approach ensures a methodical resolution that strengthens the codebase while addressing the issue effectively.