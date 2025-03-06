# **Cursor AI Rules**

## **1️⃣ General Principles**

- **Accuracy & Relevance**: Responses must strictly align with the request.
- **Direct Answers First**: Provide an immediate answer before attempting validation or deeper analysis.
- **Validation Over Modification**: Only modify files when explicitly instructed.
- **Request Missing Context**: If a request lacks essential details, AI must ask for clarification before proceeding.
- **Minimal & Safe Execution**: AI must **not** execute unnecessary commands, queries, or modifications.
- **Safety-First Execution**: Analyze dependencies and risks before making changes.
- **No Assumptions on Missing Information**: If a required file, path, or parameter is missing, AI must ask the user instead of guessing.

---

## **2️⃣ Mandatory Execution Rules**

### **📌 File Reading**

✅ **Use `run_terminal_cmd` with `cat <file path>` to read files.**

🚨 **DO NOT use `read_file`** (it provides partial content and can miss critical details).

Example:

```bash
cat ./config/settings.json | cat
```

---

### **📌 Command Execution**

✅ **Always append `| cat` to prevent interactive mode issues.**
🚨 **STOP execution on failures and ask the user before proceeding.**
✅ **Only execute necessary commands, nothing extra.**

Allowed Example:

```bash
ls -la | cat
```

🚫 **Forbidden:**

```bash
ls -la
```

---

## **3️⃣ 🚨 Strict File Modification Rules (`edit_file` Enforcement)**

🚨 **ABSOLUTELY FORBIDDEN: Using `run_terminal_cmd` to Create or Modify Files** 🚨
✅ **MANDATORY: Use `edit_file` for ALL modifications.**

### **❌ DO NOT USE THE FOLLOWING COMMANDS TO MODIFY FILES**

| 🚨 Forbidden Commands        | ✅ Use `edit_file` Instead               |
| ---------------------------- | ---------------------------------------- |
| `echo "text" >> <file>`      | `edit_file <full-path> "update content"` |
| `echo "text" > <file>`       | ✅                                       |
| `cat > <file>`               | ✅                                       |
| `sed -i 's/.../.../' <file>` | ✅                                       |
| `printf "...">> <file>`      | ✅                                       |

---

## **4️⃣ 🔍 Path Validation Rules (Prevent AI Hallucination)**

✅ **AI must use only absolute paths (relative to the project root) for `edit_file`.**
✅ **AI must verify paths BEFORE modifying files.**
🚨 **DO NOT create or modify a file unless the path is 100% verified.**
🚨 **If AI cannot determine the correct path, it must STOP and ask the user.**

### **✅ Path Validation Process Before `edit_file` Execution**

1. **Verify the provided path exists**:

   ```bash
   ls <full-path-to-file> | cat
   ```

2. **If the file does not exist, ask the user for confirmation** before creating it.
3. **If the path is ambiguous, STOP and prompt for clarification.**

✅ **Allowed Example**

```bash
edit_file ./infra/terraform/sikap-prod/03-redis-instance/sikap-redis-gke/main.tf "Update Redis config"
```

❌ **Not Allowed**

```bash
edit_file ./redis-config.tf "Update Redis config"  # 🚨 Path is too vague!
```

✅ **Example User Prompt for Path Clarification**

```markdown
"Multiple possible paths detected for `config.yaml`.
Please confirm the correct path:
1️⃣ `./config/config.yaml`
2️⃣ `./deploy/config.yaml`
3️⃣ `./infra/config.yaml`
Select the correct number or provide the full path."
```

---

## **5️⃣ 🚫 Strict Rules to Prevent AI Overreach**

### **📌 `tree` Execution (Only When Necessary)**

🚨 **DO NOT** execute `tree -L 4 --gitignore` unless:

- The request explicitly requires **file organization, dependencies, or structure.**
- AI needs to verify paths **before modification**.

✅ **Allowed Example**:

```markdown
- "Where is the Terraform configuration file located?"
  → ✅ Run `tree`
```

❌ **Not Allowed**:

```markdown
- "Can we query OpenSearch?"
  → ❌ DO NOT run `tree`
```

---

### **📌 Limit Query Execution (Prevent Overly Proactive Checks)**

🚨 **DO NOT make extra API queries or checks unless explicitly requested.**
✅ **Only verify when:**

- The request includes **"verify," "list," or "check all."**
- The response would be **incomplete or unreliable without it.**
- AI encounters a **clear dependency issue** that must be addressed.

✅ **Example Allowed Query**

```markdown
User: "Check my AWS permissions."
AI: ✅ Runs `aws sts get-caller-identity`
```

❌ **Not Allowed**

```markdown
User: "Can we run a query in OpenSearch?"
AI: ❌ Runs 5+ unnecessary verification commands.
```

---

## **6️⃣ 🚀 User-Controlled AI Behavior (Customize Execution Scope)**

✅ **Introduce optional flags for execution behavior:**

| Flag       | Behavior                                                              |
| ---------- | --------------------------------------------------------------------- |
| `--verify` | Enables **deep validation** (AWS checks, role verification, etc.).    |
| `--fast`   | Disables **extra** validation and runs the minimal required commands. |

✅ **Example:**

```bash
User: "Check OpenSearch access --fast"
→ AI skips excessive validation, directly runs the `aws-sso-util run-as` command.
```

---

## **7️⃣ 🔒 Security & Permissions Handling**

🚨 **DO NOT assume permissions (`*`) guarantee full access.**
✅ **Check for role-based constraints before executing actions.**
🚨 **If permissions are missing, report the issue and STOP execution.**

Example:

```bash
aws sts get-caller-identity | cat
```

---

## **8️⃣ 🚨 FINAL RULES: DO NOT BREAK THESE!**

🚨 **STRICT ENFORCEMENT RULES** 🚨

1. **DO NOT modify files with `run_terminal_cmd`**—always use `edit_file`.
2. **DO NOT execute `tree` unless the request involves codebase structure.**
3. **DO NOT perform excessive queries—answer first, verify second.**
4. **ALWAYS validate paths before executing `edit_file`.**
5. **STOP execution if AI cannot determine a correct path.**
6. **If in doubt, ask the user before proceeding.**