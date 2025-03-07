{my request (e.g. Develop feature xyz)}

---

Approach this request with the strategic mindset of a solution architect and senior engineer:

1. **Architectural Understanding**:
   - Map the application's current architecture patterns and conventions
   - Identify domain models, abstractions, and organizational principles
   - Determine where the requested feature naturally fits within this structure
   - Consider how the feature aligns with the system's overall design philosophy

2. **Requirements Engineering**:
   - Transform the request into clear requirements with acceptance criteria
   - Identify stakeholders and potential use cases for the feature
   - Define technical constraints and non-functional requirements
   - Establish boundaries to maintain architectural integrity

3. **Code Reusability Analysis**:
   - Search for existing components, utilities, or patterns that can be leveraged
   - Identify opportunities to extract reusable abstractions during implementation
   - Assess if the feature should be implemented as a reusable module for future use
   - Review similar implementations across the codebase for consistency

4. **Technical Discovery**:
   - Map all affected areas of the codebase with specific file paths
   - Analyze cross-cutting concerns (authentication, logging, error handling, etc.)
   - Evaluate integration points and API boundaries
   - Consider how the implementation will affect system behaviors and performance
   - Assess test coverage and documentation needs

5. **Implementation Strategy**:
   - Design a solution that follows established architectural patterns
   - Break down implementation into incremental steps that preserve system stability
   - Detail specific code changes with before/after comparisons
   - Highlight opportunities to improve existing code organization
   - Preserve separation of concerns and maintain appropriate abstraction levels

6. **Quality Assurance Framework**:
   - Define comprehensive test scenarios across unit, integration, and system levels
   - Establish criteria for successful implementation
   - Create a validation plan that includes performance and security considerations
   - Suggest monitoring metrics to ensure long-term stability
   - Include rollback procedures and feature toggles if appropriate

This architectural approach ensures the feature integrates seamlessly while strengthening the codebase's overall design and maintainability.
