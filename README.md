# 飞书汇报 · feishu-report

用于实验报告、模型对比和结果分析的 Agent Skill：首段用数字支撑核心判断，关键表图紧邻结论；发布前逐项自检，发布后回读验收，不通过不得宣称完成。

## 安装

需要 Git，以及支持 `SKILL.md` 的 Agent。对于读取 `~/.agents/skills/` 的 Agent，全新安装：

```bash
mkdir -p ~/.agents/skills
git clone https://github.com/CollaalloC/feishu-report.git ~/.agents/skills/feishu-report
```

如果目标目录已存在，不要覆盖已有内容。使用其他技能目录的 Agent 时，将仓库克隆到对应目录下的 `feishu-report/`。安装后刷新技能列表或开启新会话。

OMP 可用以下命令检查发现结果：

```bash
omp skill list --json
```

列表中应出现 `name: feishu-report`。本仓库无需构建，也不包含可执行安装脚本。

## 使用

在支持技能调用的 Agent 中直接描述任务：

> 用 feishu-report（飞书汇报）整理这份实验报告，结论先行，保留关键数据和图表。

需要发布时明确说明：

> 用 feishu-report 整理这份模型对比报告，并发布到飞书。

更新已有报告时提供文档链接：

> 用 feishu-report 整理这份飞书报告，必要时整体重排正文，保留未受影响的数值表、配图和视频 block。

Agent 可以根据技能名称或描述检索本技能；实际触发方式取决于所用 Agent。

## 能力与依赖

- **撰稿与精简**：读取用户提供的报告、结果和图表，组织核心结论、关键数据、可视化证据及必要建议；不需要飞书账号。
- **发布与更新**：需要另行安装 `lark-doc`、`lark-drive` 及其依赖，配置其所需的 `lark-cli` 身份和访问权限。本技能仅规定写作和交付规则，不实现飞书 API 客户端。
- `SKILL.md` 中的 `../lark-doc/SKILL.md`、`../lark-drive/SKILL.md` 指向安装后同级的配套技能，不是本仓库内的文件。缺少配套技能时可以撰稿，不能将其描述为已完成云端发布。
- 整理报告不自动重跑实验、不改变原始数据，也不自动修改文档的共享范围。

完整规范见 [SKILL.md](SKILL.md)。中文显示配置位于 [agents/openai.yaml](agents/openai.yaml)。

## 版本与共享

GitHub 保存可克隆的技能源文件；本地已安装副本和其他共享副本不会因仓库更新而自动同步。仓库不包含实验数据、模型权重、账号凭据或其他配套技能的源码。

## 许可证

[MIT](LICENSE)，Copyright (c) 2026 CollaalloC。
