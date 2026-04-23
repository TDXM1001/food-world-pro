# 食愈森林 M0 会议主持摘要

## 1. 会议目标

- 在进入 `M1 设计与接口冻结` 前，一次性拍板 3 个 `P0` 阻塞项。
- 输出的是可执行结论，不是继续收集意见。
- 会议结束时必须明确：`Go / Conditional Go / No Go`、责任人、回写文档范围、关闭时限。

## 2. 当前阶段判断

- 当前阶段：`execution_alignment`
- 当前 Gate：`Conditional Go`
- 原因：3 个 `P0` 阻塞项都已有可评审材料，但还没有正式会审结论。

## 3. 本次只拍板 3 件事

### 3.1 阻塞项 1：饭后提醒能力

- 推荐结论：采用 `方案 C：混合保底方案`
- 一句话定义：`手动回补是保底闭环，订阅消息只是增强路径`
- 会上必须拍板：
  1. MVP 是否接受“没有外部提醒也能完成完整记录闭环”
  2. 是否接入订阅消息，但不把它当唯一完成前提
  3. 指标上是否拆开看 `整体完整记录率` 和 `提醒回补率`
- 不建议拍成的方向：把“微信提醒稳定触达”当作 MVP 默认承诺
- 如果没拍板的后果：`PRD-006 / PRD-016 / 指标解释` 都会继续摇摆

### 3.2 阻塞项 2：记录状态定义

- 推荐结论：通过当前最小状态机草案
- 一句话定义：`业务状态` 和 `提醒状态` 分层，森林成长只认 `completed`
- 当前推荐口径：
  - `business_status`: `draft_local / awaiting_post_meal_feedback / completed / deleted`
  - `reminder_status`: `not_scheduled / scheduled / sent / opened / feedback_submitted / expired / canceled`
  - `submitted / failed` 作为事件或日志，不作为长期主状态
- 会上必须拍板：
  1. 是否接受 `draft_local` 仅前端存在
  2. `expired` 的时间阈值怎么定义
  3. 是否允许补填后再次编辑饭后感受
  4. MVP 是否开放删除记录
- 如果没拍板的后果：前后端、测试、埋点、看板口径会继续不一致

### 3.3 阻塞项 3：隐私与敏感数据边界

- 推荐结论：采用 `方案 C：最小必要 + 角色隔离方案`
- 一句话定义：`原始高敏感内容默认不进入普通后台可见范围`
- 当前推荐口径：
  - `餐图 / 情绪标签 / 身体感受标签` 视为高敏感用户内容
  - `未来树洞原文` 视为高风险自由表达内容
  - BI 看板默认只看聚合指标，不开放原始内容下钻
  - 若前台暂不支持删除，至少要先有后台人工删除流程
- 会上必须拍板：
  1. 哪些角色可以看原始餐图
  2. 是否要求白名单加审计日志
  3. MVP 删除能力是前台自助还是后台人工 SLA
  4. 树洞虽延期，是否现在就锁定独立存储和独立权限
- 如果没拍板的后果：权限设计、存储方案、上线说明和后续风控都会返工

## 4. 主持人建议结论

- `建议结论 1`：提醒能力按 `混合保底方案` 通过
- `建议结论 2`：状态机按当前最小模型通过，但保留 `expired 阈值` 和 `删除策略` 的补充说明
- `建议结论 3`：隐私边界按 `最小必要 + 角色隔离方案` 通过
- 如果会议只能锁一个最低前提，优先锁：`原始高敏感内容默认不进入普通后台可见范围`

## 5. 建议会议流程

- `0-5 分钟`：重申会议目标，只拍板不发散
- `5-20 分钟`：确认饭后提醒能力
- `20-35 分钟`：确认记录状态定义
- `35-50 分钟`：确认隐私与敏感数据边界
- `50-60 分钟`：复述结论、责任人、文档回写与截止时间

## 6. 会后必须落地的动作

- 回写 [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
- 回写 [blocking-issues.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/blocking-issues.md>)
- 必要时回写 [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
- 用 [m0-decision-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-decision-template.md>) 记录最终结论
- 按 [m0-post-meeting-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-post-meeting-writeback-checklist.md>) 逐项回写正式文档

## 7. 本次会议通过条件

- 3 个 `P0` 项至少都形成明确结论，而不是“后面再看”
- 每个结论都带有降级方案或替代路径
- 每个结论都明确影响哪些文档和由谁回写
- 如果任一项为 `No Go`，则不进入正式开发承诺
