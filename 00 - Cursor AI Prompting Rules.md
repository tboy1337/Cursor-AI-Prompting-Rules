# Cursor AI Prompting Rules

This gist provides structured prompting rules for optimizing Cursor AI interactions. It includes three key files to streamline AI behavior for different tasks.

## Files and Usage

### **`core.md`**

- **Purpose:** Defines the foundational rules for Cursor AI behavior across all tasks.
- **Usage:** Add this to `.cursorrules` in your project root or configure it via Cursor settings:
  - Open `Cmd + Shift + P`.
  - Navigate to Sidebar > Rules > User Rules.
  - Paste the contents of `core.md`.
- **When to Use:** Always apply as the base configuration for consistent AI assistance.

### **`refresh.md`**

- **Purpose:** Guides the AI to debug, fix, or resolve issues, especially when it loops on the same files or overlooks relevant dependencies.
- **Usage:** Use this as a prompt when encountering persistent errors or incomplete fixes.
- **When to Use:** Apply when the AI needs to reassess the issue holistically (e.g., “It’s still showing an error”).

### **`request.md`**

- **Purpose:** Instructs the AI to handle initial requests like creating new features or adjusting existing code.
- **Usage:** Use this as a prompt for starting new development tasks.
- **When to Use:** Apply for feature development or initial modifications (e.g., “Develop feature XYZ”).

## How to Use

1. Clone or download this gist.
2. Configure `core.md` in your Cursor AI settings or `.cursorrules` for persistent rules.
3. Use `refresh.md` or `request.md` as prompts by copying their contents into your AI input when needed, replacing placeholders (e.g., `{my query}` or `{my request}`) with your specific task.

## Notes

- These rules are designed to work with Cursor AI’s prompting system but can be adapted for other AI tools.
- Ensure placeholders in `refresh.md` and `request.md` are updated with your specific context before submission.
