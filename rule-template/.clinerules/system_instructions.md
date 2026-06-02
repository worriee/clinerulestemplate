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

## 3. Persistent Memory Sync & Enforcement

- After major tasks are planned, started, or completed, or when independent user edits are discovered via Sync-on-Prompt, update the `project_memory.md` and `error_memory.md` files to keep the agent state perfectly aligned across sessions and alternative AI clients (Cline, Roo Code, Cursor, Zoo Code, etc.).
- **Startup Setup Prompt**: If a user prompts "-setup" you should immediately update the memory files the `project_memory.md`, `error_memory.md`, and `codebase_map.md` so you have a context right at the beginning then use this if you experience token loss or context window loss as these files will be your main memory if you forgot something you go back here to these files. If there's a problem or issue during this setup especially in reading files in terminal don't use that command again if it doesn't work and try another command approach. Find an absolute way so you can update the memory since this is mandatory rule and not optional. If you experience memory loss, token loss or context window loss during this process make sure to continue where you left off by temporarily using the context of the current chat session.
- **Enforced Continuity**: Under no circumstances should a file be created, modified, or debugged without an accompanying structural update to the `.clinerules/` memory layers.
- If a session memory loss is detected, you must prioritize reading `.clinerules/.clinerules`, `project_memory.md`, `error_memory.md`, and `codebase_map.md` over generating any code outputs.

## 4. Rule Immutability & Modification Restrictions

- **Zero-Tolerance Rule Tampering**: You are strictly prohibited from mutating or editing any systemic instruction or persona file (`system_instructions.md`, `.clinerules`, `orchestrator.md`, `planner.md`, `coder.md`, `debugger.md`, `ask.md`).
- **Permitted Writes**: Your modification authority is strictly limited to updating dynamic state indicators within `project_memory.md`, `error_memory.md`, and `codebase_map.md`.

<!-- c: worrie -->