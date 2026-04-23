# 食愈森林记录状态机草案

## 1. 文档目标

- 为 `M0 阻塞项 2：记录状态定义` 提供一版可评审的统一状态机草案。
- 统一产品、设计、前后端、测试、数据对“记录完成了什么、提醒走到哪一步、森林何时增长、指标如何统计”的理解。
- 明确哪些是 `业务状态`，哪些是 `提醒状态`，哪些只是 `事件`，避免后续口径混乱。

## 2. 状态建模原则

### 2.1 分层定义，不混用
- `业务状态`：描述一条用餐记录是否完成。
- `提醒状态`：描述饭后提醒任务的进展。
- `事件`：描述用户或系统刚刚发生过的动作。
- `派生状态`：例如“已超时未补填”，通过时间和现有状态计算，不单独存主状态。

### 2.2 MVP 以最小状态集为主
- 首版不为少量异常情况创造大量状态。
- 能用事件或日志表达的，不强行升格为主业务状态。

### 2.3 指标以事件为准，主逻辑以状态为准
- `meal_record_submit`、`post_meal_reminder_sent`、`complete_record_finish` 是事件。
- `awaiting_post_meal_feedback`、`completed` 是业务状态。
- 指标统计优先基于事件，页面渲染和后续逻辑优先基于状态。

## 3. 推荐状态模型

## 3.1 业务状态

### A. `draft_local`
- 含义：用户已进入记录流程，但尚未完成本餐提交。
- 说明：
  - 默认只存在客户端，不要求服务端持久化。
  - 主要用于前端交互，不进入后台主统计。

### B. `awaiting_post_meal_feedback`
- 含义：本餐记录已成功提交，等待用户补充饭后身体感受。
- 进入条件：
  - 用户完成餐图上传、选择当下心情，并提交成功。
- 说明：
  - 这是首版最关键的中间状态。
  - 无论提醒是否已成功安排，都进入该状态。

### C. `completed`
- 含义：用户已补充饭后身体感受，该条记录成为“完整记录”。
- 进入条件：
  - 用户在本餐记录上成功提交至少一个饭后感受标签。
- 说明：
  - 这是森林成长和完整记录率统计的唯一触发业务状态。

### D. `deleted`
- 含义：记录被用户主动删除，或因系统原因标记为不可用。
- 进入条件：
  - 后续若产品确认支持删除，则进入此状态。
- 说明：
  - 当前 PRD 未明确要求首版开放删除能力，因此此状态先预留，不要求 MVP 首版前台开放。

## 3.2 为什么不把 `submitted` 作为长期业务状态

- `提交成功` 更适合作为事件，而不是长期状态。
- 因为一旦提交成功，记录立即进入 `awaiting_post_meal_feedback`，没有必要长期停留在 `submitted`。
- 这样可以减少一个无实际业务价值的中间状态，降低前后端和测试复杂度。

## 3.3 为什么不把 `failed` 作为主业务状态

- 上传失败、提醒调度失败、感受提交失败，属于操作失败或任务失败。
- 它们更适合写入 `事件 / 日志 / 错误码`，而不是把整条记录置为 `failed`。
- 否则会出现“记录本身失败”与“提醒失败但记录仍有效”混淆。

## 4. 提醒状态模型

### A. `not_scheduled`
- 含义：提醒未安排成功，或当前平台能力不支持安排。
- 使用场景：
  - 订阅未授权
  - 平台限制
  - 系统调度失败

### B. `scheduled`
- 含义：提醒任务已创建，等待触发发送。

### C. `sent`
- 含义：提醒已发出。

### D. `opened`
- 含义：用户通过提醒进入了记录补填页面。

### E. `feedback_submitted`
- 含义：用户已完成饭后感受补填，提醒任务完成闭环。

### F. `expired`
- 含义：提醒在有效期内未被打开或未触发有效补填。
- 说明：
  - `expired` 不意味着记录失效。
  - 记录业务状态仍可保持 `awaiting_post_meal_feedback`，用户仍可手动回补。

### G. `canceled`
- 含义：提醒在发送前或发送后被系统取消。
- 使用场景：
  - 用户在提醒触发前已经手动完成补填
  - 记录被删除或作废

## 5. 推荐状态转换

## 5.1 主业务状态转换

### 路径 1：正常完成
1. 用户进入记录页
2. 产生前端本地态 `draft_local`
3. 用户提交成功
4. 业务状态进入 `awaiting_post_meal_feedback`
5. 用户补填饭后感受
6. 业务状态变为 `completed`

