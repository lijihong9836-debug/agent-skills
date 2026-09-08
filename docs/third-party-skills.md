# 第三方技能来源与安装清单

本清单按最近 30 个任务摘要统计。次数表示该技能出现在多少个任务摘要中，不等同于精确的单次调用次数；本次纳入阈值为至少 2 个任务摘要。

## 复制规则

- 个人编写的 Skill 可直接维护在本仓库。
- 已核实为 MIT 的 Matt Pocock Skills，复制时保留上游许可证，仓库级许可证副本位于 [`docs/third-party/mattpocock-skills/LICENSE`](third-party/mattpocock-skills/LICENSE)，每个分发目录同时携带 `LICENSE.txt`，便于单独安装。
- OpenAI 的 `pdf` Skill 保留其随包提供的 Apache 2.0 许可证，位于 [`skills/pdf/LICENSE.txt`](../skills/pdf/LICENSE.txt)。
- 未声明许可证、专有许可证或业务私有内容不复制源码，只记录来源或继续使用原安装。
- 根目录的 MIT 许可证不自动覆盖第三方镜像；第三方文件以其上游许可证为准。

## 高频技能

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
