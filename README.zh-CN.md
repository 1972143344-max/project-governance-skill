# Project Governance Skill

[English README](README.md)

一个可复用的 Codex skill，用于在大型项目、长周期项目或多轮协作项目中建立并维护项目级治理文档体系。

它主要解决这些问题：

- 上下文漂移
- 旧文件干扰当前实现判断
- spec / design / decision 相互冲突
- 重要改动没有审计记录
- 多轮协作后缺少统一口径

它适用于需要“文档驱动协作”的项目，而不是只依赖聊天上下文临时维持一致性的项目。

## 这个 Skill 做什么

默认情况下，这个 skill 会引导 agent 在下面的位置建立项目级治理文档：

- `docs/<project-scope>/governance/`

标准文档集包括：

- `00_index_and_priority.md`
- `01_constraints_and_spec.md`
- `02_design.md`
- `03_behavior_audit.md`
- `04_lessons_learned.md`
- `05_decision_log.md`
- 可选 `06_active_plan.md`

如果一个仓库里同时存在多个长期项目或实验，它还支持一个可选的仓库级路由文档：

- `docs/governance/00_project_scope_registry.md`

这个路由文档只负责“识别当前应该进入哪个 project scope”，不负责定义具体项目的 spec、design 或 decision。

此外，仓库中还包含：

- 一个可复用的项目根目录 `AGENTS.md` 模板
- 一套用于渐进式披露的摘要模板
  - 文件顶部摘要头
  - 多文件 summary index

## 为什么需要它

大型项目经常会逐渐积累：

- 多个版本的设计方案
- 旧的调试记录
- 历史实验分支
- 多轮交互中不断变化的约束
- 没有落文档的决策

结果就是 agent 很容易：

- 读错文件
- 继承过时规则
- 在冲突未解决时继续实现
- 在完成任务后无法解释“为什么这么改”

这个 skill 的目标是把这些内容变成一套稳定、可审计、可迭代的治理层。

## 仓库结构

```text
project-governance/
  SKILL.md
  agents/openai.yaml
  assets/
    00_index_and_priority.template.md
    00_project_scope_registry.template.md
    01_constraints_and_spec.template.md
    02_design.template.md
    03_behavior_audit.template.md
    04_lessons_learned.template.md
    05_decision_log.template.md
    06_active_plan.template.md
    file-summary-header.template.md
    project-root-AGENTS.template.md
    summary-index.template.md
  references/
    governance-workflow.md
```

## 核心设计原则

- 默认 project-scoped：默认使用 `docs/<project-scope>/governance/`
- 仓库级只作补充：`docs/governance/` 只在仓库级共享治理或路由真正需要时才使用
- 稳定 slug：`<project-scope>` 优先使用稳定 slug，而不是自然语言标题
- 先问再建：不要静默创建或静默更新治理文档
- 不静默覆盖 `AGENTS.md`：如果项目根目录已有 `AGENTS.md`，先读取并讨论合并方案
- 不清楚就问：如果 scope、文档权威、内容归属或材料准确性不清楚，先问用户
- 大改前先讨论：遇到 spec 冲突、设计变更、历史结论被覆盖时，先讨论再改
- 大改后要审查：重要改动完成后要做 review pass
- 有不确定性要显式披露：不能把不确定点藏在“看起来很确定”的结论里

## 渐进式披露与上下文管理

这个 skill 还支持一套“渐进式披露”策略，用来降低大项目的上下文占用。

核心原则是：

- 先路由，再展开
- 先读摘要，再决定是否读正文
- 只读当前任务真正需要的部分
- 摘要用于导航，不用于替代权威文档

它提供两个配套模板：

- `file-summary-header.template.md`
  - 用于大文件顶部的摘要头
- `summary-index.template.md`
  - 用于多文件之间的轻量索引

适合这种场景：

- 文档很多，agent 不应一次性全读
- 单个文件很大，但不同任务只需要其中一部分
- 历史材料很多，需要先用摘要判断是否值得继续展开

但它不会把当前生效的 spec / decision 简化成只有摘要，因为那样会损坏权威边界。

## 解决的问题

### 1. 文档版本混乱

通过 `00_index_and_priority.md` 明确：

- 哪些是 authoritative
- 哪些是 working
- 哪些只是 historical/reference

### 2. 约束和需求静默漂移

通过 `01_constraints_and_spec.md` 保存当前真正生效的规则，而不是让规则散落在聊天记录和旧文件里。

### 3. 改动无法追溯

通过 `03_behavior_audit.md` 保留 append-only 审计记录。

### 4. 决策理由容易丢失

通过 `05_decision_log.md` 记录备选方案、取舍理由、风险和覆盖关系。

### 5. 大项目上下文过载

通过 routing、summary header 和 summary index，减少每次任务都全量读上下文的开销。

## 安装方式

### 方式 1：作为项目本地 skill 使用

把 `project-governance/` 目录复制到目标仓库：

- `.agents/skills/project-governance/`

### 方式 2：作为全局 Codex skill 使用

把 `project-governance/` 目录复制到：

- `~/.codex/skills/project-governance/`

然后重启 Codex，使新 skill 生效。

## 使用方式

详细使用说明见：

- [docs/USAGE.md](docs/USAGE.md)

常见提示词：

- `Use $project-governance to initialize governance docs for this project.`
- `Use $project-governance to adopt this existing project into the governance system.`
- `Use $project-governance to update the spec, design, and audit docs after these changes.`
- `Use $project-governance to create a repository-level project scope registry.`

## 推荐工作流

1. 先确认 active project scope，并选定稳定 slug
2. 判断当前任务是 project-scoped 还是 repository-wide
3. 如需要，初始化项目根目录 `AGENTS.md`
4. 先创建 `00_index_and_priority.md`
5. 再创建其余治理文档
6. 在项目推进中：
   - 大改前先讨论或立计划
   - 获得确认后再更新治理文档
   - 审计日志尽量 append-only
   - 大改后做 review pass
   - 把不确定性显式告诉用户
7. 对大文档或多文件项目：
   - 先用索引或摘要做路由
   - 按职责拆分文件
   - 避免把摘要当成权威正文

## 包含的模板

- `00_index_and_priority.template.md`
  - 定义权威文档、工作文档、历史文档和冲突优先级
- `00_project_scope_registry.template.md`
  - 多项目仓库的仓库级路由注册表
- `01_constraints_and_spec.template.md`
  - 当前需求、约束、统一 spec
- `02_design.template.md`
  - 实现框架、设计细节、设计变更记录
- `03_behavior_audit.template.md`
  - append-only 行为审计
- `04_lessons_learned.template.md`
  - 经验与复盘
- `05_decision_log.template.md`
  - 决策、备选方案、理由、风险、覆盖关系
- `06_active_plan.template.md`
  - 可选的持久化计划文档
- `project-root-AGENTS.template.md`
  - 项目根目录协作规则模板
- `file-summary-header.template.md`
  - 文件顶部摘要头模板
- `summary-index.template.md`
  - 多文件轻量索引模板

## 文档管理策略

这个仓库强调的是：

- 把“规则”和“细节”分开
- 把“路由”和“权威”分开
- 把“摘要”和“正文”分开

也就是说：

- 仓库级路由文档只负责找 project
- project governance 负责具体项目定义
- summary 负责减少上下文，不负责改写真相

这样既能减少上下文占用，又能尽量避免摘要漂移和旧文件干扰。

## License

本仓库当前使用 `MIT` 许可证。
