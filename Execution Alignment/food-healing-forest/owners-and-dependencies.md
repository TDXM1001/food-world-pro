# 食愈森林 MVP 角色分工与依赖

## 1. 产品

### 负责内容
- 确认 MVP 边界
- 固化主流程和状态流转
- 明确异常场景与验收口径
- 锁定埋点指标定义

### 交付物
- 最终 PRD
- 版本切分结论
- 状态与规则说明
- 待确认问题优先级

### 依赖
- 提醒能力结论
- 隐私与风控边界结论

## 2. 设计

### 负责内容
- 首页、记录页、补感受页、森林页、后台最小审核流的线框和高保真
- 主状态、空状态、失败状态、完成反馈状态

### 交付物
- 页面流程图
- 关键页面稿
- 组件与样式规范
- 交互说明
- 原型文档：
  - [prototype-overview.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/prototype-overview.md>)
  - [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
  - [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
  - [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
  - [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)

### 依赖
- 产品冻结页面结构
- 森林成长规则最小方案

## 3. 小程序前端

### 负责内容
- 首页日签展示
- 记录发起和图片上传
- 心情选择和记录提交流
- 饭后补感受流程
- 历史记录展示
- 森林基础反馈展示
- 埋点接入

### 交付物
- 用户端主闭环功能
- 异常处理逻辑
- 埋点事件回传

### 依赖
- 设计稿
- 图片上传能力
- 后台接口
- 提醒能力方案

## 4. 服务端 / 后台

### 负责内容
- 记录数据模型
- 日签生成与审核发布
- 提醒任务管理
- 情绪/感受标签与规则维护
- 基础看板数据聚合

### 交付物
- 接口文档
- 后台管理页面
- 定时/异步任务
- 指标汇总逻辑

### 依赖
- 产品字段定义
- 埋点口径
- 内容审核规则

## 5. 测试

### 负责内容
- 主流程覆盖
- 异常场景覆盖
- 提醒与回填链路验证
- 内容发布与前台展示一致性验证
- 数据回收验证

### 交付物
- 测试清单
- 缺陷列表
- 回归报告

### 依赖
- 验收标准
- 联调环境
- 埋点校验方式

## 6. 运营

### 负责内容
- 日签内容审核与发布
- 基础标签词库维护
- 提醒文案模板确认
- 小范围上线前的内容准备

### 交付物
- 日签内容池
- 审核规范
- 提醒文案模板

### 依赖
- 后台审核流可用
- 内容风格规范明确

## 7. 关键依赖图

### 先于开发必须明确
- 提醒能力
- 记录状态机
- 埋点口径

### 可以在开发中并行细化
- 日签风格库
- 森林视觉细节
- 后台看板样式

### 上线前必须闭环
- 内容审核流
- 主流程联调
- 数据回收验证
- 隐私与风控说明

## 8. 开发移交时各角色的接包顺序建议

### 产品

1. 先确认 [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>) 与 [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>) 已是最终移交口径
2. 再确认 [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>) 与 [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>) 已完成

### 设计

1. 先确认 [prototype-overview.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/prototype-overview.md>)、[mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)、[admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>) 已回写到最新结论
2. 再确认 [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>) 不存在越界页面

### 前后端与测试

1. 统一从 [dev-handoff-package-index.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-package-index.md>) 进入本次接包材料
2. 按 [dev-handoff-meeting-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-meeting-template.md>) 在移交会上确认范围、字段、依赖和行动项
3. 后端可优先使用 [backend-handoff-brief.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/backend-handoff-brief.md>) 快速进入本轮服务端范围
4. 如果要判断是否已经能正式拆后端任务，再用 [backend-task-splitting-prereq-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/backend-task-splitting-prereq-checklist.md>) 做一次门槛检查
