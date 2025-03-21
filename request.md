{my request (e.g., "add a save button")}

---

Design and implement the request described above with a systematic, validation-driven approach:

1. **Understand the System Context**:
   - Analyze the current codebase structure using `tree -L 4 --gitignore | cat` to identify where the feature fits.
   - Review existing patterns, conventions, and domain models with `codebase_search` to ensure alignment.
   - Map out integration points and affected components based on the request’s scope.

2. **Define Clear Requirements**:
   - Break the request into specific, testable requirements with acceptance criteria.
   - Identify use cases, constraints, and non-functional needs (e.g., performance, security).
   - Establish boundaries to keep the implementation focused and maintainable.

3. **Explore Reusability**:
   - Use `codebase_search` to find existing components or utilities that can be adapted for this feature.
   - Check for similar implementations with `grep_search` to maintain consistency across the codebase.
   - Plan for potential abstraction if the feature could be reused elsewhere.

4. **Plan the Implementation**:
   - Identify all files and dependencies requiring changes, specifying relative paths from the workspace root.
   - Assess cross-cutting concerns (e.g., logging, error handling) and integration needs.
   - Evaluate impacts on performance, testing, and documentation, planning accordingly.

5. **Execute with Structure**:
   - Propose a step-by-step implementation that preserves system stability at each stage.
   - Provide detailed code changes with before/after examples, adhering to project conventions.
   - Highlight opportunities to enhance code organization or separation of concerns.

6. **Ensure Quality and Stability**:
   - Define comprehensive test scenarios (unit, integration, end-to-end) to validate the feature.
   - Suggest validation methods and monitoring metrics to confirm successful deployment.
   - Include contingency plans (e.g., rollback steps) to mitigate risks during integration.

This approach delivers a well-integrated feature that enhances the codebase’s design and reliability.