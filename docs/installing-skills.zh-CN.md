# 安装与使用 Skill

这些 skill 遵循 [Agent Skills](https://agentskills.io) 约定：一个带 `SKILL.md` 的文件夹（外加可选的辅助文件）。你基本不需要手动安装——直接让 agent 去做就行。

仓库：**https://github.com/chinsyoui/ai-skills**

## 最简单的方式：让 agent 自己装

在任何能安装 skill/插件的 agent 里，直接说出你的需求即可。例如：

> 把 https://github.com/chinsyoui/ai-skills 里的 `axis` skill 安装到本项目合适的位置，然后使用它。

agent 知道自己的 skill 该放哪，会把文件夹取下来放好。之后描述一个任务（如"帮我更好地用 AI 拿到结果"）即可激活。

如果你的 agent 有 skill 命令，就更简单：

```bash
# OpenClaw
openclaw skills install git:chinsyoui/ai-skills
```

## 基于规则的 agent（Kiro、Cursor、Trae、Qoder）

这类 agent 不会自动加载 `SKILL.md`，但说法一样——把仓库指给它，让它自己接好：

> 添加一条项目规则，遵循 https://github.com/chinsyoui/ai-skills 里的 `axis` skill，并把该 skill 文件夹保留在仓库中。

它会在 `.kiro/steering/`、`.cursor/rules/`、`.trae/rules/` 或 `.qoder/rules/` 下创建一个引用该 skill 的规则文件。

## 如果没激活

按名字提一下该 skill（如 `axis`），或在 agent 的 skill/rules 列表里确认它已加载。
