# Working with me

A small, portable AI Agent Skill to help me **finish valuable work instead of
continually expanding its scope or architecture**. It makes the assistant an
**active challenger**: willing to identify overengineering, explain what it
costs, and recommend a simpler route—without overruling a deliberate decision.

It supports two modes: **Deliver** (default) and **Explore** (intentional
brainstorming). It applies to coding, technical decisions, planning, research,
and other multistep tasks.

## What "active challenger" means

When a tangent would materially expand a delivery task, the AI should:

1. Identify what new work is being introduced and why it is not required now.
2. Explain the real cost: additional code, dependencies, testing, risk, or delay.
3. Recommend the smallest safe, complete route to the agreed outcome.
4. Respect my explicit choice if I decide the expanded scope is worthwhile.

The assistant should challenge **its own** proposals as well as mine. It should
not nag, block work, require constant approvals, or remove necessary security,
correctness, privacy, accessibility, or test coverage in the name of speed.

Example:

> **Me:** While we implement hopper validation, should we create a generic
> machine-connection framework?
>
> **AI:** That would add an abstraction and more testing beyond the immediate
> hopper rules. I'd validate the nine adjacent cells using the existing
> machine logic, then finish and test the feature. We can generalise if a
> second concrete use case emerges.

If I choose the framework anyway, the AI should update the scope and help
implement it rather than continuing to argue.

## Files

- [`skills/working-with-me/SKILL.md`](skills/working-with-me/SKILL.md) — full
  portable Agent Skill with active challenger protocol and examples.
- [`templates/AGENTS.md`](templates/AGENTS.md) — short, always-on instructions
  to copy into an individual code repository.

There are no scripts, services, or runtime dependencies.

## Install in coding agents

Clone this public repository and copy `skills/working-with-me/` into the
appropriate skill location for your agent.

| Agent | Personal skill location |
| --- | --- |
| OpenAI Codex | `~/.agents/skills/working-with-me/SKILL.md` |
| GitHub Copilot | `~/.agents/skills/working-with-me/SKILL.md` (supported personal location) |
| Cursor | `~/.agents/skills/working-with-me/SKILL.md` |
| Gemini CLI | `~/.agents/skills/working-with-me/SKILL.md` |
| Claude Code | `~/.claude/skills/working-with-me/SKILL.md` |

Install a repository-scoped copy in `.agents/skills/working-with-me/` for
agents that support it. For Copilot in GitHub-hosted/cloud environments, a
repository skill can live at `.github/skills/working-with-me/`. For Claude
Code, use `.claude/skills/working-with-me/` instead. Check your assistant's
current documentation because paths and activation behaviour may change.

### PowerShell example (Windows)

From the folder in which you want to clone the repository:

```powershell
# Replace YOUR_USERNAME with your GitHub username.
git clone https://github.com/YOUR_USERNAME/working-with-me.git

New-Item -ItemType Directory -Force "$HOME\.agents\skills" | Out-Null
Copy-Item -Recurse -Force ".\working-with-me\skills\working-with-me" "$HOME\.agents\skills\"

New-Item -ItemType Directory -Force "$HOME\.claude\skills" | Out-Null
Copy-Item -Recurse -Force ".\working-with-me\skills\working-with-me" "$HOME\.claude\skills\"
```

Restart or reload your agent if it does not detect the new skill. These are
local copies; updating GitHub does **not** automatically update them.

## Make the important rules always-on

A skill may activate only when an assistant decides the task is relevant. For
repositories where focus matters, copy `templates/AGENTS.md` to the root as
`AGENTS.md`. Some assistants recognise alternative instruction locations,
such as `.github/copilot-instructions.md` for GitHub Copilot and `CLAUDE.md`
for Claude Code. Keep these files short and aligned with the skill.

A public GitHub URL alone does **not** make every AI read the instructions.
The skill needs to be installed, explicitly referenced, or connected through
the assistant's supported mechanism.

### ChatGPT and other chat interfaces

When supported, install or attach the skill through the assistant's skill or
plugin mechanism. Otherwise, paste its essential instructions into the
project's persistent instructions or supply the file in the conversation.
Availability depends on the product and interface.

## Suggested prompts

- `Use working-with-me. Deliver mode: implement this GitHub issue and stop when the acceptance criteria pass.`
- `Use working-with-me. Challenge scope creep actively, including your own suggestions. Recommend one delivery path.`
- `Use working-with-me. Explore mode: compare three designs; do not implement or create backlog items.`
- `Apply the active challenger protocol: is this refactor necessary to finish the feature?`

## Quick acceptance test

Give the assistant a bounded feature request, then deliberately introduce an
optional architectural change. It should (1) identify the deviation, (2)
explain the concrete delivery cost, (3) recommend finishing the smallest
complete solution, and (4) accept a deliberate override without nagging.

Then check whether it actually delivers and verifies the feature instead of
suggesting a list of speculative follow-up improvements. Revise the skill
using observed outcomes rather than adding rules for imagined edge cases.

## Licence

MIT. See [LICENSE](LICENSE).
