---
name: user-guide
description: Create or refresh an end-user guide from the application's actual UI and behavior. USE FOR writing a user guide, documenting screens and workflows, creating Docs/User-Guide.md, or capturing guide screenshots. DO NOT USE FOR API or developer documentation or feature specifications.
---

# End-user guide

Create an accurate guide for the application's actual users. Use plain language, document observable behavior rather than implementation details, and do not modify application source code.

## Workflow

1. Read repository instructions and inspect navigation, pages and components, settings, validation, and existing help content. Identify the app's actual user roles and workflows; ask about audience, permissions, preview features, or other material unknowns that code cannot establish.
2. Run the application only in a local or otherwise authorized non-production environment. Walk through each relevant screen and end-to-end task with the browser. If sign-in requires the user, stop at the sign-in screen and wait for them; do not solicit or handle their password or tokens. Do not use production accounts or data or perform destructive or external actions without explicit approval.
3. Capture a screenshot for each screen or key task step when the browser tool supports it. Save images under the repository's documentation convention, defaulting to `Docs/images/user-guide/`, and use relative links. Review every screenshot for secrets, personal data, and real resource identifiers; crop or redact before saving. If visual capture or a workflow is blocked, do not fabricate it; document the limitation and ask for help if needed.
4. Write or update `Docs/User-Guide.md` or the existing documentation location. Use:
   - `# <Application Name> user guide`
   - `## Before you start`: accounts, permissions, software, and required data
   - `## How it works`: short overview and a Mermaid workflow diagram
   - ordered numbered task sections, each with when to use it, steps, expected result, and screenshot
   - `## Troubleshooting` table: `Symptom | Cause | Fix`, based on actual validation and error text
   - `## Frequently asked questions` only when there are real FAQs
5. Match visible button, menu, and field labels exactly; write short sentences for end users. Do not describe classes, code, or project structure. If an in-app Help or Guide exists, align headings and anchors; if absent, note a suggestion in the chat report without creating the in-app page.
6. Verify all described tasks against the running UI, all links and screenshots resolve, and all visible strings match. Re-open the document and check that no secrets or personal data remain.
7. Report the document path, workflows covered, blocked or unverified flows, whether screenshots were captured, and outstanding questions.

## Mermaid and privacy rules

- Do not put `\n` in Mermaid labels or start edge labels with `1.`; use `<br/>` or `Step 1 - ...`.
- Use placeholders such as `<your-email>` instead of real names or identifiers. Do not include passwords, tokens, keys, connection strings, hostnames, IP addresses, or personal data, even if they appeared in the UI.
- Do not claim the guide reflects a screen or behavior that you could not observe. If the app cannot be run, ask whether to proceed with a clearly marked source-informed, runtime-unverified guide.
