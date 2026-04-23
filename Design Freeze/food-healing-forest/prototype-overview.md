# 食愈森林 M1 原型包总览

## 1. 文档目标

- 为 `M1 设计与接口冻结` 提供一套可评审的低保真原型包。
- 先把 `MVP` 的页面结构、页面关系、关键状态和后台最小操作流固定下来。
- 本轮产物用于产品、设计、研发、测试对齐，不替代后续高保真视觉稿。

## 2. 当前阶段判断

- 当前主阶段仍为 `execution_alignment`
- 当前子目标进入 `M1 设计冻结准备`
- 当前 Gate 仍为 `Conditional Go`
- 原因：`M0` 的 3 个 `P0` 阻塞项已有决策稿，但尚未形成正式会审结论

## 3. 本轮原型范围

### 3.1 小程序 MVP 范围

- `晨光首页`
- `发起记录页`
- `饭后补感受页`
- `手帐列表 / 记录详情`
- `森林页`

### 3.2 后台 MVP 范围

- `后台首页总览`
- `日签生成与审核`
- `标签与提醒规则`
- `记录与转化看板`
- `敏感记录处置台`

### 3.3 本轮明确不展开

- `食方`
- `一分钟正念`
- `今日宜食`
- `月度洞察`
- `树洞信箱`
- `食材红绿灯`
- 任何高保真视觉和插画风格细化

## 4. 关键原型假设

1. 本轮原型严格按 `MVP` 版本规划执行，不按远期完整产品铺页面。
2. 小程序本轮默认采用 `晨光 / 手帐 / 森林` 三入口，不把 `食方` 放进当前底部主导航。
3. 饭后提醒是增强链路，不是完整记录闭环的唯一前提。
4. 后台默认不向普通角色暴露原始高敏感内容。
5. 若前台暂不开放删除记录，后台必须具备人工删除与审计入口。

## 5. 原型产物清单

- [mini-program-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/mini-program-wireframes.md>)
- [admin-console-wireframes.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/admin-console-wireframes.md>)
- [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
- [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)

## 6. 评审时优先确认的事

- 首页是否足够轻，且能稳定把用户引到记录动作
- 发起记录是否已经压缩到最低心智负担
- 饭后补感受是否同时支持“提醒进入”和“手动回补”
- 手帐是否能清楚区分 `待补` 与 `已完成`
- 森林页是否承担反馈而不是变成复杂玩法页
- 后台是否只覆盖 `内容生成审核 + 规则维护 + 提醒策略 + 看板 + 敏感处置`

## 7. 当前建议

- 先用这套低保真原型完成 `M1` 评审，再进入高保真和接口冻结。
- 如果 `M0` 最终拍板结果与本轮假设冲突，优先回写本目录原型文档，不要直接带着旧原型进入研发评审。
