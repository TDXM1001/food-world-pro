# 食愈森林 M1 接口字段占位清单

## 1. 文档目标

- 在 `M0` 未完全拍板前，先把 `MVP` 所需的核心对象和接口字段占位整理出来。
- 帮助前端、后端、测试在 `M1` 评审时对齐“需要什么数据”，而不是直接进入实现细节。
- 本文档不是最终接口文档，只是面向冻结阶段的结构草案。

## 2. 使用原则

- 字段命名优先复用 `PRD` 和状态机草案中的口径。
- 未拍板字段必须显式标记 `待 M0 确认`，不能假装已经定版。
- 接口按“够支撑 MVP 页面和核心流程”来收敛，不提前扩展远期能力。

## 3. 核心对象占位

### 3.1 `DailyCard`

- 用途：晨光首页日签展示
- 建议字段：
  - `card_id`
  - `date`
  - `title`
  - `body_text`
  - `image_url`
  - `status`
  - `fallback_used`
  - `published_at`

### 3.2 `MealRecord`

- 用途：一餐记录主对象
- 建议字段：
  - `record_id`
  - `user_id`
  - `meal_image_url`
  - `meal_time`
  - `mood_tags`
  - `post_meal_feeling_tags`
  - `business_status`
  - `completed_at`
  - `forest_growth_applied`
  - `deleted_at`
- 待 M0 确认：
  - `draft_local` 是否需要服务端草稿占位
  - 是否开放前台删除

### 3.3 `ReminderTask`

- 用途：饭后提醒任务
- 建议字段：
  - `reminder_id`
  - `record_id`
  - `user_id`
  - `reminder_status`
  - `reminder_planned_at`
  - `reminder_sent_at`
  - `reminder_opened_at`
  - `feedback_submitted_at`
  - `failure_code`
- 待 M0 确认：
  - `expired` 的阈值定义
  - 平台实际提醒链路和发送前提

### 3.4 `ForestSummary`

- 用途：森林页摘要展示
- 建议字段：
  - `user_id`
  - `plant_stage`
  - `continuous_days`
  - `completed_record_count_this_month`
  - `pending_record_count`
  - `latest_growth_at`

### 3.5 `TagOption`

- 用途：心情标签和饭后感受标签配置
- 建议字段：
  - `tag_id`
  - `tag_type`
  - `tag_name`
  - `display_order`
  - `enabled`

### 3.6 `DashboardSummary`

- 用途：后台首页与看板聚合
- 建议字段：
  - `date_range`
  - `home_view_users`
  - `record_start_rate`
  - `record_submit_count`
  - `complete_record_rate`
  - `reminder_sent_rate`
  - `reminder_backfill_rate`
  - `manual_backfill_rate`
  - `continuous_3d_users`
  - `continuous_7d_users`

### 3.7 `SensitiveCase`

- 用途：后台敏感记录处置台
- 建议字段：
  - `case_id`
  - `record_id`
  - `user_id`
  - `case_source`
  - `reason`
  - `case_status`
  - `assignee`
  - `created_at`
  - `resolved_at`

## 4. 小程序接口占位

### 4.1 获取晨光首页数据

- 建议接口：`GET /mini/home/overview`
- 最小返回：
  - `daily_card`
  - `pending_record_summary`
  - `record_entry_visible`

### 4.2 创建一餐记录

- 建议接口：`POST /mini/meal-records`
- 最小请求：
  - `meal_image_url`
  - `meal_time`
  - `mood_tags`
- 最小返回：
  - `record_id`
  - `business_status`
  - `reminder_attempted`
  - `reminder_status`

### 4.3 获取手帐列表

- 建议接口：`GET /mini/meal-records`
- 支持参数：
  - `date`
  - `cursor`
- 最小返回：
  - `today_records`
  - `history_records`

### 4.4 获取记录详情

- 建议接口：`GET /mini/meal-records/{record_id}`
- 最小返回：
  - `meal_record`
  - `reminder_task`
  - `feedback_summary`

### 4.5 提交饭后感受

- 建议接口：`POST /mini/meal-records/{record_id}/post-meal-feedback`
- 最小请求：
  - `post_meal_feeling_tags`