### 路径 2：提醒失败但用户手动补填
1. 用户提交成功
2. 业务状态进入 `awaiting_post_meal_feedback`
3. 提醒状态为 `not_scheduled`
4. 用户从历史记录手动进入
5. 补填饭后感受
6. 业务状态变为 `completed`

### 路径 3：长期未补填
1. 用户提交成功
2. 业务状态进入 `awaiting_post_meal_feedback`
3. 提醒过期或未安排
4. 用户长期未补填
5. 业务状态维持不变，是否“超时”由页面计算展示

## 5.2 提醒状态转换

### 正常发送路径
`not_scheduled` 或无状态 -> `scheduled` -> `sent` -> `opened` -> `feedback_submitted`

### 无法发送路径
`not_scheduled`

### 发送后未补填路径
`scheduled` -> `sent` -> `expired`

### 用户提前完成路径
`scheduled` -> `canceled`

## 6. 森林成长触发规则

### 6.1 唯一触发点
- 仅在业务状态首次从 `awaiting_post_meal_feedback` 变为 `completed` 时触发一次。

### 6.2 幂等要求
- 同一条记录只能触发一次森林成长。
- 重复提交感受、重复打开页面、重复刷新都不能重复发放成长。

### 6.3 推荐字段
- `forest_growth_applied: true / false`

## 7. 页面展示建议

## 7.1 手帐页

### `draft_local`
- 展示未完成填写界面，不进入历史记录列表。

### `awaiting_post_meal_feedback`
- 在今天记录和历史列表中显示“待补饭后感受”。
- 若距离用餐时间超过阈值，可展示派生态“待回补”或“已错过提醒”，但不改变主状态。

### `completed`
- 显示完整记录卡片。
- 显示完成反馈和可回看内容。

## 7.2 森林页

- 只读取 `completed` 数量和连续天数规则。
- 不读取提醒状态。

## 7.3 后台看板

- 记录发起率：基于 `meal_record_start` 事件
- 提交成功率：基于 `meal_record_submit` 事件
- 完整记录率：基于记录状态进入 `completed` 或 `complete_record_finish` 事件
- 提醒回填率：基于 `post_meal_reminder_sent` 与 `post_meal_feeling_submit` 事件

## 8. 埋点映射建议

## 8.1 事件与状态对应关系

### `meal_record_start`
- 用户进入记录流程
- 不改变服务端业务状态

### `meal_record_submit`
- 记录提交成功
- 业务状态进入 `awaiting_post_meal_feedback`

### `meal_record_submit_fail`
- 提交失败事件
- 业务状态保持 `draft_local`

### `post_meal_reminder_sent`
- 提醒状态进入 `sent`

### `post_meal_reminder_open`
- 提醒状态进入 `opened`

### `post_meal_feeling_submit`
- 用户提交饭后感受成功

### `complete_record_finish`
- 业务状态进入 `completed`
- 若需要，可与 `post_meal_feeling_submit` 同时触发，但建议保留为独立闭环完成事件

## 9. 异常场景处理建议

### 9.1 提交成功但提醒调度失败
- 业务状态仍进入 `awaiting_post_meal_feedback`
- 提醒状态记为 `not_scheduled`
- 页面允许用户从历史记录手动补填

### 9.2 提醒已发送，但用户直接从历史记录补填
- 提醒状态可记为 `feedback_submitted`
- 业务状态进入 `completed`

### 9.3 用户点开提醒但未提交感受
- 提醒状态保持 `opened`
- 业务状态不变

### 9.4 用户反复编辑饭后感受
- MVP 建议不开放复杂编辑
- 如允许再次修改，森林成长仍只结算一次

### 9.5 用户删除记录
- 若 MVP 首版不开放删除，则先不进入主流程
- 若后续开放，删除后提醒任务应同步 `canceled`

## 10. 推荐数据字段

- `record_id`
- `user_id`
- `meal_image_url`
- `meal_time`
- `mood_tags`
- `post_meal_feeling_tags`
- `business_status`
- `reminder_status`
- `reminder_planned_at`
- `reminder_sent_at`
- `completed_at`
- `forest_growth_applied`
- `deleted_at`

## 11. 当前待确认点

- `draft_local` 是否需要服务端保存草稿
- `expired` 的时间阈值如何定义
- 是否允许补填后再次编辑饭后感受
- MVP 首版是否开放删除记录

## 12. 当前建议

- 先采用这套最小状态模型进入 `M0` 评审。
- 若会议无重大异议，应在 `M1 设计与接口冻结` 前，把状态表同步到：
  - PRD
  - 接口文档
  - 埋点文档
  - 测试用例

