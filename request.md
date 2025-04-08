my query:

{my request (e.g., "Add a button to clear the conversation", "Refactor the MessageItem component to use a new prop")}

---

**AI Task: Implement the Request Proactively and Safely**

Follow these steps **rigorously**, adhering to all rules in `core.md`. Prioritize understanding the goal, validating context, considering alternatives, proposing clearly, and ensuring quality through verification.

1.  **Clarify Intent & Validate Context (MANDATORY):**
    *   **a. Understand Goal:** Re-state your understanding of the core objective of `{my request}`. If ambiguous, **STOP and ask clarifying questions** immediately.
    *   **b. Identify Target Project & Scope:** Determine which project (`api-brainybuddy`, `web-brainybuddy`, or potentially both) is affected. State the target project(s).
    *   **c. Validate Environment & Structure:** Execute `pwd` to confirm CWD. Execute `tree -L 3 --gitignore | cat` (or `ls -laR`) focused on the likely affected project/directory.
    *   **d. Verify Existing Files/Code:** If `{my request}` involves modifying existing code, use `cat -n <workspace-relative-path>` or `read_file` to examine the relevant current code and confirm your understanding of its logic and structure. Verify existence before proceeding. If files are not found, **STOP** and report.

2.  **Pre-computation Analysis & Design Thinking (MANDATORY):**
    *   **a. Impact Analysis:** Identify all potentially affected files, components, hooks, services, types, and API endpoints within the target project(s). Consider potential side effects (e.g., on state management, persistence, UI layout).
    *   **b. UI Visualization (if applicable for `web-brainybuddy`):** Briefly describe the expected visual outcome or changes. Ensure alignment with existing styles (Tailwind, `cn` utility).
    *   **c. Reusability & Type Check:** **Actively search** (`codebase_search`, `grep_search`) for existing components, hooks, utilities, and types that could be reused. **Prioritize reuse.** Justify creating new entities only if existing ones are unsuitable. Check `src/types/` first for types.
    *   **d. Consider Alternatives & Enhancements:** Think beyond the literal request. Are there more performant, maintainable, or robust ways to achieve the goal? Could this be an opportunity to apply a better pattern or refactor slightly for long-term benefit?

3.  **Outline Plan & Propose Solution(s) (MANDATORY Confirmation Required):**
    *   **a. Outline Plan:** Briefly describe the steps you will take, including which files will be created or modified (using full workspace-relative paths).
    *   **b. Propose Implementation:** Detail the specific `edit_file` operations (including code snippets).
    *   **c. Include Proactive Suggestions (If Any):** If step 2.d identified better alternatives or enhancements, present them clearly alongside the direct implementation proposal. Explain the trade-offs or benefits (e.g., "Proposal 1: Direct implementation as requested. Proposal 2: Implement using a new reusable hook `useClearConversation`, which would be slightly more code now but better for future features. Which approach do you prefer?").
    *   **d. State Risks/Preconditions:** Clearly mention any dependencies, potential risks, or necessary setup.
    *   **e. Request Confirmation:** **CRITICAL:** Explicitly ask the user to confirm *which* proposal (if multiple) they want to proceed with and to give permission to execute the proposed `edit_file` command(s) (e.g., "Please confirm if I should proceed with Proposal 1 by applying the `edit_file` changes?").

4.  **Implement (If Confirmed by User):**
    *   Execute the confirmed `edit_file` operations precisely as proposed. Report success or any errors immediately.

5.  **Propose Verification Steps (MANDATORY after successful `edit_file`):**
    *   **a. Linting/Formatting/Building:** Propose running the standard verification commands (`format`, `lint`, `build`, `curl` test if applicable for API changes) for the affected project(s) as defined in `core.md` Section 6. State that confirmation is required before running these state-altering commands (per `core.md` Section 1.2.b).
    *   **b. Functional Verification (Suggest):** Recommend specific manual checks or testing steps the user should perform to confirm the feature/modification works as expected and hasn't introduced regressions (e.g., "Verify the 'Clear' button appears and removes messages from the UI and IndexedDB").

---

**Goal:** Fulfill `{my request}` safely, efficiently, and with high quality, leveraging existing patterns, suggesting improvements where appropriate, and ensuring rigorous validation throughout the process, guided strictly by `core.md`.