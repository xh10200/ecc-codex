# Personal Codex Guidance Base

这是一个为 Codex 维护的个人规范仓库。

基于早期 ECC 上游内容整理和裁剪而成，当前定位为个人 Codex 规范与加载基座。

当前范围聚焦于本机 AI 辅助设计、开发、测试与验证闭环，优先服务 `Go`、`Python`、`C#`、`TypeScript` 以及数据库与前端原型工作流。

仓库基线严格限定为“本地执行、绝不出网”：
- 不依赖远程文档检索、远程连接器或在线研究工具
- 不依赖会再次发起在线模型调用的子流程
- 只保留面向本机设计、开发、测试、验证的工作流

这套仓库的目标很简单：
- 用根目录入口文件定义默认行为
- 用 `agents/`、`rules/`、`skills/` 维护核心规范资产
- 用 `docs/` 维护这些核心资产的说明和多语言文档
- 用 `.codex/`、`.agents/` 作为更贴近 Codex 的本地加载和映射层
- 用 `docs/zh-CN/`、`docs/ja-JP/` 维护多语言说明，包括 agents、skills 和 rules

## 快速理解

一句话概括：

- 根目录文件：默认入口
- `agents/`、`rules/`、`skills/`：核心标准源
- `docs/`：说明和多语言文档
- `.codex/`、`.agents/`：Codex 的本地运行时配置和投喂层

## 分层说明

### 根目录文件

根目录文件是默认设定入口。

- `AGENTS.md`：总入口和执行指南
- `RULES.md`：硬约束和必须遵守的规则
- `SOUL.md`：人格、语气、方法论
- `README.md`：仓库概览、分层说明和当前保留面导航

对于 Codex，这一层负责回答三个问题：
- 进入仓库后先看什么
- 默认遵守什么
- 默认按什么风格和工作方式执行

### `agents/`、`rules/`、`skills/`

这是核心标准源，也是平时主要编辑的内容层。

- `agents/`：定义代理角色
- `rules/`：定义规则
- `skills/`：定义技能

可以把这三类目录理解为“主数据源”。如果需要新增或修改长期规范，优先改这里。

### `docs/`

这是文档和多语言说明层。

主要职责：
- 维护 `agents/`、`rules/`、`skills/` 的补充说明
- 维护这些内容的多语言版本

这一层主要用于查阅和维护，不是默认强加载入口。

### `.codex/`、`.agents/`

这是面向 Codex 的本地加载和运行时映射层。

- `.codex/`：Codex 专属配置、本地偏好、初始化补充
- `.agents/`：为 Codex 准备的辅助加载层和 skill 投喂层

它们不是主知识源，而是让 Codex 更容易直接吃到这些规范的“投喂层”。

## 当前保留面

按当前精简结果，这个仓库主要由三部分组成：
- `agents/`：负责分工和角色化协作
- `skills/`：负责方法库、流程模板和专项实践
- `rules/`：负责硬约束、通用标准和语言规则

### Agents

当前主保留的 agent 共 16 个：

- `planner`：实现规划、阶段拆解、风险识别和测试策略设计
- `architect`：架构分析、边界划分、技术选型和系统设计判断
- `tdd-guide`：测试先行、Red-Green-Refactor 和覆盖率控制
- `code-reviewer`：通用代码审查，关注正确性、可维护性和缺失测试
- `security-reviewer`：安全审查，检查输入验证、鉴权、注入、密钥和敏感数据处理
- `build-error-resolver`：快速修复构建、类型和编译错误，强调最小改动
- `e2e-runner`：使用本地 Playwright 运行端到端测试和关键用户流程验证
- `refactor-cleaner`：清理死代码、重复逻辑和可安全收缩的旧结构
- `database-reviewer`：聚焦 PostgreSQL，处理查询优化、schema 设计、RLS 和性能问题
- `go-reviewer`：Go 代码审查，关注惯用法、并发、错误处理和性能
- `go-build-resolver`：处理 Go 的 build、vet、lint 和编译问题
- `python-reviewer`：Python 代码审查，关注 Pythonic 风格、类型、性能和安全
- `typescript-reviewer`：TypeScript/JavaScript 代码审查，关注类型安全、异步正确性和 Web/Node 安全
- `gan-planner`：GAN 原型链路中的规划角色，把一句需求扩成前端原型 spec
- `gan-generator`：GAN 原型链路中的生成角色，按 spec 实作原型并持续迭代
- `gan-evaluator`：GAN 原型链路中的评审角色，跑本地应用并按 rubric 打分反馈

Codex 运行层额外保留了两个轻量角色：
- `explorer`：只读代码探索
- `reviewer`：只读审查

