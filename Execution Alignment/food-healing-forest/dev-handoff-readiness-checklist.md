# 食愈森林 开发移交前检查表

## 1. 文档目标

- 判断食愈森林是否已经具备“正式移交开发”的条件。
- 把“可以先预研”与“可以正式接包开发”区分开。
- 作为 `M1` 评审通过后的最后一道移交门槛。

## 2. 核心原则

- 只有 `M0` 和 `M1` 都过关，才建议正式移交开发。
- 文档齐全不等于可开发，必须同时满足范围冻结、状态冻结、字段冻结、边界冻结。
- 如果某项仍会改动主闭环、页面结构或后台权限，就不能算正式移交。

## 3. 当前建议口径

- `可以提前介入`：技术预研、工时评估、风险评估、接口草案
- `可以正式移交`：排期承诺、任务拆分、正式联调开发
- 本清单用于判断是否能从前者进入后者

## 4. 开发移交前检查清单

## A. 决策关口

- `M0` 三项 `P0` 阻塞是否已拍板
- `M1` 是否已通过结构评审
- 是否仍存在会直接影响主闭环的未决问题

## B. 范围关口

- `MVP` 页面范围是否已冻结
- `MVP` 后台范围是否已冻结
- 不做项是否已从评审和移交范围中明确剔除
- 是否不存在“先做着看”的灰色页面或灰色模块

## C. 状态与字段关口

- `business_status` 是否最终锁定
- `reminder_status` 是否最终锁定
- `MealRecord / ReminderTask / ForestSummary / SensitiveCase` 是否已具备正式字段定义基础
- `M0` 未决字段是否已关闭，或被明确降级处理

## D. 设计关口

- 小程序关键页面线框是否确认
- 后台关键页面线框是否确认
- 空状态、失败状态、待补状态、已完成状态是否已覆盖
- 页面间跳转是否唯一且清晰

## E. 接口关口

- 页面与接口映射是否完整
- 是否已具备正式 API 文档起草条件
- 图片上传、记录创建、补感受、森林摘要、看板、敏感处置是否都有接口占位
- 是否不存在页面已依赖、但后端仍未知的数据项

## F. 测试与验收关口

- 核心流程验收标准是否已明确
- 状态与幂等验收是否已明确
- 异常场景是否已具备测试依据
- 埋点与看板回收口径是否已明确

## G. 运营与后台关口

- 日签生成与审核流是否明确
- 标签与提醒规则维护方式是否明确
- 人工删除兜底方案是否明确
- 敏感处置台的角色边界和审计要求是否明确

## 5. 开发正式接包的最低交付包

- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
- [prototype-overview.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/prototype-overview.md>)
- [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
- [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
- [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
- [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)
- `M0` 最终决议记录
- `M1` 评审结论记录

## 6. 判定标准

### 6.1 `可正式移交开发`

- 上述检查项全部通过，或仅剩不影响范围和口径的细枝末节
- 研发可以据此拆任务、定接口、排联调，不会在一周内被迫推翻结构

### 6.2 `可预研，不可正式移交`

- 文档和原型已足够让研发提前介入
- 但仍有关键决策未锁，排期与开发承诺会有返工风险

### 6.3 `不可移交`

- 仍缺页面清单、字段清单或关键状态口径
- 仍存在会影响主流程的未决问题
- 仍需重新收缩 `MVP` 范围

## 7. 当前食愈森林的判断口径

- 如果 `M0` 尚未正式拍板：`可预研，不可正式移交`
- 如果 `M0` 完成，但 `M1` 还未评审：`可准备移交包，不可正式移交`
- 只有 `M0 + M1` 都通过后，才进入 `可正式移交开发`

## 8. 会后建议动作

1. 先用 [m1-review-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-checklist.md>) 走完 `M1`
2. 再按本清单逐项检查
3. 用 [dev-handoff-package-index.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-package-index.md>) 整理本次正式接包材料
4. 通过后再用 [dev-handoff-meeting-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-meeting-template.md>) 组织开发移交会

## 9. 当前建议

- 开发移交会不要开成需求澄清会
- 如果会前还在改页面范围、状态定义或权限边界，就先不开移交会
- 真正移交的标志不是“文档很多”，而是“团队对做什么和不做什么没有第二种理解”
