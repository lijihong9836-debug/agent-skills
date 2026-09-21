# Skill 同步核验（2026-09-21）

本次从远端 `main` 的 `892fb762dbde69bb6016f2dbdd46bb02bc574caf` 创建独立分支，检查 2026-09-14 至 2026-09-21 会话中显式引用的 16 个本地 Skill。会话引用仅用于筛选候选，不代表每个流程均完整执行。

## 发布范围

新增 9 个已有本地 Skill 的公开镜像，分发目录由 17 个增至 26 个：

- `agent-reach`
- `codebase-design`
- `diagnosing-bugs`
- `neat-freak`
- `no-negative-echo`
- `officecli`
- `playwright`
- `prototype`
- `research`

42 个来源文件与对应上游 Git 对象逐一匹配，文本比较统一 CRLF/LF。41 个分发文件与本地来源 SHA-256 一致；`agent-reach/references/dev.md` 仅清理第 3 行的一个行末空格。补入 8 份上游许可证和 OfficeCLI 的 NOTICE；`playwright` 已自带许可证及 NOTICE。来源提交和许可类型见[来源清单](third-party-skills.md)。`agent-reach`、`neat-freak` 采用可核实的历史版本，其余新增项与本次核验时的上游提交一致。

README 增补目录、依赖说明和固定版本定位，来源清单区分本次收录与此前统计快照。

## 候选处置

| 候选 | 处置 |
| --- | --- |
| `pdf`、`storage-analyzer` | 本地与现有镜像一致，保持原状。 |
| `craft-codex-prompts`、`credit-negative-monitoring` | 本地差异属于旧配套名称及项目工具依赖表述，保留远端现行名称和可选集成说明。 |
| `writing-great-skills` | 远端已采用后继 `writing-for-agents`，保留当前入口。 |
| `codex-chatgpt-skill` | 来源仓库已核实，但未找到许可证，不复制。 |
| `weekly-meeting-materials` | 含业务专用内容，保持本地使用。 |

本次未变更另一个分支上的 eli5 PR。

## 验证结果

- 26 个目录的 UTF-8 YAML、必需字段、名称对应关系及已有界面元数据检查通过。
- `quick_validate.py`：17 个直接通过，9 个返回兼容性限制。新增的 9 个目录中，8 个通过；`agent-reach` 的上游自定义 `triggers` 字段不在校验器允许范围。其余 8 个是既有镜像中的 `disable-model-invocation` / `argument-hint` 字段或中文名称限制。保留上游内容，未将这些结果记为直接通过；不同宿主的激活兼容性仍待验证。
- 新增来源文件、分发副本及许可证哈希核对通过。
- 新增包和本次仓库文档的实际 Markdown 文件链接检查通过。
- 新增 Python 脚本语法检查、两个 Bash 脚本语法检查通过。
- `no-negative-echo` 辅助程序的正常文本、命中正文、命中文件名、不可见字符 4 类合成输入返回预期结果，输出未泄露测试词。
- `diagnosing-bugs` 交互模板通过合成输入检查；`playwright` 包装脚本通过模拟 npx 的会话默认值、显式会话及含空格参数检查。未调用真实外部平台。
- 发布范围内的凭据、私钥、机器路径、业务上下文及备份/缓存文件扫描未发现命中；`git diff --check` 通过。

## 验证边界

本次验证覆盖来源、许可、分发完整性、静态结构及辅助脚本。未执行真实账号登录、Office 文档操作、浏览器端到端任务，未验证全部 Skill 在其他设备或宿主中的激活和工作流行为。复制 Skill 不会安装其外部依赖或配置账号。

变更仅发生在独立发布副本。本地已安装 Skill、业务工作区、全局配置、记忆和定时任务均未修改。
