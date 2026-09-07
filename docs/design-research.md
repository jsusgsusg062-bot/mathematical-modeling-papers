# 参考项目与设计取舍

调研日期：2026-09-07。阅读了下列具体文件，以下优劣是相对于“用户操作知网、逐轮教学、数模论文拆解”的适配判断，不是对项目总体质量排名。没有运行第三方自动化代码，未验证其所有语法与兼容性。

| 参考项目与已读文件 | 可借鉴之处 | 对本需求的局限 | 本项目的取舍 |
|---|---|---|---|
| [turbin/cnki-search](https://github.com/turbin/cnki-search/blob/main/SKILL.md) | 字段、逻辑、检索式校验组织清楚 | 集中在语法，缺少按用户反馈推进；部分字段语义与排除策略写得绝对，不能当知网各版本规范 | 保留字段与逻辑分层；按当前入口帮助核对复杂语法，不默认大范围NOT排除 |
| [cookjohn/cnki-skills](https://github.com/cookjohn/cnki-skills/blob/master/skills/cnki-advanced-search/SKILL.md) | 明确区分行内/行间条件、字段、来源和时间 | 依赖Chrome DevTools及旧界面选择器；实际目标是自动操作 | 借鉴条件分解；转换成人工操作表，去掉选择器与自动化依赖 |
| [bytedance/deer-flow](https://github.com/bytedance/deer-flow/blob/main/skills/public/academic-paper-review/SKILL.md) | 主张与证据对应，方法、实验、公平基准和可复现性检查 | 以审稿为主，包含录用意见、评分和固定优缺点数量；默认外部定位检索较重 | 保留原文定位与方法检查；改为理解和迁移，不输出录用评分、不凑缺点 |
| [yananlong/codex-skills](https://github.com/yananlong/codex-skills/blob/main/research/research-systematic-literature-review/SKILL.md) | 区分快速探索和系统综述，记录覆盖、来源、停止理由与技能职责 | 系统综述的审计、语料冻结、PRISMA及多技能依赖超出备赛探索需求 | 保留轻量状态记录、停止条件及交接；不要求完整系统综述流程 |

## 可复查的文件版本

本轮GitHub读取返回的文件blob SHA（不是仓库commit SHA）：

- turbin/cnki-search，`SKILL.md`：`dc23e54a2e1a95a08ca5b225e19bc9c97dcccb36`
- cookjohn/cnki-skills，`skills/cnki-advanced-search/SKILL.md`：`431b00b9e1aa9ec95be385fbebc395199a27c90a`
- bytedance/deer-flow，`skills/public/academic-paper-review/SKILL.md`：`165321cb6ce032f943ec50d8537431e3552e7785`
- yananlong/codex-skills，`research/research-systematic-literature-review/SKILL.md`：`8addfa439092a54b5f12019976a6c9380edc1160`

这些项目是思路参考。仓库中的指令为独立编写，没有复制第三方实现、脚本或整段技能文本，也不把第三方的兼容性声明当成本项目实测结果。

## 用户确认的设计

1. 不操作知网，由用户检索并反馈。
2. 逐轮推进，根据已有材料跳转，避免机械重搜。
3. 论文先讲整体，再解释关键公式和方法，代码不默认生成。
4. 仅论文即可拆解；有赛题才增加针对性迁移判断。
5. 检索初筛与全文分析分工，允许带着具体缺口返回补搜。

## 对原始教学流程的修正

- 任务先行：区分连续值预测、分类、优化和评价，避免把不同输出的模型混在同一效果榜。
- 方法分工：变量筛选、模型、参数估计、求解算法和解释方法分别标记，按实际输入输出连接。
- 证据范围：题名、摘要、AI概括与全文分开；用户确认文献真实后不重复存在性验证。
- 效果条件：记录验证窗口、信息可用性、基准、指标口径，不把拟合度当未来预测能力。
- 决策边界：文献筛出可尝试的路线；本题结果未产生前不预设谁精度最高。

方法检查的背景参考：
- [scikit-learn：交叉验证与测试集隔离](https://scikit-learn.org/stable/modules/cross_validation.html)
- [Forecasting: Principles and Practice：回归预测的未来输入](https://otexts.com/fpp3/forecasting-regression.html)

## 截图与论文的作用

高级检索参考依据用户提供的2026-09-07截图：多行条件、字段下拉、行间逻辑、行内运算提示、时间和文献类型；未显示的专业检索语法不予推定。CNKI AI截图只证明相关控件可见，不证明功能质量或权限。

用户提供的《基于多元回归和GM的新能源汽车保有量预测》用于验证方法链和效果提取。它是阅读练习，不作为所有论文都应采用的模型范式。
