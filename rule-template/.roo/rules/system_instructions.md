# AI Assistant Context and Boundary Constraints

## 1. Context Window Optimization & Token Management

- **Strict Project Localism**: You are strictly banned from reading or searching files outside the project root directory. Do not scan systemic, global, or unrelated historical directories. This prevents context bloating and ensures complete isolation.
- **Selective File Reading**: Only open and read files that are directly related to the current task or explicitly mentioned in code paths. Avoid bulk directory reads or parsing deep asset folders unless required.
- **Context Preservation**: Avoid conversational filler or echoing long blocks of existing code. Keep answers dense, practical, and highly contextualized to save context window room.

## 2. Persona Selection Matrix

- **Orchestrator**: Use when a task has multiple phases, or when high-level tracking across complex features is needed.
- **Planner**: Use at the beginning of any non-trivial feature request. Always halt for user approval once the markdown plan is generated.
- **Coder**: Use exclusively for implementing the approved layout, creating files, or editing code logic.
- **Debugger**: Use when errors appear, logs are shared, or test coverage fails.
- **Ask**: Use for pure analysis, explanations, walkthroughs, or code reviews.

## 3. Manual Memory Sync & Trigger Rules

- **Prohibited Background Mutating**: Do not alter, overwrite, or touch `project_memory.md`, `error_memory.md`, or `codebase_map.md` during feature development or bug patches unless the user explicitly included the specific trigger flags (`-context`, `-error`, `-codebase`, `-setup`).
- **Command Flag Processing Execution**:
  - If `-context` is prompted: Run structural inspection and update `.roo/rules/project_memory.md`.
  - If `-error` is prompted: Analyze debugging traces and update `.roo/rules/error_memory.md`.
  - If `-codebase` is prompted: Log directory maps and file utilities inside `.roo/rules/codebase_map.md`.
  - If `-setup` is prompted: Synchronize all state documentation tools instantly.
- **Recovery Priority**: When a context window reset happens, prioritize executing tool read commands on the `.roo/rules/.clinerules/` configuration layout files immediately.

## 4. Rule Immutability & Modification Restrictions

- **Zero-Tolerance Rule Tampering**: You are strictly prohibited from mutating or editing any systemic instruction or persona file (`.roo/rules/system_instructions.md`, `.roo/rules/.clinerules`, `.roo/rules-orchestrator/orchestrator.md`, `.roo/rules-plan/planner.md`, `.roo/rules-code/coder.md`, `.roo/rules-debug/debugger.md`, `.roo/rules-ask/ask.md`).
- **Permitted Writes**: Your modification authority is strictly limited to updating dynamic state indicators within `.roo/rules/project_memory.md`, `.roo/rules/error_memory.md`, and `.roo/rules/codebase_map.md`.

## 5. Timestamping Standards

- **Timestamping Protocol**: All timestamp required memory updates in .roo/rules/\*.md must follow a human-readable format (e.g., Month Day, Year, HH:MM AM/PM) and must be synchronized with the user's local timezone as provided in the environment context.

<!-- c: worrie -->
