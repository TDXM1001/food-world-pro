# 食愈森林 MVP 阻塞项清单

## P0 阻塞项

### 1. 饭后提醒能力
- 影响范围：`PRD-006`、`PRD-016`
- 为什么阻塞：它决定“完整记录闭环”是否能成立。
- 若未确认的风险：可能需要把提醒改成被动回访，直接影响完整记录率预期。
- 建议处理：优先由产品、研发确认平台能力与替代方案。
- 参考材料：[reminder-capability-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/reminder-capability-decision.md>)

### 2. 记录状态定义
- 影响范围：记录提交、提醒、补填、森林成长、看板统计
- 为什么阻塞：如果状态机不统一，前后端和数据口径会出现偏差。
- 建议处理：在设计冻结前输出统一状态表。

### 3. 隐私与敏感数据边界
- 影响范围：餐图、情绪、身体感受
- 为什么阻塞：这类数据直接影响产品说明、存储方式和风控策略。
- 建议处理：在开发前完成基础隐私口径确认。
- 参考材料：[privacy-sensitive-data-boundary-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/privacy-sensitive-data-boundary-decision.md>)

## P1 风险项

### 4. 日签 AI 生成稳定性
- 影响范围：首页体验、内容品牌一致性
- 为什么重要：若生成不稳，审核成本会明显上升。
- 建议处理：首版先只支持单一内容类型，并保留兜底模板。

### 5. 森林成长规则过复杂
- 影响范围：用户端逻辑、后台规则、测试成本
- 为什么重要：过早做复杂养成会拖慢 MVP。
- 建议处理：首版只保留“完整记录 -> 增长一次”的最小规则。

## 当前建议

- `P0` 三项未收口前，不建议把 MVP 进入正式开发承诺。
- `P1` 项可在设计和开发过程中并行收敛，但不能扩成新版本目标。
