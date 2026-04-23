# 食愈森林 M1 评审后回写清单

## 1. 文档目标

- 用于 `M1 设计与接口冻结评审` 结束后，把结论同步回原型、页面、字段和执行文档。
- 避免出现“评审通过了，但原型和清单仍停留在旧版本”的情况。
- 本清单只覆盖 `M1` 相关产物，不替代 `M0` 决议回写清单。

## 2. 使用方式

1. 先用 [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>) 记录会议结论。
2. 再按本清单逐项回写正式文档。
3. 如果 `M1 = No Go`，先冻结结论范围，不进入开发移交前检查。

## 3. 回写总原则

- 以 `MVP` 边界为准，不因为评审讨论顺手扩范围。
- 页面和字段的变更，必须同时更新“页面清单”和“字段占位”，不能只改其中一份。
- 影响结构的结论应先回写原型，再回写执行对齐文档。
- 若 `M1` 引发范围变化，再考虑更新版本规划。

## 4. 必回写文档

### 4.1 设计冻结文档

- [prototype-overview.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/prototype-overview.md>)
- [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
- [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
- [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
- [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)

### 4.2 执行对齐文档

- [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)
- [owners-and-dependencies.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/owners-and-dependencies.md>)
- [m1-review-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-checklist.md>)

## 5. 有条件回写文档

### 5.1 PRD

- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
- 仅当 `M1` 评审改变页面结构、主流程口径、字段对象边界时更新

### 5.2 版本规划

- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
- [tradeoff-log.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/tradeoff-log.md>)
- 仅当评审导致 `MVP / V1 / V2` 边界变化时更新

## 6. 回写重点

## A. 页面范围

- 是否仍严格限制在 `MP-01 ~ MP-06` 与 `ADM-01 ~ ADM-05`
- 是否移除了评审中被否掉的页面或入口
- 是否把“不进入 M1”的页面继续留在了主方案里

## B. 页面结构

- 首页、手帐、森林是否仍围绕完整记录闭环
- 后台是否仍是最小审核和看板系统
- 是否补上了空状态、失败状态、待补状态

## C. 字段与接口

- 对象和字段名是否与评审结论一致
- 页面是否都能映射到现有接口占位
- 未定字段是否被清楚标记，而不是默认为已确认

## D. 执行口径

- `alignment-plan.md` 的 `M1` 退出条件是否与评审结论一致
- `owners-and-dependencies.md` 的设计交付口径是否与原型包一致
- 是否已经明确能否进入开发移交前检查

## 7. 建议回写顺序

1. 回写 [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>) 的会议结论。
2. 回写设计冻结文档：原型总览、线框、页面清单、字段占位。
3. 回写执行对齐文档：`alignment-plan.md` 和 `owners-and-dependencies.md`。
4. 如有必要，再回写 `PRD / version-split / tradeoff-log`。
5. 最后用 [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>) 重新判断能否正式移交开发。

## 8. 完成判定

- 原型和页面清单不再与评审结论冲突
- 字段占位文档不再残留过时口径
- 执行计划中 `M1` 退出条件与会议结论一致
- 团队可以用同一套文档继续进入开发移交判断

## 9. 当前建议

- `M1` 会后先收口原型和字段，再开开发移交会
- 如果 `M1` 会后 24 小时内还没完成文档回写，不建议直接口头宣布“可交开发”
