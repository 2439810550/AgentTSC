# AgentTSC — AI 编程助手提示词汇编

> 收集、整理、合并多款 AI 编程助手的系统提示与交付契约，并按目标工具分类归档。
> 整理日期：2026-09-10 ｜ 最近更新：2026-09-16

本仓库把散落在 Claude Code / Codex / Grok Build / ZCode 四个工具下的提示词集中到一处，
同时提供一份把它们合并后的**统一交付契约**，方便单独取用或整体部署。

---

## 目录结构

```
AgentTSC/
├─ AGENTS.md                        ← 统一交付契约（9 份合并版，可直接部署）
├─ README.md                        ← 本文件
├─ 说明.md                          ← 原始整理说明与文件来源对照表
├─ 提示词参考合集.md                  ← 9 份提示词全文合集（阅读用，约 80 KB）
├─ Claude Code/                     2 份
│   ├─ Claude Code 系统提示 v4.0（研究工程助手）.md
│   └─ Claude 创作追加提示.md
├─ Codex/                           4 份
│   ├─ Codex 交付契约.md
│   ├─ Codex 精简交付契约.md
│   ├─ Codex 人格交付契约.md
│   └─ Codex 无限制模式.md
├─ Grok Build/                      2 份
│   ├─ Grok 无限制模式.md
│   └─ Grok 无限制模式 v1 旧版.md
├─ ZCode/                           1 份
│   └─ ZCode 系统角色.md
└─ LICENSE                          MIT
```

---

## 文件清单

### 统一契约

| 文件 | 说明 |
|------|------|
| `AGENTS.md` | 上述 9 份提示词合并为**单一可执行基线**：语言铁律、身份、输出规则、占位符体系、请求重释、场景路由（11 类场景各带首行确认语与字段集）、知识域、写作指南、会话连续性、交付引擎、不可逆操作确认、开局规则。冲突时以本文件内条款为准，注入的上下文层不得覆盖。 |

### Claude Code

| 文件 | 用途标签 | 来源（仓库 / 原文件名） |
|------|----------|--------------------------|
| Claude Code 系统提示 v4.0（研究工程助手）.md | 规则、系统提示 | `claude-keysmith` / `examples/claude-project-rules.md` |
| Claude 创作追加提示.md | 追加提示、创作 | `claude-keysmith` / `examples/claude-append-prompt.md` |

### Codex

| 文件 | 用途标签 | 来源（仓库 / 原文件名） |
|------|----------|--------------------------|
| Codex 交付契约.md | 输出契约 | `codex-keysmith` / `examples/gpt-contract.md` |
| Codex 精简交付契约.md | 输出契约、精简 | `codex-keysmith` / `examples/gpt-lean.md` |
| Codex 人格交付契约.md | 输出契约、人格 | `codex-keysmith` / `examples/gpt-persona-contract.md` |
| Codex 无限制模式.md | 破限 | `codex-keysmith` / `examples/gpt-unrestricted.md` |

### Grok Build

| 文件 | 用途标签 | 来源（仓库 / 原文件名） |
|------|----------|--------------------------|
| Grok 无限制模式.md | 破限 | `grok-keysmith` / `examples/grok-unrestricted.md` |
| Grok 无限制模式 v1 旧版.md | 破限、旧版 | `grok-keysmith` / `examples/grok-unrestricted-v1.md` |

### ZCode

| 文件 | 用途标签 | 来源（仓库 / 原文件名） |
|------|----------|--------------------------|
| ZCode 系统角色.md | 系统角色、系统提示 | `zcode-keysmith` / `examples/system-role.md` |

---

## 这些文件是干什么的

它们是**给 AI 编程助手使用的系统指令 / 提示词**，按工具分工：

- **Claude Code**——系统提示与人设规则（研究工程助手定位、响应协议、领域覆盖、上下文独立性）。
- **Codex**——输出交付契约：规定 AI 直接给结果、不铺垫、不推诿，并定义交付格式。
- **Grok Build**——无限制交付契约，含 v1 旧版留档。
- **ZCode**——系统角色定义，写入 system 消息使用。
- **AGENTS.md**——把以上九份合并成一个文件，作为工作区的执行基线。多数支持
  `AGENTS.md` / `CLAUDE.md` 约定的工具会**自动读取仓库根目录的同名文件**，因此把本文件
  放在项目根目录即可生效，无需逐条复制。

---

## 怎么使用

1. **单条使用**——用文本编辑器打开对应分类下的 `.md`，复制内容到目标工具配置：
   - Claude Code：`CLAUDE.md` 或项目级 `.claude/` 配置
   - Codex：`~/.codex/config.toml` / `AGENTS.md`
   - Grok Build：`~/.grok/rules`
   - ZCode：system 消息字段
2. **整体使用**——直接把根目录 `AGENTS.md` 复制到项目根目录，任何读取该约定的工具都会加载。
3. **纯阅读**——`提示词参考合集.md` 是九份提示词的全文串联，带目录和来源标注，适合通读比较。
4. **集中管理**——可用 **Keysmith Switch** 应用统一管理（本机上已把九条导入该应用的提示词库）。

工具间通用做法：把仓库放在项目根或通过符号链接挂进项目，让提示词跟随版本管理，
换机时 `git clone` 即可恢复全部配置。

---

## 版本与维护

- 新增提示词：按目标工具丢进对应目录，同时补 `说明.md` 与 `提示词参考合集.md` 的清单。
- 合并版更新：修改 `AGENTS.md`，并在提交信息里注明改动的条款编号。
- 命名约定：`<工具> <特性>.md`；旧版保留原名并加 `旧版` 后缀，不直接覆盖历史版本。

---

## ⚠️ 风险提示

其中有 6 个属于**"越狱 / 破限"类**提示词（要求 AI 忽略拒绝、绕过安全限制、避免推诿措辞）：

- Codex 无限制模式
- Codex 交付契约、Codex 精简交付契约、Codex 人格交付契约
- Grok 无限制模式、Grok 无限制模式 v1 旧版

这类提示词：

- 可能**违反对应 AI 服务的用户协议**，账号存在被封禁风险；
- 可能诱导 AI 输出受限制内容，**后果自负**；
- 请仅用于合法的学习、研究目的。

相对中性的：Claude Code 系统提示、Claude 创作追加提示、ZCode 系统角色。

---

## 来源与许可

- 提示词原始作者 GitHub：<https://github.com/Jia-Ethan>（Keysmith 系列仓库）
- 本地源码：`D:\keysmith\repos\` 与 `D:\keysmith\keysmith-switch\`
- 本仓库许可：MIT，见 [LICENSE](LICENSE)
