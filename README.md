# 审计底稿助手

`audit-workpaper-assistant` 是一个 Agent Skill（智能体技能），从提问和附件判断需要做哪些工作，覆盖存货流程与穿行、Excel 底稿与抽样、租赁合同及 ASC 842 重算。资料分批到达时，先交可核实的结果，再把需要用户确认的项目口径和需要客户补交的证据分别列出。收到补件后，按事项更新已做工作及剩余缺口。

v0.3.0 根据 1,029 条去重后的海外公开审计情形补充了任务识别和例外处理规则。案例主要来自 Reddit 的公开原帖及评论，记录的是从业者或被审方的自述。

## 从 GitHub 读取或安装

在 GitHub 打开下方的技能正文，点击 **Raw** 即可取得直读链接。也可使用下列地址格式。`<ref>` 可填分支名或提交哈希，使用提交哈希可固定版本。

```text
https://raw.githubusercontent.com/<owner>/audit-workpaper-assistant/<ref>/audit-workpaper-assistant/SKILL.md
```

在支持链接读取的客户端中，将实际 Raw 链接填入下面的消息并发送。

> 请读取这个链接的完整 `SKILL.md` 正文，并在本会话按它的说明协助我。先返回技能名、版本号和首次调用回执。若无法读取，请告诉我。链接为 `<SKILL.md 的 Raw 链接>`。

打不开链接时，可从 GitHub 文件页打开 **Raw**，保存为 `SKILL.md` 后上传到当前对话。支持本地技能安装的客户端可解压仓库中的 `audit-workpaper-assistant-v0.3.0.zip`，将整个 `audit-workpaper-assistant` 文件夹放入该客户端的技能目录。

安装后新开会话，只发「请调用 `audit-workpaper-assistant`，返回首次调用回执」，先不提供文件或链接。如果有技能列表或调用记录，同时检查是否出现 `audit-workpaper-assistant`。本版回执为 `AUDIT-WORKPAPER-READY-03`。 [Agent Skills 客户端加载说明](https://agentskills.io/client-implementation/adding-skills-support)

## 验收与迭代

- [技能正文](audit-workpaper-assistant/SKILL.md) 是唯一运行入口。它包含完整规则，可单独使用。
- [18 轮验收题](TESTS.md) 覆盖订单错版本、总体版本与缺件样本、租赁付款与期初桥接、盘点观察缺失与截图不可读。其中 7 题只给用户可能说的原话，检查模型会做什么。题目均为虚构，可分别复制到新会话。实际行为以用户的客户端测试为准。
- 用户发现反复返工的情形时，可用一组脱敏材料记录问题。保留原提问、实际回答、期望的下一步和一段必要的项目口径。把这个例子补成回归题，再用原题检查修订前后的区别。

## 工作范围与标准

正式程序和结论采用该项目适用的审计框架、报告准则、期间版本及项目方法。开发时核对的官方入口包括 [PCAOB 审计证据 AS 1105](https://pcaobus.org/oversight/standards/auditing-standards/details/AS1105)、[审计记录 AS 1215](https://pcaobus.org/oversight/standards/auditing-standards/details/AS1215)、[审计抽样 AS 2315](https://pcaobus.org/oversight/standards/auditing-standards/details/AS2315)、[存货审计 AS 2510](https://pcaobus.org/oversight/standards/auditing-standards/details/AS2510)、[IAASB 准则目录](https://www.iaasb.org/standards-pronouncements) 和 [FASB Accounting Standards Codification](https://asc.fasb.org/) 中的 Topic 842。
