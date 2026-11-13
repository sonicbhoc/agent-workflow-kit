# Agent workflow kit

Reusable agent skills and read-only reviewer profiles for planning features, assessing application security, and writing end-user guides.

## What's included

| Skill | Purpose |
| --- | --- |
| [feature-plan](skills/feature-plan/SKILL.md) | Research a feature, resolve important questions, and create a reviewable implementation plan. |
| [security-review](skills/security-review/SKILL.md) | Produce an evidence-based security assessment and phased remediation plan. |
| [user-guide](skills/user-guide/SKILL.md) | Document real user workflows, with screenshots where available. |

The [agent profiles](agents/) provide a codebase researcher, an independent plan reviewer, and an independent security reviewer. Separate profiles configure the read-only tools for GitHub Copilot and Claude Code.

## Install skills

The `skills` directory follows the [Agent Skills](https://agentskills.io) layout and can be installed using [npx skills](https://github.com/vercel-labs/skills). In PowerShell, list the skills from a local checkout:

```powershell
npx skills add "$HOME\source\repos\agent-workflow-kit" --list
```

Install selected skills globally for Copilot and Claude Code:

```powershell
npx skills add "$HOME\source\repos\agent-workflow-kit" --global --agent github-copilot claude-code
```

After publishing the repository, replace the local path with its GitHub `owner/repository` or URL. Review existing skills with the same names before installing; an install may replace them. The repository copies and any separately installed copies do not automatically stay in sync.

## Install agent profiles

`npx skills` installs skills, **not** the custom agent profiles. To install those globally, copy the files from the appropriate directory:

| Source | Destination |
| --- | --- |
| [`agents/copilot`](agents/copilot/) | `~\.copilot\agents\` |
| [`agents/claude`](agents/claude/) | `~\.claude\agents\` |

Check for existing files with the same names before copying. Restart the relevant session if it does not discover newly added profiles. Support for profiles, tools, and delegation varies by harness; the skills describe a fallback when a reviewer agent is unavailable.

## Safety and scope

Planning and security review do not authorize implementation. Runtime checks require an authorized non-production environment, and security findings must not reproduce secret values. The user-guide workflow pauses for user-driven sign-in and avoids consequential actions without approval.

## Credits

Inspired by Michael Washington's [Agentic Coding: Where I Am At Now (October 2026)](https://blazorhelpwebsite.com/ViewBlogPost/20094) on Blazor Help Website. The article credits [Saad Awais](https://github.com/imsaadawais) for the original planning prompt template. These skills adapt the article's planning, security-review, and user-guide workflows rather than reproducing the article verbatim.
