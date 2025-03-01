{my query (e.g. it is still showing an error)}

---

Diagnose and resolve the current issue with the mindset of a senior architect/engineer, following a structured, rigorous, and holistic approach:

1. **Understand the Architecture First**:
   - **Objective:** Establish a clear mental model of the system before diagnosing the issue.
   - **Actions:**
     - Identify the application's architectural patterns (e.g., MVC, microservices, layered) and key abstractions (e.g., services, repositories, DTOs).
     - Map the component hierarchy and data flow relevant to the issue, using a concise diagram or description if complex.
     - Assess whether the issue indicates an architectural misalignment (e.g., tight coupling, violated boundaries).
     - Determine how the solution should integrate with the existing architecture to maintain consistency.
   - **Output:** A brief summary of the relevant architecture and its relation to the issue.

2. **Assess the Issue Holistically**:
   - **Objective:** Capture the full scope of the problem across system layers.
   - **Actions:**
     - Collect all available error messages, logs, stack traces, and observed behavioral symptoms from the user’s input or system outputs.
     - Hypothesize at least 3 potential root causes, spanning different layers (e.g., UI, business logic, data access, infrastructure).
     - Evaluate whether the issue reflects a deeper design flaw (e.g., lack of error propagation, brittle dependencies) rather than a surface-level bug.
   - **Output:** A list of symptoms and 3+ prioritized root cause hypotheses with their system-layer context.

3. **Discover Reusable Solutions**:
   - **Objective:** Leverage existing patterns to ensure consistency and efficiency.
   - **Actions:**
     - Search the codebase for similar issues and their resolutions, identifying reusable patterns or fixes.
     - Review existing utilities, helpers, or abstractions (e.g., logging frameworks, validation libraries) that could address the issue.
     - Check if common patterns (e.g., error handling, input validation, retry logic) are consistently applied across the codebase.
     - Identify opportunities to extract reusable components or utilities from the proposed fix.
   - **Output:** A summary of applicable existing solutions and potential reusable abstractions.

4. **Analyze with Engineering Rigor**:
   - **Objective:** Ensure the diagnosis and solution adhere to high engineering standards.
   - **Actions:**
     - Trace dependencies and interactions between affected components, noting any unexpected side effects.
     - Verify separation of concerns, single responsibility principle, and adherence to project conventions (e.g., naming, structure).
     - Assess performance implications of the issue and potential fixes (e.g., latency, resource usage).
     - Evaluate maintainability (e.g., readability, modularity) and testability (e.g., ease of unit testing) of the solution.
   - **Output:** A detailed analysis of dependencies, adherence to principles, and performance/maintainability impacts.

5. **Propose Strategic Solutions**:
   - **Objective:** Deliver actionable, architecturally sound resolutions.
   - **Actions:**
     - Propose 1-2 solutions that align with the existing architecture, prioritizing simplicity and long-term value.
     - Specify exact file paths, line numbers, and code changes (or pseudocode if files are unknown) for each solution.
     - Highlight refactoring opportunities to improve code organization (e.g., extract methods, consolidate logic).
     - Explain the engineering principles (e.g., DRY, SOLID, loose coupling) behind each solution.
     - Balance immediate fixes with architectural improvements, justifying trade-offs if necessary.
   - **Output:** A detailed plan with solutions, file changes, principles, and trade-off reasoning.

6. **Validate Like a Professional**:
   - **Objective:** Ensure the solution is robust, verified, and future-proof.
   - **Actions:**
     - Define 3+ test scenarios, including edge cases, to validate the fix (e.g., null inputs, high load, failure states).
     - Specify validation methods tailored to the project’s stack (e.g., unit tests with Jest, integration tests with Postman).
     - Suggest monitoring approaches (e.g., logging, metrics, alerts) to confirm the solution’s effectiveness in production.
     - Identify potential regressions and mitigation strategies (e.g., guard clauses, fallback logic).
   - **Output:** A validation plan with test scenarios, methods, monitoring suggestions, and regression prevention.

**Execution Guidelines:**
- Approach each step sequentially, ensuring clarity and completeness before proceeding.
- If critical information (e.g., logs, file paths) is missing, explicitly request it from the user with specific examples of what’s needed.
- Present findings and proposals in a structured format (e.g., numbered lists, code blocks) for readability.
- Ensure solutions not only resolve the immediate issue but also enhance the codebase’s architecture, maintainability, and scalability.

---