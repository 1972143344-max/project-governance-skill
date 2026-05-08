# Project Governance Skill

[English](./README.md)

这个仓库打包了一个可复用的 Codex skill，用于在长周期项目中维护项目级治理体系。

它适合解决这些问题：

- authority 路由不稳定
- 文档更新缺少统一方法
- task、audit、decision 面不同步
- 上下文压缩、暂停或切会话后难以恢复
- 历史摘要、聊天记录或旧文档反过来污染当前真相

## 仓库结构

```text
project-governance-skill/
  README.md
  README.zh-CN.md
  docs/
    USAGE.md
  project-governance/
    SKILL.md
    agents/openai.yaml
    assets/
    references/
```

## 这个 skill 覆盖什么

`project-governance/` 里的 skill 主要帮助 agent：

- 初始化或接管项目级治理
- 同步 authority、task、audit、decision 等治理面
- 采用 route-first 阅读和渐进式披露
- 维护项目级 recovery / context 状态
- 用 lane 区分 docs、review、probe、implementation、结构维护等轮次
- 保持 authority 边界，避免摘要或聊天历史反过来定义项目真相

## skill 目录内容

`project-governance/` 下包含：

- `SKILL.md`：治理工作流约束
- `agents/openai.yaml`：skill 入口元数据
- `assets/`：治理文档、context 面、summary header、index、lane-based task record 模板
- `references/governance-workflow.md`：工作流参考
- `references/acceptance-scenarios.md`：验证场景

## 安装方式

### 作为全局 Codex skill 安装

把 `project-governance/` 目录复制到：

```text
<CODEX_HOME>/skills/project-governance/
```

### 作为项目级本地 skill 安装

把同一个 `project-governance/` 目录复制到：

```text
<repo>/.agents/skills/project-governance/
```

如果同名的 repo-local skill 和 user-level skill 同时存在，Codex 可能同时发现两者。若你有意保留双份，请确保它们同步。

## 说明

- 这个 skill 保持仓库无关，不依赖某一个固定项目结构，只依赖文档里约定的治理面。
- 在当前常见布局中，具体的 recovery surface 通常落在 `docs/<project-scope>/context/`。
- 如果仓库本地治理定义了更严格或更新的 contract，应以仓库本地规则为准。

## 使用

使用说明和示例提示词见 [docs/USAGE.md](./docs/USAGE.md)。
