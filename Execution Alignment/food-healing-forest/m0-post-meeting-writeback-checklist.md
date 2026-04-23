# 食愈森林 M0 决议回写清单

## 1. 文档目标

- 用于 `M0 阻塞项确认会` 结束后，快速把正式结论同步回现有文档。
- 避免出现“会上已经拍板，文档口径还停留在旧版本”的情况。
- 这份清单只覆盖 `P0` 三项阻塞和它们直接影响的文档，不扩展到详细设计稿或接口文档正文。

## 2. 使用方式

1. 先用 [m0-decision-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-decision-template.md>) 记录会议最终结论。
2. 再按本清单逐项回写正式文档。
3. 如果任一阻塞项结论为 `No Go`，先更新版本与执行口径，再决定是否继续推进 `M1`。

## 3. 回写总原则

- `PRD` 负责沉淀正式需求口径，不能只停留在会议纪要里。
- `blocking-issues.md` 负责更新阻塞项状态，避免团队继续把已拍板事项当未决问题。
- `alignment-plan.md` 负责同步里程碑进入条件和跨角色依赖。
- `version-split.md` 只在结论影响 `MVP / V1 / V2` 边界时更新，不做无意义重写。
- 如结论改变了原有取舍理由，再补写 [tradeoff-log.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/tradeoff-log.md>)。

## 4. 阻塞项 1：饭后提醒能力

### 4.1 必回写文档

- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
  - `7.2 手帐`
  - `7.5 后台`
  - `8. 记录状态与提醒状态定义`
  - `10. 验收标准`
  - `11. 数据要求`
  - `13. 依赖与风险`
  - `14. 待确认问题`
- [blocking-issues.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/blocking-issues.md>)
  - `1. 饭后提醒能力`
- [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)
  - `工作流 A：前置约束确认`
  - `M0 约束锁定`
  - `M1 设计与接口冻结`

### 4.2 有条件回写文档

- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
  - 当提醒能力被降级，导致 `MVP` 去掉订阅消息增强时更新
- [tradeoff-log.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/tradeoff-log.md>)
  - 当提醒能力方案从“增强项”变为“后移项”时更新

### 4.3 回写重点

- 明确提醒是否只是增强路径，还是 `MVP` 必要能力。
- 明确 `整体完整记录率` 和 `提醒回补率` 是否拆开统计。
- 明确授权失败、主开关关闭、模板不可用时的降级路径。
- 删除或保留与“固定微信横幅提醒”相关的对外承诺。

## 5. 阻塞项 2：记录状态定义

### 5.1 必回写文档

- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
  - `8. 记录状态与提醒状态定义`
  - `9. 异常场景与边界`
  - `10.4 状态与幂等验收`
  - `11. 数据要求`
  - `14. 待确认问题`
- [blocking-issues.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/blocking-issues.md>)
  - `2. 记录状态定义`
- [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)
  - `工作流 B：产品与设计冻结`
  - `工作流 C：用户端开发`
  - `工作流 D：后台与服务端开发`
  - `工作流 E：联调与验证`

### 5.2 有条件回写文档

- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
  - 当 `删除记录`、`补填后再编辑` 等边界导致 MVP 范围变化时更新
- [record-state-machine-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/record-state-machine-draft.md>)
  - 若会议有新口径，需同步或标记为已纳入正式 PRD

### 5.3 回写重点

- 锁定 `business_status` 和 `reminder_status` 最终枚举。
- 锁定 `expired` 阈值、`draft_local` 是否落服务端、是否开放删除。
- 明确 `submitted / failed` 是事件还是主状态。
- 明确森林成长唯一触发点与幂等口径。

## 6. 阻塞项 3：隐私与敏感数据边界

### 6.1 必回写文档

- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
  - `7.2 手帐`
  - `7.5 后台`
  - `9. 异常场景与边界`
  - `11. 数据要求`
  - `12. 非功能要求`
  - `13. 依赖与风险`
  - `14. 待确认问题`
- [blocking-issues.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/blocking-issues.md>)
  - `3. 隐私与敏感数据边界`
- [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)
  - `工作流 A：前置约束确认`
  - `工作流 D：后台与服务端开发`
  - `工作流 E：联调与验证`

### 6.2 有条件回写文档

- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
  - 当前台删除能力被后移，或树洞边界被提前锁定为后续版本前置条件时更新
- [tradeoff-log.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/tradeoff-log.md>)
  - 当权限、删除、风控边界引发体验与实施成本取舍时更新

### 6.3 回写重点

- 明确哪些数据按高敏感内容处理。
- 明确哪些后台角色默认不可见原始内容。
- 明确 BI 是否只保留聚合指标。
- 明确删除策略是前台自助还是后台人工 SLA。
- 明确树洞虽然延期，但是否现在就锁独立存储、独立权限、独立风控。

## 7. 文档回写顺序建议

1. 回写 [m0-decision-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-decision-template.md>)，保留原始会议结论。
2. 回写 [blocking-issues.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/blocking-issues.md>)，同步阻塞项状态。
3. 回写 [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)，固化正式需求口径。
4. 回写 [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)，同步阶段进入条件和依赖。
5. 仅在范围变化时回写 [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>) 和 [tradeoff-log.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/tradeoff-log.md>)。

## 8. 完成判定

- `blocking-issues.md` 中 3 个 `P0` 项都已更新为会后实际状态。
- `prd.md` 中不再残留与会议结论冲突的旧口径。
- `alignment-plan.md` 的 `M0` 退出条件与会议结论一致。
- 若 `MVP` 范围被改动，`version-split.md` 与 `tradeoff-log.md` 也已同步。

## 9. 当前建议

- 会后不要直接分散给各角色分别改文档，先由产品统一回写主口径，再通知设计、研发、测试跟进。
- 如果会议结束后 24 小时内还没有完成文档回写，就不建议口头进入 `M1`。
