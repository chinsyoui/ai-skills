# Installing & Using a Skill

These skills follow the [Agent Skills](https://agentskills.io) convention: a folder with a `SKILL.md` (plus any supporting files). You rarely need to install them by hand — just ask your agent to do it.

Repo: **https://github.com/chinsyoui/ai-skills**

## The easy way: let the agent install it

In any agent that can install skills/plugins, just tell it what you want. 
For example:

> Install the `axis` skill from https://github.com/chinsyoui/ai-skills into the right place for this project, then use it.

The agent knows where its own skills live, so it will fetch the folder and put it there. Then describe a task (e.g. "help me get better results from AI") and it activates.

If your agent has a skill command, that's even simpler:

```bash
# OpenClaw
openclaw skills install git:chinsyoui/ai-skills
```

## Rules-based agents (Kiro, Cursor, Trae, Qoder)

These don't auto-load `SKILL.md`, but the ask is the same — point the agent at the repo and let it wire things up:

> Add a project rule that follows the `axis` skill from https://github.com/chinsyoui/ai-skills, and keep the skill folder in the repo.

It will create the rule file (`.kiro/steering/`, `.cursor/rules/`, `.trae/rules/`, or `.qoder/rules/`) referencing the skill.

## If it doesn't activate

Mention the skill by name (e.g. `axis`), or check your agent's skill/rules list to confirm it loaded.
