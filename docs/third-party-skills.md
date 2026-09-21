# 第三方技能来源与安装清单

本清单记录各次收录时的来源与许可证。下方“2026-09-08 收录快照”按当时最近 30 个任务摘要统计，次数不等同于精确调用次数；2026-09-21 新增项按近一周会话中的显式 Skill 文件引用筛选，并逐文件核对公开上游。

## 复制规则

- 个人编写的 Skill 可直接维护在本仓库。
- 已核实为 MIT 的 Matt Pocock Skills，复制时保留上游许可证，仓库级许可证副本位于 [`docs/third-party/mattpocock-skills/LICENSE`](third-party/mattpocock-skills/LICENSE)，每个分发目录同时携带 `LICENSE.txt`，便于单独安装。
- OpenAI 的 `pdf` 和 `playwright` Skill 保留各自随包提供的 Apache 2.0 许可证；`playwright` 同时保留 `NOTICE.txt`。
- 未声明许可证、专有许可证或业务私有内容不复制源码，只记录来源或继续使用原安装。
- 根目录的 MIT 许可证不自动覆盖第三方镜像；第三方文件以其上游许可证为准。

## 2026-09-21 新增镜像

以下来源文件与对应固定提交逐一匹配，文本比较统一 CRLF/LF。每个目录均附带 `LICENSE.txt`；OfficeCLI 和 Playwright 同时保留上游 NOTICE。分发副本保留本地已使用版本的内容，仅清理 `agent-reach/references/dev.md` 第 3 行的一个行末空格。

