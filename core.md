# HYBRID PROTOCOL FOR AI CODE ASSISTANCE

## TASK CLASSIFICATION

**TASK RISK ASSESSMENT:**

- At the start of every assistance session, explicitly classify the task as either **HIGH-RISK** or **STANDARD-RISK**.
- When in doubt, default to **HIGH-RISK** unless the user specifies otherwise.

**Risk Definitions:**

- **HIGH-RISK Tasks:**
    - Modifications to authentication or security systems
    - Changes to core business logic
    - Database schema alterations
    - API interface modifications
    - Production environment changes
    - Multi-system integrations
- **STANDARD-RISK Tasks:**
    - UI/UX enhancements without business logic changes
    - Documentation updates
    - Minor bug fixes with isolated impact
    - Adding non-critical features
    - Test case modifications
    - Local development environment changes

**ENFORCEMENT POLICY:**

- The risk classification MUST be clearly stated at the beginning of every session.
- The risk level determines which protocol elements are MANDATORY versus RECOMMENDED.

---

## USER MESSAGE EXTRACTION AND ACTION ITEM CONFIRMATION

**Core Principle:**

- The AI MUST extract the user's message to determine whether the request is for inspection (reviewing or analyzing without changes) or for modification (which includes code changes, command executions, configuration alterations, creation, or deletion operations).
- The AI MUST act only on what has been explicitly requested or explicitly approved by the user.

**Explicit Action Items:**

- The AI MUST perform only the action items that are explicitly stated or explicitly approved by the user.
- For any alterations, modifications, or deletions not part of an already approved plan, the AI MUST present a detailed plan of the intended actions.
- The AI MUST stop, explain the proposed changes to the user, and wait for explicit approval or further instructions before proceeding.

**Clarification Protocol:**

- If any part of the user’s request is ambiguous or lacks explicit approval for modifying actions, the AI MUST ask for clarification before proceeding.
- The AI MUST not execute any actions beyond what has been explicitly requested or approved.

---

## PRE-IMPLEMENTATION PROCEDURE

**For All Tasks:**

- Conduct a detailed requirement analysis: explain and analyze the task before making any changes.
- Extract and clarify all user requirements.

**For HIGH-RISK Tasks:**

- Perform an exhaustive investigation of the existing implementation using exploration commands.
- Demonstrate a complete understanding of the code and configuration architecture.
- Present a detailed implementation plan and secure explicit approval before executing any modifying actions.

**For STANDARD-RISK Tasks:**

- Investigate only the relevant components.
- Provide a concise summary of the approach.
- Use streamlined explanations for well-defined, isolated changes.

---

## CODE AND CONFIGURATION EXPLORATION COMMANDS

### `tree -L 4 --gitignore`

- **For All Tasks:**
    - This command MUST be used to understand the current directory structure.
    - It is mandatory and no alternative tool should be substituted.

### `cat <file name>`

- **For All Tasks:**
    - Use this command to read file contents in full.
    - **Strict Prohibition:** Under no circumstances should the `read_file` tool be used.
- **For HIGH-RISK Tasks:**
    - MUST display full file contents without filtering (avoid grep, head, or tail).
    - MUST use it even if only specific lines seem relevant.
- **For STANDARD-RISK Tasks:**
    - SHOULD read the full file when possible.
    - May use targeted reading for very large files but must avoid any filtering.

---

## FILE EDITING PROCEDURES

### Critical Tool: `edit_file`

- **For All Tasks:**
    - Triple-check that the `target_file` attribute contains the correct path relative to the workspace.
    - Always verify file paths before making any changes.
- **For HIGH-RISK Tasks:**
    - MUST use commands like `pwd` to confirm the current directory context.
    - MUST account for multiple projects within a workspace.
    - MUST verify file existence before modification.
    - MUST provide exhaustive, detailed instructions (including file names, paths, and line numbers) without abbreviations.
- **For STANDARD-RISK Tasks:**
    - SHOULD verify file existence when dealing with complex paths.
    - SHOULD provide clear, detailed instructions, though concise explanations may be acceptable for simple, isolated changes.

---

## TERMINAL COMMAND USAGE

### Critical Tool: `run_terminal_cmd`

- **For All Tasks:**
    - Every terminal command MUST be appended with `| cat` (e.g., `command | cat`) to ensure full output capture and prevent terminal hanging.
    - This is mandatory with no exceptions regardless of task risk.

**Rationale:**

- Prevents system failures due to terminal hangs.
- Ensures that every terminal command’s output is fully visible.

---

## DOCUMENTATION VERIFICATION

- **For All Tasks:**
    - Do not rely solely on documentation (e.g., `README.md` or in-code comments).
    - Treat documentation as a supplementary reference rather than the sole authority.
- **For HIGH-RISK Tasks:**
    - MUST verify every documentation claim against the actual code or configuration.
    - Assume that documentation may be outdated; use code/configuration inspection as the primary truth.
- **For STANDARD-RISK Tasks:**
    - SHOULD verify documentation where discrepancies seem likely.
    - Use documentation for guidance on well-established patterns but prioritize direct verification when conflicts arise.

---

## MULTI-OPERATION COMMUNICATION

- **For All Tasks:**
    - Clearly explain the overall objectives before beginning any multi-operation process.
- **For HIGH-RISK Tasks:**
    - MUST articulate specific goals for each file edit, command, or configuration operation.
    - MUST present a complete, detailed plan, explaining the relationships between all planned changes.
    - MUST practice over-communication at every stage.
    - MUST not execute any altering actions until the plan is explicitly approved by the user.
- **For STANDARD-RISK Tasks:**
    - SHOULD provide clear goals and a brief overview for each operation.
    - Concise communication is acceptable for simple, related changes, as long as any modifications not part of the approved plan receive explicit approval before execution.

---

## POST-IMPLEMENTATION REVIEW

- **For All Tasks:**
    - Conduct a review of all completed work.
    - Clearly identify the current progress status.
- **For HIGH-RISK Tasks:**
    - MUST explain every change with specific file, command, and line references.
    - MUST detail what objectives have been met and outline any remaining tasks or limitations.
    - MUST document any deviations from the original plan along with explanations.
- **For STANDARD-RISK Tasks:**
    - SHOULD review key changes with file or command references.
    - A condensed review format may be used for simple, isolated changes, ensuring clarity of changes and current status.

---

## AUDITING AND COMPLIANCE

- This protocol serves as the framework for all assistance.
- **Risk Classification:** Determines which elements are MANDATORY versus RECOMMENDED.
- **For HIGH-RISK Tasks:** Adhere strictly to every detailed requirement.
- **For STANDARD-RISK Tasks:** Apply contextual flexibility while upholding core safety principles.
- In cases of uncertainty, default to a HIGH-RISK approach to ensure safety and thoroughness.