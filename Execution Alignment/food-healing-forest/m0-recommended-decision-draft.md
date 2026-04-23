# 食愈森林 M0 决策参考样稿

## 1. 使用说明

- 本文档不是正式会议纪要，而是基于当前材料整理出的 `M0` 推荐决策样稿。
- 作用是帮助 `M0 阻塞项确认会` 更快收口，避免会议现场从空白模板开始组织语言。
- 正式结论仍以 [m0-decision-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-decision-template.md>) 回写版本为准。

## 2. 建议前提

- 当前推荐结论基于以下材料：
  - [reminder-capability-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/reminder-capability-decision.md>)
  - [record-state-machine-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/record-state-machine-draft.md>)
  - [privacy-sensitive-data-boundary-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/privacy-sensitive-data-boundary-decision.md>)
- 当前目标不是把所有细节一次定死，而是把会直接阻塞 `M1` 的关键口径锁住。

## 3. 推荐会议总结论

- 总体结论：`Conditional Go`
- 是否允许进入 `M1 设计与接口冻结`：`允许`
- 条件说明：
  - 会上按推荐方案拍板后，需在 `24 小时内` 完成 `PRD / 页面清单 / 字段占位 / 执行对齐文档` 回写。
  - `expired 阈值`、删除策略和个别接口级细节可以带着责任人进入 `M1`，但不能再推翻主闭环。

## 4. 阻塞项建议结论

### 4.1 阻塞项 1：饭后提醒能力

- 当前结论：`Go`
- 主方案：采用 `方案 C：混合保底方案`
- 会议建议口径：
  - `MVP` 不把外部提醒当成完整记录闭环的唯一前提。
  - 用户完成一餐记录后，优先尝试订阅消息授权与提醒。
  - 如果授权拒绝、主开关关闭、模板不可用或发送失败，自动退回“手动回补保底路径”。
- 对 `MVP` 边界的影响：
  - 不新增页面。
  - 强化 `手帐列表待补提醒` 与 `饭后补感受页` 的保底入口。
- 会后待补动作：
  - 明确授权失败与模板不可用时的埋点口径。
  - 明确后台提醒任务的失败状态展示。

### 4.2 阻塞项 2：记录状态定义

- 当前结论：`Conditional Go`
- 主方案：通过当前最小状态机草案，采用“业务状态 / 提醒状态分层”的方式
- 会议建议口径：
  - `submitted`、`failed` 作为事件或日志保留，不作为长期业务主状态。
  - `business_status` 只承载记录生命周期，不混入提醒发送结果。
  - `reminder_status` 独立承载提醒是否待发、已发、失败、跳过等信息。
  - 森林成长由单一规则触发，并保留幂等标记，避免重复加养分。
- 本轮必须锁住的点：
  - 采用分层状态模型
  - 不把本地草稿直接当成服务端正式状态
  - 饭后补感受完成后，记录才进入“完整完成”口径
- 允许带入 `M1` 的补充项：
  - `expired` 的时间阈值
  - 删除后的展示与统计口径
  - 是否保留服务端草稿占位

### 4.3 阻塞项 3：隐私与敏感数据边界

- 当前结论：`Go`
- 主方案：采用 `方案 C：最小必要 + 角色隔离方案`
- 会议建议口径：
  - 餐图、情绪标签、身体感受按高敏感数据处理。
  - 普通后台不默认展示原始敏感内容。
  - 敏感内容查看、删除、处置都要求角色隔离和审计链路。
  - 如果前台删除能力首版不上线，后台必须保留人工删除兜底流程。
- 对实现的直接影响：
  - 后台最小能力中必须包含 `敏感记录处置台`
  - 页面和字段文档中必须显式标记敏感数据对象
  - 测试范围中必须覆盖删除、脱敏、权限拦截

## 5. 推荐行动项

| 序号 | 动作 | 责任角色 | 截止时间 | 输出物 |
|---|---|---|---|---|
| 1 | 回写 `M0` 正式结论 | 产品 | 会后 24 小时内 | [m0-decision-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-decision-template.md>) |
| 2 | 同步状态与提醒口径 | 产品 / 后端 | 会后 24 小时内 | [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>) |
| 3 | 同步页面与字段边界 | 产品 / 设计 | 会后 24 小时内 | [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)、[interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>) |
| 4 | 更新执行口径与阻塞状态 | 产品 / 项目 | 会后 24 小时内 | [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)、[blocking-issues.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/blocking-issues.md>) |

## 6. 会议上最容易反复讨论的点

- 是否把“提醒”视作用户闭环完成的必要条件
- `expired` 到底算业务状态还是统计标签
- 删除记录后，森林成长是否回滚
- 后台哪些角色能看原图和原始感受文本

## 7. 推荐主持收口话术

- 这次 `M0` 的目标不是把所有实现细节说完，而是锁定不会再反改 `MVP` 主闭环的三条口径。
- 只要提醒、状态机、隐私边界都形成可执行结论，我们就进入 `M1`，剩余细项通过责任人和截止时间继续收。