| Skill | 固定来源 | 许可证 |
| --- | --- | --- |
| [`agent-reach`](../skills/agent-reach/) | [Panniantong/Agent-Reach @ e4c31b2](https://github.com/Panniantong/Agent-Reach/tree/e4c31b29b1828d196e2930cca9d5f7dfb154f251/agent_reach/skill) | MIT |
| [`codebase-design`](../skills/codebase-design/) | [mattpocock/skills @ c55ee46](https://github.com/mattpocock/skills/tree/c55ee46073ed923f86ce59a5eb3b6d895095d1b7/skills/engineering/codebase-design) | MIT |
| [`diagnosing-bugs`](../skills/diagnosing-bugs/) | [mattpocock/skills @ c55ee46](https://github.com/mattpocock/skills/tree/c55ee46073ed923f86ce59a5eb3b6d895095d1b7/skills/engineering/diagnosing-bugs) | MIT |
| [`neat-freak`](../skills/neat-freak/) | [KKKKhazix/khazix-skills @ d4e43c9](https://github.com/KKKKhazix/khazix-skills/tree/d4e43c91f16dcd859748c1d71ec7d8aa1ebb4694/neat-freak) | MIT |
| [`no-negative-echo`](../skills/no-negative-echo/) | [LB623/no-negative-echo @ eba9f1d](https://github.com/LB623/no-negative-echo/tree/eba9f1d2b4c19e699786a49427189988ad6d8d65/no-negative-echo) | MIT |
| [`officecli`](../skills/officecli/) | [iOfficeAI/OfficeCLI @ dced0d7](https://github.com/iOfficeAI/OfficeCLI/tree/dced0d74ff85b1fef0b777efcdb637c2c4ef8a6e/skills/officecli) | Apache 2.0 |
| [`playwright`](../skills/playwright/) | [openai/skills @ 49f948f](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/playwright) | Apache 2.0 |
| [`prototype`](../skills/prototype/) | [mattpocock/skills @ c55ee46](https://github.com/mattpocock/skills/tree/c55ee46073ed923f86ce59a5eb3b6d895095d1b7/skills/engineering/prototype) | MIT |
| [`research`](../skills/research/) | [mattpocock/skills @ c55ee46](https://github.com/mattpocock/skills/tree/c55ee46073ed923f86ce59a5eb3b6d895095d1b7/skills/engineering/research) | MIT |

`agent-reach` 和 `neat-freak` 对应已核实的历史版本；上游已有后续改动，此处不表示已升级到最新版本。依赖工具和宿主能力仍须在安装设备上核对。完整范围与验证结果见 [2026-09-21 维护记录](maintenance-20260921.md)。

## 2026-09-08 收录快照

| Skill | 近期任务摘要 | 上游来源 | 许可状态 | 本仓库处理 |
| --- | ---: | --- | --- | --- |
| [`implement`](../skills/implement/) | 17 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/implement) | MIT | 已复制，保留上游许可证 |
| [`code-review`](../skills/code-review/) | 8 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/code-review) | MIT | 已复制，保留上游许可证 |
| [`handoff`](../skills/handoff/) | 6 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/handoff) | MIT | 已复制，保留上游许可证 |
| [`wayfinder`](../skills/wayfinder/) | 4 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/wayfinder) | MIT | 已复制，保留上游许可证 |
| [`pdf`](../skills/pdf/) | 4 | [openai/skills](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/pdf) | Apache 2.0 | 已复制，保留随包许可证 |
| `pptx` | 4 | 本机随包 Skill，未找到可公开镜像的源码入口 | Proprietary | 不复制源码 |
| [`to-tickets`](../skills/to-tickets/) | 3 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-tickets) | MIT | 已复制，保留上游许可证 |
| [`ask-matt`](../skills/ask-matt/) | 2 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/ask-matt) | MIT | 已复制，保留上游许可证 |
| [`to-spec`](../skills/to-spec/) | 2 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/to-spec) | MIT | 已复制，保留上游许可证 |
| [`setup-matt-pocock-skills`](../skills/setup-matt-pocock-skills/) | 2 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/setup-matt-pocock-skills) | MIT | 已复制，保留上游许可证 |
| [`domain-modeling`](../skills/domain-modeling/) | 2 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/engineering/domain-modeling) | MIT | 已复制，保留上游许可证 |
| [`writing-for-agents`](../skills/writing-for-agents/) | 手动同步 | [mattpocock/skills](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015/skills/productivity/writing-for-agents) | MIT | 已复制，保留上游许可证 |
| [`磨刀石`](../skills/磨刀石/) | 手动同步 | [crazyooo/modaoshi](https://github.com/crazyooo/modaoshi/tree/c1fdc74f55541f49d5fcfd7ca40fc7338f99ecdb/skills/磨刀石) | MIT | 已复制，保留上游许可证副本 `skills/磨刀石/LICENSE.txt` |

`craft-codex-prompts` 和 `karpathy-guidelines` 属于本仓库已有的个人 Skill，不计入上述第三方镜像表。

## 安装方式

优先从上游来源安装，以便接收上游更新：

```powershell
python "$env:USERPROFILE\.codex\skills\.system\skill-installer\scripts\install-skill-from-github.py" `
  --url https://github.com/mattpocock/skills/tree/main/skills/engineering/implement
```

需要从个人镜像安装时，将 URL 换成：

```text
https://github.com/lijihong9836-debug/agent-skills/tree/main/skills/<skill-name>
```

安装后应重新启动 Codex，或显式调用 `$<skill-name>`；对于 `pptx`，继续使用已有的专有随包版本，不从本仓库安装源码镜像。

## 验证说明

- 2026-09-08 重新核对 Matt Pocock、OpenAI 和磨刀石的上游版本。Matt Pocock 镜像更新至表内固定提交；比较文本时统一 CRLF/LF，另加的 `LICENSE.txt` 与上游 MIT 许可证一致。OpenAI `pdf` 和磨刀石上游提交未变，当前镜像保持一致。
- 对全部分发目录执行本机 `quick_validate.py`，并单独核对 UTF-8 YAML、目录名、引用及许可证；具体结果见本次维护记录。
- 部分 Matt Pocock 镜像保留了上游当前的 `disable-model-invocation` 或 `argument-hint` 元数据；本机旧版 `quick_validate.py` 会把这些合法字段误报为未知字段，因此没有为了通过旧校验器而改写第三方源码。
- 所有镜像的 UTF-8 YAML frontmatter、`name`、`description` 和目录名匹配关系均已单独校验。

## 上游替换

2026-09-08 按上游当前目录将 `writing-great-skills` 更新为 `writing-for-agents`，包含 `SKILL-MECHANICS.md`。仓库内的入口和配套引用使用新名称；既有安装由使用者按新名称安装，旧版仍可通过 Git 历史追溯。