- 最小返回：
  - `record_id`
  - `business_status`
  - `forest_growth_applied`
  - `completion_feedback`

### 4.6 获取森林摘要

- 建议接口：`GET /mini/forest/summary`
- 最小返回：
  - `forest_summary`
  - `pending_record_summary`

### 4.7 获取标签配置

- 建议接口：`GET /mini/tag-options`
- 最小返回：
  - `mood_tags`
  - `post_meal_feeling_tags`

## 5. 后台接口占位

### 5.1 后台首页总览

- 建议接口：`GET /admin/dashboard/overview`
- 最小返回：
  - `dashboard_summary`
  - `content_status_summary`
  - `todo_summary`

### 5.2 生成日签

- 建议接口：`POST /admin/daily-cards/generate`
- 最小请求：
  - `date_range`
  - `count`
- 最小返回：
  - `job_id`
  - `generated_count`

### 5.3 查询日签列表

- 建议接口：`GET /admin/daily-cards`
- 支持参数：
  - `status`
  - `date_range`

### 5.4 审核并发布日签

- 建议接口：`POST /admin/daily-cards/{card_id}/review`
- 最小请求：
  - `action`
  - `edited_text`

### 5.5 标签与提醒规则

- 建议接口：
  - `GET /admin/rules/tag-options`
  - `POST /admin/rules/tag-options`
  - `GET /admin/rules/reminder`
  - `POST /admin/rules/reminder`

### 5.6 记录与转化看板

- 建议接口：`GET /admin/dashboard/conversion`
- 支持参数：
  - `date_range`

### 5.7 敏感记录处置

- 建议接口：
  - `GET /admin/sensitive-cases`
  - `GET /admin/sensitive-cases/{case_id}`
  - `POST /admin/sensitive-cases/{case_id}/resolve`
- 最小请求：
  - `action`
  - `reason`

## 6. 页面与接口映射

### 6.1 小程序映射

- `MP-01 晨光首页`
  - `GET /mini/home/overview`
- `MP-02 发起记录页`
  - `GET /mini/tag-options`
  - `POST /mini/meal-records`
- `MP-03 饭后补感受页`
  - `GET /mini/meal-records/{record_id}`
  - `POST /mini/meal-records/{record_id}/post-meal-feedback`
- `MP-04 手帐列表`
  - `GET /mini/meal-records`
- `MP-05 记录详情`
  - `GET /mini/meal-records/{record_id}`
- `MP-06 森林页`
  - `GET /mini/forest/summary`

### 6.2 后台映射

- `ADM-01 后台首页总览`
  - `GET /admin/dashboard/overview`
- `ADM-02 日签生成与审核`
  - `POST /admin/daily-cards/generate`
  - `GET /admin/daily-cards`
  - `POST /admin/daily-cards/{card_id}/review`
- `ADM-03 标签与提醒规则`
  - `GET /admin/rules/tag-options`
  - `POST /admin/rules/tag-options`
  - `GET /admin/rules/reminder`
  - `POST /admin/rules/reminder`
- `ADM-04 记录与转化看板`
  - `GET /admin/dashboard/conversion`
- `ADM-05 敏感记录处置台`
  - `GET /admin/sensitive-cases`
  - `GET /admin/sensitive-cases/{case_id}`
  - `POST /admin/sensitive-cases/{case_id}/resolve`

## 7. 当前仍不能定版的字段

- 提醒链路的真实发送前提与失败码口径
- `expired` 的时间阈值
- 是否允许补填后再次编辑
- 是否开放前台删除记录
- 敏感记录处置台的角色白名单与 SLA

## 8. 评审重点

- 是否已经覆盖所有 `MVP` 页面必需的数据，而没有超配
- 对象名、字段名、状态名是否与 PRD 口径一致
- 是否存在页面已经依赖、但文档里还没有占位的接口
- 是否把 `M0` 未决问题误写成了定版字段

## 9. 当前建议

- 用这份清单进入 `M1 接口冻结评审`，先锁对象和字段，再写正式 API 文档。
- 若 `M0` 结论有变化，优先更新 `MealRecord`、`ReminderTask`、`SensitiveCase` 这三类对象。
