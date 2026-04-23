# 食愈森林 开发移交会议模板

## 1. 会议定位

- 用于 `M0` 和 `M1` 都完成后的正式开发移交会。
- 目标不是重新做需求澄清，而是确认本次开发接包范围、冻结依据、依赖顺序和后续动作。
- 如果会前还在改 `MVP` 范围、主流程、状态定义或后台权限边界，不建议使用本模板直接开移交会。

## 2. 会前确认

- 是否已通过 [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>)
- 是否已整理好 [dev-handoff-package-index.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-package-index.md>)
- 是否已有最新的 `M0` 决策结论和 `M1` 评审记录
- 是否已完成 `M1` 会后回写

## 3. 会议基本信息

- 会议名称：
- 会议时间：
- 参会角色：
- 主持人：
- 记录人：

## 4. 本次移交目标

- 本次移交对应版本：
- 本次只接的范围：
- 本次明确不接的范围：
- 本次最关键的业务指标：
- 本次最关键的交付风险：

## 5. 会议议程

### 5.1 范围确认

- 是否以 `MVP` 为唯一移交边界
- 是否确认 `不做项` 不进入本轮开发任务拆分
- 是否存在任何会后可能反改主闭环的争议点

### 5.2 主流程与状态确认

- 首页进入记录的主链路是否唯一
- `business_status` 是否已冻结
- `reminder_status` 是否已冻结
- 森林成长触发口径是否已冻结

### 5.3 页面与后台结构确认

- 小程序页面清单是否以 [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>) 为准
- 后台页面范围是否以最小审核和看板能力为准
- 空状态、失败状态、待补状态是否已覆盖

### 5.4 字段与接口确认

- 是否以 [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>) 作为 API 文档起草基础
- 是否仍有会影响实现方式的未决字段
- 图片上传、记录创建、补感受、森林摘要、看板、敏感处置是否都有明确对象占位

### 5.5 角色分工与依赖确认

- 产品、设计、前端、后端、测试、运营各自的起始输入是否明确
- 是否存在需要先行预研、再排正式开发的链路
- 是否存在单点阻塞责任人未明确的事项

### 5.6 测试与节奏确认

- 验收标准是否已经足够支撑测试起草用例
- 联调前置条件是否明确
- 是否允许进入正式排期与开发承诺

## 6. 会议结论模板

- 总体结论：`Go / Conditional Go / No Go`
- 是否允许正式移交开发：
- 本次接包版本：
- 本次接包页面范围：
- 本次不接页面范围：
- 本次接包后台范围：
- 本次冻结依据文档：

| 文档 | 版本或日期 | 责任人 | 备注 |
|---|---|---|---|
| PRD |  |  |  |
| 页面清单 |  |  |  |
| 字段占位 |  |  |  |
| M0 结论 |  |  |  |
| M1 结论 |  |  |  |

## 7. 待跟进行动项

| 序号 | 动作 | 责任人 | 截止时间 | 是否阻塞开发 |
|---|---|---|---|---|
| 1 |  |  |  |  |
| 2 |  |  |  |  |
| 3 |  |  |  |  |

## 8. 会议中不要做的事

- 不把移交会开成新一轮需求分析会。
- 不现场扩 `MVP` 范围。
- 不用尚未验证的技术细节去推翻已冻结的产品主结构。
- 如果发现主闭环仍无共识，应退回 `M1`，而不是勉强宣布可开发。

## 9. 会后动作

1. 补全本次移交会结论并留档。
2. 用 [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>) 再次确认是否达到正式移交条件。
3. 如果 `Go`，再组织研发任务拆分和正式排期。
4. 如果 `Conditional Go / No Go`，把问题退回对应文档，不直接口头承诺开工。