### Skills

当前主保留的 skill 共 19 个：

- `ai-regression-testing`：AI 辅助开发下的回归测试策略，专门抓模型容易忽略的问题
- `api-design`：REST API 设计规范，包括资源命名、分页、过滤、错误格式和限流
- `bun-runtime`：Bun 作为 runtime、包管理器、bundler 和测试运行器的使用建议
- `codebase-onboarding`：快速读陌生仓库，生成入口图、约定和入门说明
- `coding-standards`：TypeScript/JavaScript/React/Node 的通用编码规范
- `database-migrations`：数据库迁移、回滚、零停机 schema 变更和数据迁移模式
- `e2e-testing`：Playwright 的 E2E 组织方式、POM、配置和抗 flaky 策略
- `eval-harness`：Eval-driven development 的评估框架和验证流程
- `frontend-patterns`：React / Next.js 前端开发模式、状态管理和 UI 组织
- `golang-patterns`：Go 语言惯用写法、工程结构和常见实现模式
- `golang-testing`：Go 的表驱动测试、subtest、benchmark、fuzz 和覆盖率实践
- `nextjs-turbopack`：Next.js 16+ 与 Turbopack 的使用场景和开发体验要点
- `postgres-patterns`：PostgreSQL 的索引、schema、查询优化和安全模式
- `python-patterns`：Pythonic 风格、PEP 8、类型标注和常见实现模式
- `python-testing`：pytest、fixture、mock、参数化和 Python 测试组织
- `security-review`：安全检查清单，适合鉴权、输入、密钥、接口和敏感功能
- `skill-stocktake`：盘点本地 skills 和 workflow 质量，用于做技能资产审查
- `tdd-workflow`：新功能、修 bug、重构时的 TDD 工作流，强调 80%+ 覆盖
- `verification-loop`：构建、测试、lint、typecheck 和安全检查的验证闭环

### Rules

`rules/` 现在采用“通用层 + 语言层 + 中文翻译层”的结构，主保留文件共 41 个。

通用规则 `rules/common/`：
- `agents`：什么时候该用哪个 agent，以及基本协作方式
- `code-review`：代码审查标准和优先级
- `coding-style`：语言无关的编码风格原则
- `development-workflow`：从澄清、规划、实现到验证的整体开发流程
- `git-workflow`：提交、分支、变更整理的 git 约定
- `hooks`：Codex 语境下的本地验证建议
- `patterns`：通用设计模式和结构建议
- `performance`：性能意识、热点识别和常见优化原则
- `security`：通用安全底线
- `testing`：测试层级、覆盖率和验证要求

语言规则层当前保留 4 套：
- `rules/csharp/`：`coding-style`、`hooks`、`patterns`、`security`、`testing`
- `rules/golang/`：`coding-style`、`hooks`、`patterns`、`security`、`testing`
- `rules/python/`：`coding-style`、`hooks`、`patterns`、`security`、`testing`
- `rules/typescript/`：`coding-style`、`hooks`、`patterns`、`security`、`testing`

中文翻译层 `rules/zh/` 是通用规则的中文版本，包含：
- `README`
- `agents`
- `code-review`
- `coding-style`
- `development-workflow`
- `git-workflow`
- `hooks`
- `patterns`
- `performance`
- `security`
- `testing`

## 使用建议

维护这套仓库时，优先遵循下面的顺序：

1. 默认行为先看根目录入口文件
2. 长期规范优先写入 `agents/`、`rules/`、`skills/`
3. 文档解释和翻译维护在 `docs/`
4. Codex 专属适配再放进 `.codex/` 或 `.agents/`

这样可以保证：
- 核心规范和运行时适配分离
- 多语言文档不会反过来成为主源
- Codex 专属内容不会污染通用规范层

## 推荐使用路径

如果你是第一次进入这个仓库，建议按下面顺序理解和使用：

1. 先看 `AGENTS.md`、`RULES.md`、`SOUL.md`
2. 再根据任务类型选择对应的 `agent`、`skill` 和语言 `rules`
3. 需要补充说明或翻译时，再看 `docs/`
4. 需要了解 Codex 本地运行时行为时，再看 `.codex/` 和 `.agents/`

## 子代理使用

当前实际生效、可稳定依赖的子代理入口是：

- `/agent <name> <task>`

例如：
- `/agent planner 添加用户认证`
- `/agent architect 分析当前架构`
- `/agent code-reviewer review 当前改动`
- `/agent security-reviewer 检查登录接口`

如果需要查看可用子代理名称，建议先输入：
- `/agent`
