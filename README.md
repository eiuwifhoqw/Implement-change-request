# 个人交付规范云端知识库（GitHub 公开规则源与镜像）

## 定位

这个仓库是**单一事实源的镜像**，存放跨任务复用的项目初始化规范、交付标准、自检清单和纠偏台账。它提供版本历史、跨设备访问和可审计的规则变更记录。

**它不自动向 WorkBuddy 会话注入上下文。** 新会话真正默认生效的是本机两层：用户级 `MEMORY.md` 的常开锚点 + 用户级技能包 `~/.workbuddy/skills/project-delivery-contract/`。本仓库的文件与它们保持同源文本，通过显式同步保持一致。

## 三层架构

| 层 | 位置 | 生效方式 | 职责 |
|---|---|---|---|
| L1 常开锚点 | 本机用户级 `MEMORY.md` | 每次会话自动注入 | 5–8 条铁律 + 「开工前加载契约」指令 |
| L2 技能 + 模板 | 本机 `~/.workbuddy/skills/project-delivery-contract/` | 开工前加载 | 完整规则、5 份模板、纠偏台账 |
| L5 云端镜像 | 本仓库 | 需显式读取 | 版本历史、跨设备、规则变更评审 |

L3 模板骨架、L4 纠偏闭环是 L2 内部的机制，不是独立存储位置。

## 文件索引

| 文件 | 作用 | 对应 GitHub 实践 |
|---|---|---|
| `AGENTS.md` | 给支持该开放格式的 agent 的稳定入口，内容极简 | AGENTS.md 开放格式 |
| `.github/copilot-instructions.md` | 全仓库常开指令，自动加入每次请求 | 仓库级自定义指令 |
| `.github/ISSUE_TEMPLATE/task-intake.yml` | 结构化开工单，9 项必填信息 | Issue forms 的 `validations.required` |
| `.github/ISSUE_TEMPLATE/config.yml` | 禁用空白起手 | `blank_issues_enabled: false` |
| `.github/PULL_REQUEST_TEMPLATE.md` | 规则升级时的 G1–G8 勾选复核 | PR 模板的 Definition of Done |
| `CONTRIBUTING.md` | 纠偏回写与版本升级流程 | 贡献指南 |
| `docs/CORRECTIONS.md` | 纠偏台账（与本机同源） | 决策记录 / ADR |
| `CHANGELOG.md` | 规则版本差异 | 变更日志 |

## 同步约定

- 本机技能包为主本，本仓库为镜像；改动先落本机，再同步此处。
- 每条规则变更以一次 PR 呈现，PR 模板中的 G1–G8 勾选结果即为变更复核记录。
- 规则版本写在 `CHANGELOG.md`，与本机 `CHANGELOG.md` 同源。
- 仓库当前为公开（用户 2026-11-13 设置）；内容只含规范与偏好，不含账号、密钥、业务数据。
- 用户另指定 `eiuwifhoqw/Implement-change-request` 为回答要求源，规则文件约定为根目录 `ANSWER-RULES.md`；本镜像的 `ANSWER-RULES.md` 与其同源，仓库不可达时以本机副本为准。
- 跨设备使用说明见 `CROSS-DEVICE.md`；本仓库的 `AGENTS.md` 同时作为跨工具开放格式的规则入口。

## 技术栈边界

本仓库所有文件技术栈中立：不含语言、框架、运行时、构建工具、包管理器的约定。涉及工具链的位置留空为槽位，由具体任务另行指定。
