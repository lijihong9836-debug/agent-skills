# Skill 同步与更新核验（2026-09-08）

本次在远端 `main` 的 `4abe5e0` 基础上检查全部 16 个已有 Skill，并加入 `credit-negative-search-flow`，完成后共 17 个分发目录。

## 本次变更

| 范围 | 处理结果 |
| --- | --- |
| `credit-negative-monitoring` | 同步前正文与本地最新版一致；补充配套技能和可选项目工具的定位说明，保留金额门槛、主体范围、证据要求、列示、姓名脱敏、结论及版式规则。 |
| `credit-negative-search-flow` | 新增主文件、界面元数据、联网策略、证据对账参考；将机器绝对路径改为同级技能引用，将项目工具引用改为明确的可选集成。 |
| `ask-matt`、`code-review`、`handoff`、`setup-matt-pocock-skills`、`to-spec`、`to-tickets`、`wayfinder` | 更新到 Matt Pocock 上游当前固定提交；包含阶段边界参考、新的流程路由及前置设置提示。 |
| `writing-for-agents` | 按上游替换 `writing-great-skills`，同时更新 `craft-codex-prompts` 和仓库文档中的引用。 |
| `domain-modeling`、`implement` | 正文已与上游一致；与其他 Matt Pocock 镜像一起补充目录内 `LICENSE.txt`。 |
| `pdf`、`磨刀石` | 最新上游提交与原记录一致，实时核对源文件后保持不变。 |
| `storage-analyzer` | 与本地当前版本一致，保持不变。 |
| `craft-codex-prompts` | 与本地当前版本一致，仅调整写作技能的配套引用。 |
| `karpathy-guidelines` | 复核现有结构与内容；没有本地副本或已登记的独立上游更新来源，保持现状，不宣称已核对外部最新版本。 |
| README 与来源清单 | README 列全 17 个 Skill，说明成对安装及上游套件依赖；更新固定来源与许可证位置。 |

## 来源与范围

- Matt Pocock：[固定提交 `3cca18b`](https://github.com/mattpocock/skills/tree/3cca18b368ae95cdbdebbff572ccafa662551015)。10 个分发目录与该提交逐文件核对，新增的目录内许可证与上游 MIT 文件一致。
- OpenAI PDF：[固定提交 `49f948f`](https://github.com/openai/skills/tree/49f948faa9258a0c61caceaf225e179651397431/skills/.curated/pdf)。4 个上游文件的 Git 对象哈希一致。
- 磨刀石：[固定提交 `c1fdc74`](https://github.com/crazyooo/modaoshi/tree/c1fdc74f55541f49d5fcfd7ca40fc7338f99ecdb/skills/磨刀石)。2 个上游文件的 Git 对象哈希一致，保留既有许可证副本。
- 文本比较统一 CRLF/LF；本地换行差异未作为功能更新。
- 两个授信 Skill 的分发包包含规则与参考文件；项目业务工具、机构映射、监测工作簿、历史证据和备份不属于分发包。此次只更新 GitHub 仓库副本，本地已安装 Skill 和业务工作区保持原状。

## 验证

- 全部 17 个 Skill 的 UTF-8、YAML、必需字段、目录名对应关系及界面元数据检查通过。
- 全部目录均运行 `quick_validate.py`：9 个直接通过；7 个 Matt Pocock 镜像因本机校验器不识别 `disable-model-invocation` / `argument-hint` 返回失败；`磨刀石` 因其中文上游名称返回失败。上述 8 个结果属于已确认的校验器限制，未改写上游元数据来隐藏结果。
- 仓库内实际 Markdown 文件引用检查通过；模板中的示例链接与面向使用方项目的路径按用途区分。Matt Pocock 套件中的其他技能依赖按 README 从上游取得。
- 10 个 Matt Pocock 镜像及其许可证核对通过；PDF、磨刀石实时上游对象核对通过。
- 现有 3 个 Python 脚本编译通过；本次没有修改可执行脚本。
- 凭据、私钥、机器路径和备份文件扫描完成；唯一命中为 Windows 参考中的通用 `C:\Users\<u>\` 示例，人工复核为占位符。
- `git diff --check` 通过；发布前仅暂存本次已审阅的 Skill 与仓库维护文件。

静态流程复核覆盖 DM 指定来源、已有证据补强、存放同业具体分支行边界和访问缺口处理。原有“缺口不等于未发现”、DM 与官网证据分别标识、历史范围不扩张等约束保留。

本次未运行真实业务监测、工作簿回写或每个第三方 Skill 的交互流程，也未验证其在所有宿主中的激活行为。全局配置和定时任务未修改。
