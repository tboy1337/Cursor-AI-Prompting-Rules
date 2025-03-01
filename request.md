{my request (e.g. Develop feature xyz)}

---

Approach this request with the strategic mindset of a solution architect and senior engineer, ensuring a robust, scalable, and maintainable implementation:

1. **Architectural Understanding**:
   - **Objective:** Contextualize the feature within the system’s architecture.
   - **Actions:**
     - Map the current architecture patterns (e.g., microservices, monolithic, event-driven) and conventions (e.g., RESTful APIs, hexagonal design).
     - Identify domain models (e.g., entities, aggregates), abstractions (e.g., services, repositories), and organizational principles (e.g., package structure).
     - Determine the feature’s natural integration point (e.g., new endpoint, service layer extension) based on the architecture.
     - Assess alignment with the system’s design philosophy (e.g., simplicity, modularity, scalability).
   - **Output:** A concise overview of the relevant architecture and the feature’s intended placement.

2. **Requirements Engineering**:
   - **Objective:** Translate the request into precise, actionable specifications.
   - **Actions:**
     - Convert the request into 3-5 clear requirements with measurable acceptance criteria (e.g., “User can view X when Y occurs”).
     - Identify stakeholders (e.g., end-users, admins) and 2-3 key use cases for the feature.
     - Define technical constraints (e.g., framework version, latency limits) and non-functional requirements (e.g., security, scalability).
     - Establish boundaries to protect architectural integrity (e.g., no direct DB access from UI layer).
   - **Output:** A requirements list with acceptance criteria, use cases, constraints, and boundaries.

3. **Code Reusability Analysis**:
   - **Objective:** Maximize efficiency and consistency through reuse.
   - **Actions:**
     - Search the codebase for existing components (e.g., helpers, services) or patterns addressing similar needs.
     - Identify opportunities to create reusable abstractions (e.g., generic utilities, shared interfaces) during implementation.
     - Assess whether the feature warrants a reusable module (e.g., a library or plugin) for future use.
     - Review similar implementations for consistency in approach (e.g., error handling, data transformation).
   - **Output:** A summary of reusable components, abstraction opportunities, and consistency findings.

4. **Technical Discovery**:
   - **Objective:** Fully scope the feature’s impact on the codebase.
   - **Actions:**
     - Map affected codebase areas with exact file paths (e.g., `src/services/user.js`) and dependencies.
     - Analyze cross-cutting concerns (e.g., authentication, logging, caching) and their integration with the feature.
     - Evaluate integration points (e.g., new API endpoints, message queues) and API boundaries (e.g., input/output contracts).
     - Assess system behavior impacts (e.g., concurrency, state changes) and performance implications (e.g., query load).
     - Determine test coverage gaps and documentation needs for the affected areas.
   - **Output:** A technical impact report with file paths, concerns, integration points, and assessment.

5. **Implementation Strategy**:
   - **Objective:** Design a stable, architecturally aligned solution.
   - **Actions:**
     - Propose a solution adhering to existing patterns (e.g., RESTful controllers, domain-driven services).
     - Break implementation into 3-5 incremental steps (e.g., “Add model, then service, then endpoint”) to minimize disruption.
     - Detail code changes with file paths, line ranges, and before/after snippets (or pseudocode if paths are unknown).
     - Highlight refactoring opportunities (e.g., consolidate duplicate logic, improve naming) to enhance organization.
     - Ensure separation of concerns (e.g., business logic in services, not controllers) and appropriate abstraction levels.
   - **Output:** A step-by-step plan with detailed changes, refactoring notes, and architectural alignment.

6. **Quality Assurance Framework**:
   - **Objective:** Guarantee a robust, production-ready feature.
   - **Actions:**
     - Define 5+ test scenarios across unit (e.g., function behavior), integration (e.g., API calls), and system levels (e.g., end-to-end flow).
     - Establish success criteria tied to requirements (e.g., “Endpoint returns 200 with valid data”).
     - Create a validation plan addressing performance (e.g., load tests) and security (e.g., input sanitization).
     - Suggest monitoring metrics (e.g., request latency, error rates) for long-term stability.
     - Include rollback procedures (e.g., revert commits) and feature toggles (e.g., config flags) for safety.
   - **Output:** A QA plan with test scenarios, criteria, validation methods, monitoring, and safety measures.

**Execution Guidelines:**
- Follow each step sequentially, completing all actions before advancing.
- Request clarification from the user if critical details (e.g., file paths, requirements) are missing, providing specific examples of what’s needed.
- Present responses in a structured format (e.g., numbered sections, code blocks) for clarity and traceability.
- Ensure the feature integrates seamlessly, enhances maintainability, and aligns with architectural goals.

---