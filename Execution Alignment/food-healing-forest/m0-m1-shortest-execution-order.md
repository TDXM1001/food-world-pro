# 食愈森林 M0 到 M1 最短执行顺序清单

## 1. 文档目标

- 把“从现在到正式开发移交前”最短需要走完的动作压缩成一条执行链。
- 避免团队继续在“是不是该开发了”这个问题上反复空转。
- 作为产品、设计、前后端、测试共同遵循的最小推进顺序。

## 2. 当前判断

- 当前阶段：`execution_alignment`
- 当前 Gate：`Conditional Go`
- 当前不是正式开发阶段，而是“`M0 / M1` 最后收口阶段”

## 3. 最短执行顺序

### 第 1 步：开 `M0 阻塞项确认会`

- 目标：锁住不会再反改 `MVP` 主闭环的三条前提
- 必拍板事项：
  - 饭后提醒能力
  - 记录状态机
  - 隐私与敏感数据边界
- 会前材料：
  - [m0-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-checklist.md>)
  - [m0-meeting-chair-summary.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-meeting-chair-summary.md>)
  - [m0-recommended-decision-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-recommended-decision-draft.md>)

### 第 2 步：回写 `M0` 正式结论

- 目标：把口头拍板变成正式文档事实
- 必做动作：
  - 用 [m0-decision-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-decision-template.md>) 记录正式结论
  - 按 [m0-post-meeting-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m0-post-meeting-writeback-checklist.md>) 完成回写
- 至少同步到：
  - `PRD`
  - `blocking-issues`
  - `page-inventory`
  - `interface-field-placeholders`
  - `alignment-plan`

### 第 3 步：开 `M1 设计与接口冻结评审`

- 目标：冻结 `MVP` 页面范围、后台范围、字段占位和主流程
- 本轮只看 `MVP`
- 必须确认：
  - 小程序是否按 `晨光 / 手帐 / 森林` 三入口理解
  - 后台是否只做 `ADM-01 ~ ADM-05`
  - `MP-04 手帐列表` 是否作为待补记录核心回流入口
  - 页面与接口映射是否完整
- 会前材料：
  - [m1-review-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-checklist.md>)
  - [m1-recommended-review-draft.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-recommended-review-draft.md>)
  - [page-inventory.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/page-inventory.md>)
  - [interface-field-placeholders.md](</e:/my-project/food-world-pro/Design Freeze/food-healing-forest/interface-field-placeholders.md>)

### 第 4 步：回写 `M1` 正式结论

- 目标：确保原型、页面、字段、执行文档全部统一
- 必做动作：
  - 用 [m1-review-record-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-review-record-template.md>) 记录正式结论
  - 按 [m1-post-review-writeback-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/m1-post-review-writeback-checklist.md>) 完成回写
- 至少同步到：
  - `prototype-overview`
  - `mini-program-wireframes`
  - `admin-console-wireframes`
  - `page-inventory`
  - `interface-field-placeholders`
  - `alignment-plan`
  - `owners-and-dependencies`

### 第 5 步：做正式开发移交前检查

- 目标：判断是否已经具备正式移交开发条件
- 使用清单：
  - [dev-handoff-readiness-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-readiness-checklist.md>)
  - [backend-task-splitting-prereq-checklist.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/backend-task-splitting-prereq-checklist.md>)
- 只要还有会改实现方式的未决项，就不能宣布正式开发

### 第 6 步：组织开发移交会

- 前提：第 5 步通过
- 使用材料：
  - [dev-handoff-package-index.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-package-index.md>)
  - [dev-handoff-meeting-template.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/dev-handoff-meeting-template.md>)
  - [backend-handoff-brief.md](</e:/my-project/food-world-pro/Execution Alignment/food-healing-forest/backend-handoff-brief.md>)

## 4. 哪一步之后才能算进入正式开发

- 不是 `M0` 结束后
- 不是 `M1` 开完会后
- 不是材料写得很多之后
- 只有在：
  - `M0` 已拍板并回写
  - `M1` 已评审并回写
  - 开发移交前检查通过
  - 开发移交会已明确责任人与依赖
- 才能算进入正式开发阶段

## 5. 当前最小结论

- 现在还没到正式开发那一步
- 现在最该做的是：`先完成 M0，再完成 M1`
- 在这两步完成前，研发都只适合做预研，不适合做正式任务拆分和排期承诺

## 6. 当前建议

- 如果你想最短路径往前推，就不要继续扩内容或再补大而全方案了。
- 直接按这份顺序清单推进，完成 `M0 -> M1 -> 移交检查 -> 移交会` 即可。
