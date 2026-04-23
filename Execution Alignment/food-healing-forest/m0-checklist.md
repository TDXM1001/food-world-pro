# 食愈森林 M0 阻塞项确认清单

## 1. 会议目标

- 在正式进入 MVP 设计冻结和开发承诺前，确认 3 个 P0 阻塞项。
- 输出可执行结论，而不是只做讨论记录。
- 明确哪些结论已锁定，哪些需要降级方案，哪些会导致 MVP 边界调整。

## 2. 参会角色建议

- 产品
- 小程序前端
- 服务端 / 后台
- 测试
- 设计
- 如有条件，补充安全 / 合规 / 运维相关角色

## 3. 会议前准备

### 3.1 需要提前阅读的材料
- [prd.md](</e:/my-project/food-world-pro/Project Requirements/food-healing-forest/prd.md>)
- [version-split.md](</e:/my-project/food-world-pro/Release Planning/food-healing-forest/version-split.md>)
- [blocking-issues.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/blocking-issues.md>)
- [m0-meeting-chair-summary.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-meeting-chair-summary.md>)
- [reminder-capability-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/reminder-capability-decision.md>)
- [privacy-sensitive-data-boundary-decision.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/privacy-sensitive-data-boundary-decision.md>)

### 3.2 需要提前准备的信息
- 平台提醒能力说明
- 图片上传和存储方案草案
- 敏感数据处理约束
- 记录状态流转初稿

## 4. 会议输出要求

- 每个阻塞项都必须形成以下四类结论：
  - 结论：`Go / Conditional Go / No Go`
  - 方案：采用什么实现路径
  - 降级：如果主方案不可行，降级怎么做
  - 影响：是否改变 MVP 边界或成功指标解释方式

## 5. 阻塞项确认清单

## 阻塞项 1：饭后提醒能力

### 要确认的问题
1. 当前目标小程序平台是否支持饭后提醒触达？
2. 需要什么授权、订阅或触发条件？
3. 是否存在频次限制、时间限制、触达成功率问题？
4. 如果不能稳定触达，是否有可接受的替代方案？

### 必须给出的结论
- 主方案是什么
- 替代方案是什么
- 是否影响 `PRD-006` 与 `PRD-016`
- 是否影响 MVP 对“完整记录率”的验证解释

### 推荐判定标准
- `Go`
  - 有明确触达能力
  - 用户授权路径和触发方式清晰
  - 能满足 MVP 基本验证需要

- `Conditional Go`
  - 能做，但限制较多
  - 需要调整提醒文案、频次或回填预期
  - 需要同步修订验收口径

- `No Go`
  - 无法稳定实现
  - 或实现代价与首版目标明显不匹配
  - 需要回到版本边界调整 MVP

### 若结论为 No Go 的处理建议
- 将“饭后补感受”从强提醒闭环改为弱提醒或被动回访
- 重新定义 MVP 成功指标
- 回到版本规划重新评估首版验证路径

## 阻塞项 2：记录状态定义

### 要确认的问题
1. 一条记录从创建到完成会经历哪些状态？
2. 记录状态和提醒状态是否分开定义？
3. 哪个状态代表“完整记录”？
4. 哪些状态会触发森林成长？
5. 看板统计口径如何对应这些状态？

### 必须给出的结论
- 记录状态表
- 提醒状态表
- 状态转换规则
- 埋点与统计口径的状态映射

### 推荐最小状态集
- 记录状态：
  - `draft`
  - `submitted`
  - `awaiting_post_meal_feedback`
  - `completed`
  - `failed`

- 提醒状态：
  - `scheduled`
  - `sent`
  - `opened`
  - `expired`

### 推荐判定标准
- `Go`
  - 前后端、测试、数据口径可共用同一套状态定义

- `Conditional Go`
  - 核心状态已清楚，但个别边界还要补

- `No Go`
  - 状态口径仍不统一
  - 无法支撑联调和指标统计

## 阻塞项 3：隐私与敏感数据边界

### 要确认的问题
1. 餐图、情绪标签、身体感受是否需要特别提示或授权？
2. 哪些数据需要长期保存，哪些只需业务必要保存？
3. 是否需要删除、撤回、匿名化能力？
4. 日志、看板和后台是否能直接查看用户敏感数据？
5. 树洞虽不在 MVP，但是否要提前定义同类数据边界？

### 必须给出的结论
- 数据分类
- 存储边界
- 前台提示方式
- 后台可见范围
- 删除或停用策略

### 推荐判定标准
- `Go`
  - 数据处理边界清楚
  - 不会阻塞设计、开发和上线说明

- `Conditional Go`
  - 主口径清楚，但细则仍需补充
  - 可先进入设计冻结，不建议直接承诺上线

- `No Go`
  - 核心数据边界不清楚
  - 会直接影响功能设计或合规风险

## 6. 建议会议议程

### 0-5 分钟
- 对齐会议目标和期望输出

### 5-20 分钟
- 确认饭后提醒能力

### 20-35 分钟
- 确认记录状态定义

### 35-50 分钟
- 确认隐私与敏感数据边界

### 50-60 分钟
- 汇总结论、未决项、责任人和截止时间

## 7. 会后必须产出

- 决策记录
- 更新后的阻塞项状态
- 若有必要，更新 PRD / 版本切分 / 执行对齐文档
- 按 [m0-post-meeting-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-post-meeting-writeback-checklist.md>) 完成会后回写

## 8. 当前建议

- 这场会的目标不是“把所有细节聊完”，而是把会阻塞下一阶段的关键前提锁住。
- 如果 3 个阻塞项中有任意 1 项达到 `No Go`，就不要继续往开发承诺推进。
