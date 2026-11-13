---
name: feature-plan
description: Create or refine a self-contained Markdown feature or application plan from repository evidence. USE FOR planning features, interviewing about requirements, creating a master plan, or breaking a master plan into implementation specs. DO NOT USE FOR implementing an approved plan or reviewing an existing plan without revising it.
---

# Feature planning

Create a repository-grounded plan that resolves important product and engineering decisions before implementation. This is planning only: do not modify source code or start implementation.

## Workflow

1. **Inspect first.** Read applicable `AGENTS.md`, `.github/copilot-instructions.md`, and repository guidance. Find relevant code and existing plan examples. Use `codebase-researcher` for bounded, independent research when available and permitted; otherwise inspect relevant areas directly. Cite only files and symbols actually read.
2. **Clarify material gaps.** Ask about edge cases, scope, user roles, trade-offs, and acceptance criteria that cannot be established from the repository. Do not ask questions the code or docs answer. Ask before writing if a choice materially changes architecture, scope, or behavior. Give options, a recommended default, and why each choice matters. If several questions are needed, ask them in a concise batch when the interface supports it; otherwise ask one at a time. If nothing material is unclear, proceed without questions.
3. **Choose the document shape.** For a bounded feature, use the repository's existing planning convention and file naming. If none exists, default to `Docs/<Feature-Name>-Plan.md`. For an end-to-end application, create a master plan first; only after it is reviewed, derive focused sub-plans from it. If features are unrelated, ask whether to create one plan or separate plans. If the destination exists, inspect it and ask before overwriting.
4. **Write an implementable plan, not code.** Scale detail to scope. Include:
   - summary, goals, non-goals, and decisions, including rejected alternatives and reasons
   - current state with links to evidence; mark uncertain claims `(assumed)`
   - design and contracts: signatures, schemas, configuration, defaults, and examples where applicable
   - major flows, including failure paths
   - file-by-file change table: `File | New/Modified | Change`
   - security and privacy considerations, tests, risks and mitigations, and acceptance criteria
   - ordered implementation tasks, each small enough for a PR, with a concrete "done when" check
   - open questions
5. **Validate evidence and diagrams.** Re-open every cited file or member and confirm the description. Render Mermaid diagrams if a renderer is available; otherwise check syntax against the rules below and say they were not rendered. Do not claim a diagram was rendered when it was only inspected.
6. **Independent review.** When permitted, give `plan-reviewer` only the plan path and codebase access, not this conversation's requirements discussion. Ask for actionable gaps: unsupported claims, decisions a developer still needs, missing failure paths, contradictions, and tasks too large to implement. Incorporate valid findings; if the agent is unavailable, perform a distinct skeptical pass and say so.
7. **Report.** Give the plan path, a concise summary, decisions made on the user's behalf, unaddressed review findings, diagram-rendering status, and open questions.

## Mermaid rules

- Do not use `\n` in labels; use `<br/>` or shorten the label.
- Do not begin a label with `1.`; use `Step 1:` or sequence-diagram `autonumber`.
- Quote labels containing Mermaid punctuation such as parentheses, brackets, braces, colons, semicolons, slash, hash, or ampersand.
- Use alphanumeric node IDs; avoid reserved words such as `end`, `graph`, and `subgraph` as IDs.
- Keep diagrams near 20 nodes; split larger flows.

## Boundaries

- Do not write source code, run implementation commands, or create code as part of planning.
- Do not invent repository behavior. Link claims to evidence or mark them `(assumed)`.
- Do not put credentials, tokens, connection strings, real hostnames or IPs, or personal data in a plan; use placeholders.
- Do not use terminal commands to create the plan file. Use the normal file-editing capability.
- A plan is not approval to implement it. Wait for the user's direction.
