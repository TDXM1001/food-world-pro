# 食愈森林 后端接包简报

## 1. 文档目标

- 只面向 `服务端 / 后台研发`，把正式接包所需信息压缩成一份最短材料。
- 区分“现在可以预研什么”和“什么时候算可以正式开做”。
- 作为后端参加开发移交会时的主参考，不替代完整 PRD 和字段文档。

## 2. 当前结论

- 当前阶段：`execution_alignment`
- 当前 Gate：`Conditional Go`
- 当前对后端的口径：
  - `可以预研`：数据模型、任务链路、接口草案、风控与权限方案
  - `暂不可正式接包`：正式排期承诺、联调承诺、按最终口径开发表结构和权限

## 3. 后端本轮实际接包范围

### 3.1 服务端核心能力

- 一餐记录数据模型
- 饭后提醒任务模型与状态记录
- 饭后补感受提交流程
- 森林摘要聚合
- 情绪 / 感受标签配置
- 日签生成、审核、发布最小链路
- 转化看板聚合
- 敏感记录处置链路

### 3.2 后台最小页面支撑

- `ADM-01 后台首页总览`
- `ADM-02 日签生成与审核`
- `ADM-03 标签与提醒规则`
- `ADM-04 记录与转化看板`
- `ADM-05 敏感记录处置台`

### 3.3 本轮不接包内容

- 食方内容库
- 一分钟正念
- 今日宜食详情
- 月度洞察
- 树洞信箱
- 食材红绿灯百科

## 4. 后端正式接包前必须锁住的 5 件事

### 4.1 `M0` 三项阻塞已正式拍板

- 提醒能力方案已定
- 记录状态机已定
- 隐私与敏感数据边界已定

### 4.2 `M1` 范围已冻结

- 后台只做 `ADM-01 ~ ADM-05`
- 小程序仍按 `晨光 / 手帐 / 森林` 三入口 `MVP` 结构理解
- `MP-04 手帐列表` 是待补记录的重要回流入口

### 4.3 核心对象占位已可进入正式 API 草案

- `MealRecord`
- `ReminderTask`
- `ForestSummary`
- `DashboardSummary`
- `SensitiveCase`

### 4.4 权限与删除策略已明确

- 敏感内容默认不进入普通后台可见范围
- 是否支持前台删除已明确
- 如前台不支持删除，后台人工删除 SLA 已明确

### 4.5 页面到接口映射已完整

- 页面不能再出现依赖后端但字段未定义的情况
- 后端不需要再自行猜测前端页面需要什么数据

## 5. 后端现在就可以做的预研

- 数据表草案
- 记录与提醒任务状态模型
- 日签生成任务链路草案
- 敏感处置权限模型
- 定时任务 / 异步任务方案
- API 草案目录
- 失败重试与幂等方案

## 6. 后端暂时不要定死的内容

- `expired` 最终阈值
- 前台删除是否开放前的删除实现细节
- 仍标记为 `待 M0 确认` 的字段
- 因长期订阅消息能力边界导致的最终提醒发送细节
- BI 看板的最终展示样式

## 7. 后端接包时建议优先阅读顺序

1. [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)
2. [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
3. [record-state-machine-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/record-state-machine-draft.md>)
4. [reminder-capability-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/reminder-capability-decision.md>)
5. [privacy-sensitive-data-boundary-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/privacy-sensitive-data-boundary-decision.md>)
6. [owners-and-dependencies.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/owners-and-dependencies.md>)

## 8. 后端正式接包判定

### 可以正式接包

- `M0 + M1` 都完成
- 接口字段占位不再残留会影响实现方式的未决项
- 后台范围和权限边界不再存在第二种解释
- 开发移交会上已明确责任人和依赖顺序

### 只能预研，不能正式接包

- 仍未形成正式 `M0` 或 `M1` 结论
- 字段和状态还有会反改实现方式的未决口径
- 后台权限、删除或提醒方案还会改表结构或任务链路

## 9. 当前建议

- 现在最适合后端做的是“预研 + 接口草案 + 数据模型草案”。
- 真正正式接包的触发点，不是文档数量够多，而是 `M0` 和 `M1` 的正式结论都已经回写完成。
- 如需判断是否已经能开始正式拆后端任务，可直接看 [backend-task-splitting-prereq-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/backend-task-splitting-prereq-checklist.md>)
