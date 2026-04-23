# 食愈森林 开发移交包索引

## 1. 文档目标

- 把正式开发移交所需材料收成一包，避免 `M1` 通过后仍依赖口头串联。
- 明确哪些文档属于“冻结事实”，哪些只是“背景参考”，减少团队二次理解。
- 作为组织开发移交会时的统一入口，方便产品、设计、研发、测试、运营按同一口径接包。

## 2. 使用前提

- `M0` 三项 `P0` 阻塞已形成正式结论。
- `M1` 已完成评审，并已用 [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>) 留存结论。
- 会后已按 [m1-post-review-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-post-review-writeback-checklist.md>) 完成文档回写。
- 已用 [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>) 判断是否满足正式移交门槛。

## 3. 开发移交包结构

### A. 范围与决策层

- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
- [tradeoff-log.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/tradeoff-log.md>)
- [record-state-machine-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/record-state-machine-draft.md>)
- [reminder-capability-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/reminder-capability-decision.md>)
- [privacy-sensitive-data-boundary-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/privacy-sensitive-data-boundary-decision.md>)

### B. 页面与结构冻结层

- [prototype-overview.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/prototype-overview.md>)
- [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
- [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
- [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)

### C. 字段与接口冻结层

- [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)
- [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>)

### D. 执行与协同层

- [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)
- [owners-and-dependencies.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/owners-and-dependencies.md>)
- [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>)
- [dev-handoff-meeting-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-meeting-template.md>)
- [backend-handoff-brief.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/backend-handoff-brief.md>)
- [backend-task-splitting-prereq-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/backend-task-splitting-prereq-checklist.md>)
- [m0-m1-shortest-execution-order.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-m1-shortest-execution-order.md>)
- [m0-m1-execution-tracker.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-m1-execution-tracker.md>)

### E. 会前参考样稿

- [m0-recommended-decision-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-recommended-decision-draft.md>)
- [m1-recommended-review-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-recommended-review-draft.md>)

## 4. 冻结事实与背景参考的区分

### 4.1 冻结事实

- `PRD` 中已回写的功能范围、主流程、状态与异常口径
- `version-split.md` 中已确认的 `MVP / V1 / V2` 边界
- `page-inventory.md` 中已冻结的页面清单与不做项
- `interface-field-placeholders.md` 中已冻结的对象与字段占位
- `M1` 评审结论记录中已拍板的结构、字段、后台边界

### 4.2 背景参考

- 线框与原型说明
- 版本取舍记录
- `M0` 三项决策稿
- 会前 checklist 和主持材料

说明：
- 正式移交时，开发应优先以“冻结事实”作为实现依据。
- “背景参考”用于理解为什么这样定，不应用来绕开已冻结边界。

## 5. 各角色建议阅读顺序

### 产品 / 项目负责人

1. [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
2. [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
3. [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>)
4. [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)

### 小程序前端

1. [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
2. [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
3. [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)
4. [alignment-plan.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/alignment-plan.md>)

### 服务端 / 后台

1. [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
2. [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
3. [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)
4. [owners-and-dependencies.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/owners-and-dependencies.md>)

### 测试

1. [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
2. [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
3. [record-state-machine-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/record-state-machine-draft.md>)
4. [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>)

### 运营 / 内容审核

1. [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
2. [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
3. [owners-and-dependencies.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/owners-and-dependencies.md>)
4. [privacy-sensitive-data-boundary-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/privacy-sensitive-data-boundary-decision.md>)

## 6. 开发移交会必须产出的结论

- 明确本次接包所依据的文档版本和日期。
- 明确 `MVP` 做什么、不做什么，以及哪些项进入后续版本。
- 明确前后端、测试、运营的职责边界和依赖顺序。
- 明确仍然存在的技术未知项，并把它们改写成责任人明确的行动项。
- 明确是否允许进入正式排期与联调开发。

## 7. 当前建议

- 如果 `M0` 或 `M1` 仍未通过，这份索引只用于“整理移交包”，不用于宣布正式开工。
- 一旦 `M0 + M1` 都通过，这份索引应作为开发移交会的单一入口，而不是临时散发多份链接。
