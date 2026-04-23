# 食愈森林 MVP 执行对齐方案

## 1. 对齐目标

- 将当前已确认的 `MVP` 版本方案转成可协同推进的执行包。
- 明确设计、研发、测试、运营在首版中的职责边界。
- 提前暴露会阻塞开发和联调的关键前提，避免“文档已定，但团队开不了工”。

## 2. 当前执行对象

### 2.1 本次只对齐 MVP
- 首页日签与记录入口
- 一餐记录发起
- 饭后补感受闭环
- 历史回看与完成反馈
- 森林基础成长反馈
- 后台最小内容生成、规则、提醒、看板能力

### 2.2 本次不进入执行承诺的内容
- 一分钟正念
- 今日宜食
- 场景食方
- 月度洞察
- 树洞信箱
- 食材红绿灯百科

## 3. 执行主线

本次执行不按“页面”推进，而按“闭环”推进。

### 3.1 主执行链路
1. 首页进入并点击记录
2. 完成一餐拍照与心情提交
3. 系统生成记录并安排饭后提醒
4. 用户补充身体感受
5. 系统给出轻反馈并更新森林状态
6. 后台能看到记录与转化数据

### 3.2 执行原则
- 先保主闭环，再补体验增强。
- 先把需要联调的能力定清楚，再推进并行开发。
- 先确认高风险依赖，再承诺里程碑。

## 4. 工作流拆分

## 工作流 A：前置约束确认

### 目标
- 确认不会直接改变 MVP 实现方式的关键前提。

### 必须先确认的事项
- 小程序提醒能力及其限制
- 图片上传与存储方案
- 隐私说明与敏感数据处理边界
- AI 日签生成的审核发布方式
- 森林成长最小规则

### 产出
- 约束确认结论
- 若无法确认，给出降级实现方案

## 工作流 B：产品与设计冻结

### 目标
- 把 MVP 的主流程、页面结构和状态规则固定下来。

### 需要冻结的内容
- 首页最小结构
- 记录发起流程
- 饭后补感受流程
- 手帐历史页结构
- 森林基础反馈结构
- 后台最小操作流

### 产出
- 信息架构图
- 关键页面线框图
- 状态流转说明
- 组件清单与设计规范
- 原型文档参考：
  - [prototype-overview.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/prototype-overview.md>)
  - [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
  - [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
  - [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
  - [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)

## 工作流 C：用户端开发

### 目标
- 完成小程序 MVP 主闭环。

### 范围
- 首页日签卡与记录入口
- 拍照/上传
- 心情选择
- 记录提交
- 感受补填
- 历史记录展示
- 完成反馈
- 森林基础反馈

### 与其他工作流的依赖
- 依赖设计冻结
- 依赖提醒能力确认
- 依赖后台接口与图片上传方案

## 工作流 D：后台与服务端开发

### 目标
- 完成内容、提醒、记录、规则和看板的最小后台支撑。

### 范围
- 日签生成与审核
- 基础情绪/感受标签管理
- 提醒任务与状态记录
- 记录数据存储
- 看板指标汇总

### 与其他工作流的依赖
- 依赖产品定义字段和状态
- 依赖埋点指标口径

## 工作流 E：联调与验证

### 目标
- 确保主闭环可以稳定跑通，并且关键数据能被正确记录。

### 重点
- 首页到记录页来源链路
- 记录提交成功率
- 饭后补填链路
- 森林成长是否正确触发
- 后台审核发布流是否与前台展示一致
- 指标是否可回收

## 5. 里程碑建议

## M0 约束锁定

### 进入条件
- PRD 和版本切分已完成

### 退出条件
- 提醒能力有明确结论
- 敏感数据处理边界有明确结论
- 树洞因不在 MVP 内，不阻塞本阶段

## M1 设计与接口冻结

### 进入条件
- M0 完成

### 退出条件
- 关键页面线框图确定
- 记录与提醒状态机确定
- 核心接口字段确定
- 埋点事件与口径确定

## M2 开发完成可联调

### 进入条件
- M1 完成

### 退出条件
- 前后端完成主闭环开发
- 后台可生成、审核、发布日签
- 看板可读取基础指标

## M3 内测可用

### 进入条件
- M2 完成

### 退出条件
- 主闭环问题已收敛
- 关键异常场景已覆盖
- 埋点和日志可用

## M4 小范围验证

### 进入条件
- M3 完成

### 退出条件
- 可以开始验证记录发起率、完整记录率、回填率、连续记录人数

## 6. 并行与串行关系

### 可以并行
- 设计稿深化 与 后台数据结构设计
- 小程序首页/记录页开发 与 后台日签审核流开发
- 埋点方案梳理 与 看板定义

### 不建议并行
- 在提醒能力未定前，锁死饭后补填交互
- 在记录状态流未定前，开始森林成长联动开发
- 在字段和口径未定前，做看板统计实现

## 7. 跨角色对齐节奏建议

### 周会
- 每周一次执行对齐会
- 重点过：阻塞项、依赖项、边界变化

### 评审节点
- PRD 评审
- 线框与流程评审
- 接口与状态评审
- 联调验收评审
- 评审与移交参考：
  - [m1-review-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-checklist.md>)
  - [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>)
  - [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>)
  - [m1-post-review-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-post-review-writeback-checklist.md>)

### 变更规则
- 任何新增需求，先判断是否进入 MVP 闭环
- 不属于 MVP 闭环增强的，默认进入后续版本池

## 10. 开发移交参考

- 正式移交前先通过 [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>)
- 移交材料统一按 [dev-handoff-package-index.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-package-index.md>) 整理
- 开发移交会建议直接使用 [dev-handoff-meeting-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-meeting-template.md>)

## 8. 当前最关键的阻塞点

- 饭后提醒的可实现路径
- 记录状态与提醒状态的统一定义
- 日签生成后审核发布的最小后台流程
- 森林成长最小规则是否足够简单稳定

## 9. 当前建议

- 不建议现在直接排研发人日或甘特图。
- 先完成 `M0` 和 `M1`，再进入具体执行节奏安排。
- 如果 `饭后提醒` 无法稳定实现，需要立刻回到版本边界，调整 MVP 的验证方式。
