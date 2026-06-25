# Axis Skills

本目录包含 Axis 系统的所有 skill 定义及相关文件。

## 文件分类

### Skill 文件（`axis-*.md`）

每个 skill 是一份 markdown 格式的指令文档，描述 AI 在特定场景下应该如何行为。

- `SKILL.md` 是唯一的入口 skill。所有用户交互从这里开始，由它判断情况后路由到其他 skill。其他 skill 不会被直接触发，都经由 SKILL.md 分发。
- `axis-onboarding.md` 负责首次接触用户时了解其背景，产出 user profile（更新 `axis-user-profile.md`）。它不诊断也不 coach，只收集信息。
- 其余 `axis-*.md` 各自负责一个具体职能（coaching、测评、领域拓展等），由 SKILL.md 按需调用。

### 设计文档（`design-*.md`）

Skill 的伴生文档，记录对应 skill 的设计动机、核心洞察和关键决策。Skill 文件本身只写"怎么做"，设计文档记录"为什么这么做"。

不是每个 skill 都需要设计文档。简单直接的 skill（如 onboarding）不需要；涉及非显而易见的设计决策的 skill 才需要。

### 用户数据文件（`axis-user-profile.md` / `axis-test-*.md` / `axis-domain-expansion-*.md`）

运行时产生的用户相关数据，由各 skill 在交互过程中写入和更新。这些文件**不在 skill 目录内**，而是写入宿主系统的可写位置（如工作目录、workspace 根目录、memory 目录等）。

- `axis-user-profile.md`：用户 profile，由 onboarding 产出，其他 skill 按需读取（软依赖——没有也能工作，有了更好）。模板见 `references/axis-user-profile-template.md`。
- `axis-test-articulation.md`：测评结果。
- `axis-domain-expansion-{target}.md`：领域拓展分析结果。

这些文件是活的——随着用户持续使用 Axis，内容会被更新和补充。

## 约定

- Skill 之间通过约定的文件名互相引用（如 "look for `axis-user-profile.md`"），不硬编码路径。
- 用户数据文件写入宿主系统的可写位置，不写入 skill 目录（skill 目录可能是只读的）。
- 新增 skill 时需要在 `SKILL.md` 的路由表中注册，否则不会被触发。
- 用户数据文件不提交 git（属于运行时产物）。
