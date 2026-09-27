# painpoint-discovery

让 AI 从真实用户反馈中发现痛点，判断下一步是否值得投入，并把需求交给开发 AI。

[English](README.en.md) · [Skill 入口](skills/painpoint-discovery/SKILL.md) · [合成示例](examples/synthetic-research.md) · [测试方法](evals/rubric.md) · [发布清单](RELEASE-CHECKLIST.md)

**真实试运行：** [研究型学生案例](examples/research-students-desk-pilot.md) 找到了文献笔记整理的公开求助，也找到现成的矩阵工具，因此结论是先试现有方案。找到痛点不等于应该新建产品。

这是一个按需执行的需求调研 skill 文件包，不是常驻采集系统。它指导宿主 AI 使用已有的搜索、浏览器或资料读取工具；不附带账号、采集服务、自动开发或部署后台。

## 能做什么

| 你有什么 | 它做什么 | 输出 |
|---|---|---|
| 人群或领域，还没有产品想法 | 找具体任务中的障碍，比较现有替代方案 | 痛点候选、来源证据、排序理由 |
| 产品想法、Demo 或已有产品 | 检索支持与反对证据，核对当前情况 | 继续验证／补证据／暂不开发的判断 |
| 已有调研材料，准备开发 | 检查证据缺口，限定最小方案 | MVP、输入输出、异常流程、验收与开发提示词 |

每个核心需求都有 **证据 E → 痛点 P → 需求 R → 验收 A** 的追踪关系。模型提出的设计会单独标记，不冒充用户已经验证的需求。

它区分个人提效、开源工具与商业产品；不把“没有付费意愿证据”当作所有项目的否决条件。点赞、真实使用、实际付费也分别判断。

发布版进一步记录来源与目标人群的匹配程度、日期依据，以及已有工具究竟只是文档声称支持，还是已完成真实任务。相邻痛点不会被合并成一个虚假的共同需求。

## 开始使用

将 `skills/painpoint-discovery/` 整个文件夹复制到宿主支持的技能目录，保留 references、assets 和 agents。没有技能发现机制的工具可以直接读取 SKILL.md 及其相对引用，但实际能力取决于宿主，不保证自动触发。

Codex 本地手动安装：可选项目的 `.agents/skills/` 或个人的 `~/.agents/skills/`。例如在本仓库根目录执行以下命令，仅在目标不存在时安装，避免覆盖已有版本：

```sh
mkdir -p "$HOME/.agents/skills"
if [ -e "$HOME/.agents/skills/painpoint-discovery" ] || [ -L "$HOME/.agents/skills/painpoint-discovery" ]; then
  echo "目标已存在，请先比较版本；本次未覆盖。"
else
  cp -R skills/painpoint-discovery "$HOME/.agents/skills/painpoint-discovery"
fi
```

安装路径依据 [OpenAI 官方技能文档](https://learn.chatgpt.com/docs/build-skills)，核对日期 2026-09-27。若未显示，可重启 Codex。此包未自动安装到你的环境，也未在所有宿主实测安装。

在支持 `$skill-name` 的宿主中调用：

```text
使用 $painpoint-discovery。
发现模式：面向中文自由职业设计师，寻找交付与客户沟通中值得用软件解决的痛点。
我是独立开发者，最多投入两周做原型。先比较至多三个问题，给出来源和反证。
```

```text
使用 $painpoint-discovery。
验证模式：我想做一个把会议记录转成客户报价的工具，面向小型设计工作室。
请检查他们现在怎么做、现有工具哪里不足，先别假设必须用 AI 或必须做新产品。
```

```text
使用 $painpoint-discovery。
交接模式：只基于我提供的访谈和试用记录，生成最小原型需求及验收标准。
缺少证据的部分标为假设；不要直接启动开发或部署。
```

默认兼顾中英文查询，按目标市场调整；不将一个地区的反馈外推到另一个地区。未指定投入时，先筛至多三个问题、进行发现与反证两轮检索。它可以得出“没有足够证据推荐任何机会”。

## 需要什么能力

- 实时调研：宿主提供可用搜索、网页读取、API 或浏览器能力；没有固定付费依赖。
- 资料分析：能读取用户提供的文件或文本。
- 文件输出：宿主支持写文件时可保存报告；也可直接在对话输出。

网站登录限制或访问失败会成为报告中的证据缺口。没有联网工具时会改为明确标记的“仅基于提供材料”分析。它不承诺访问所有社交平台，不把搜索摘要当成已读原文。

## 输出与边界

简短任务可以只输出一份报告；复杂任务可分为调研报告、证据台账和开发交接。模板包含检索范围、事实与推断、替代方案、反证、验证实验和停止条件。产品需要 AI 时再讨论错误率、成本与复核；AI 编程不意味着产品必须调用模型。

这个 skill 不保证找到可盈利产品。公开评论不是代表性抽样，合成案例不是市场验证，原型可用也不等于有人愿意付费。招募文案和开发提示词是草稿产物，不等于已经联系用户或执行开发。

## 文件与验证

```text
skills/painpoint-discovery/
  SKILL.md
  agents/openai.yaml
  references/research-method.md
  references/decision-rules.md
  assets/report-template.md
  assets/handoff-template.md
examples/synthetic-research.md
evals/scenarios.json
evals/rubric.md
evals/results.md
evals/runs/
```

[发布回归](evals/release-results.md) 中，新旧版本均通过六项检查，不据此声称能力提升。

[测试结果](evals/results.md) 区分结构校验、合成场景试运行与未覆盖能力。可按 [评分说明](evals/rubric.md) 在独立上下文重复测试。初版不声称相对基线有统计显著提升。

## 发布与授权状态

公开仓库：[EmilyJYQ/painpoint-discovery](https://github.com/EmilyJYQ/painpoint-discovery)。许可证尚待所有者选择，目前未授予开源许可；公开可见不代表授予修改、分发或商用许可。发布检查见 [清单](RELEASE-CHECKLIST.md)。仓库中不包含参考案例截图、私人访谈或第三方 skill 源码。

工作流受到用户提供的“AI 产品需求调研”演示案例启发；本包独立编写指令和模板，没有访问或复制原案例的 skill 源码。需要保留或补充公开致谢时，由发布者确认可公开的作者名称与链接。
