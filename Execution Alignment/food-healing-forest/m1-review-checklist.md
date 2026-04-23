# 食愈森林 M1 评审清单

## 1. 文档目标

- 用于 `M1 设计与接口冻结评审`，统一评审范围、评审标准和会后输出。
- 把 `M1` 从“看过原型”变成“确认页面、状态、字段、边界已冻结”的正式关口。
- 作为进入正式开发移交前的最后一轮产品侧结构确认。

## 2. 当前定位

- 当前阶段：`execution_alignment`
- 当前子阶段：`M1 设计与接口冻结`
- 当前 Gate：`Conditional Go`
- 本清单的作用：判断能否从 `M1` 进入“开发可正式接包”的准备状态

## 3. 评审前必须具备的输入

### 3.1 必备文档

- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
- [prototype-overview.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/prototype-overview.md>)
- [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
- [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
- [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
- [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)

### 3.2 前置结论

- `M0` 三项 `P0` 阻塞至少已有会审结论
- 若仍有未定项，必须明确写为“已知约束”或“待开发前最终锁定”
- 不允许把 `M0` 未决问题伪装成 `M1` 已冻结事实

## 4. 参会角色建议

- 产品
- 设计
- 小程序前端
- 后端 / 后台
- 测试
- 运营
- 如有条件，补充合规 / 安全支持角色

## 5. M1 评审清单

## A. 页面范围是否冻结

- 小程序页面是否严格限制在 `MP-01` 到 `MP-06`
- 后台页面是否严格限制在 `ADM-01` 到 `ADM-05`
- 是否已明确哪些页面不进入 `M1`
- 是否存在“线框里出现、PRD 和版本规划里没有”的新增页面
- 是否存在 `V1 / V2` 页面被提前塞入 `MVP`

## B. 页面结构是否冻结

- `晨光首页` 是否只保留轻内容和主记录入口
- `发起记录页` 是否已压缩到 `餐图 + 心情 + 提交`
- `饭后补感受页` 是否同时支持提醒进入和手动回补
- `手帐列表` 是否清楚区分 `待补` 和 `已完成`
- `森林页` 是否承担反馈，不承担复杂玩法
- `后台首页 / 日签审核 / 规则 / 看板 / 敏感处置` 是否结构清晰且不过度膨胀

## C. 状态与流程是否冻结

- `business_status` 与 `reminder_status` 是否已分层
- 页面状态是否与 PRD 状态口径一致
- `待补 -> 完成` 的主流程是否在首页、手帐、提醒链路里都能闭合
- 森林成长是否只认 `completed`
- 异常场景是否已经覆盖：
  - 上传失败
  - 提醒失败
  - 错过提醒
  - 重复补填
  - 删除记录或人工删除兜底

## D. 接口与字段是否冻结到可讨论状态

- 是否已经为全部 `MVP` 页面准备字段占位
- `MealRecord / ReminderTask / ForestSummary / SensitiveCase` 是否已对齐当前口径
- 页面是否已经能映射到对应接口
- 是否还有页面依赖的数据没有在清单里出现
- 未拍板字段是否已明确标记，而不是被写成定版字段

## E. 后台边界是否冻结

- 后台是否只围绕 `内容生成审核 + 规则维护 + 提醒策略 + 看板 + 敏感处置`
- 是否默认不让普通后台查看原始高敏感内容
- 是否已经预留人工删除与审计路径
- BI 看板是否保持聚合，不向普通角色开放原始内容下钻

## F. 非功能与埋点是否冻结到可继续细化状态

- 核心埋点事件是否已定义
- 指标口径是否能支撑 `MVP` 成功判断
- 图片上传、失败重试、异常提示是否已有页面承接
- 后台审核流和前台展示关系是否一致

## 6. 评审输出要求

- 页面范围结论：`Go / Conditional Go / No Go`
- 结构结论：哪些页面通过，哪些页面要调整
- 字段结论：哪些对象和字段可进入正式 API 文档
- 待补项清单：责任人、截止时间、影响范围
- 是否允许进入 `开发移交前检查`

## 7. 判定标准

### 7.1 `Go`

- 页面范围无争议
- 主流程结构无争议
- 状态、字段、埋点已能稳定进入正式文档细化
- 仅剩视觉和实现层细化，不再影响范围和口径

### 7.2 `Conditional Go`

- 核心结构已通过
- 仍有少量文案、阈值、字段备注待补
- 待补项不会改变 `MVP` 页面范围和主闭环逻辑

### 7.3 `No Go`

- 页面范围仍在漂移
- 主流程仍存在两种以上解释
- 核心状态和字段仍无法统一
- 后台权限边界仍会影响结构设计

## 8. 会后动作

- 用 [m0-post-meeting-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-post-meeting-writeback-checklist.md>) 处理仍需回写的 `M0` 结论
- 回写 `PRD / 原型 / 页面清单 / 字段占位`
- 如果 `M1 = Go`，进入 [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>) 检查
- 用 [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>) 记录评审结论
- 按 [m1-post-review-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-post-review-writeback-checklist.md>) 完成会后回写
- 如需会前先统一建议结论，可参考 [m1-recommended-review-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-recommended-review-draft.md>)

## 9. 当前建议

- `M1` 评审不要讨论高保真视觉喜好，重点只看结构和冻结边界
- 如果 `M0` 没拍板完，不建议把 `M1` 评审结果当正式开发依据
