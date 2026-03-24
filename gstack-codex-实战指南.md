# 把 Codex 变成一支 AI 软件战队：Gstack 安装、用法与实战示例

## 这是什么

[gstack](https://github.com/garrytan/gstack) 不是单个技能，而是一整套围绕“想法梳理、方案评审、代码审查、QA、发布、复盘”的 AI 工作流技能包。它的核心思路很像给 Codex 配一支虚拟团队：产品负责人、技术负责人、设计评审、代码审查员、QA、发布工程师，各司其职。

如果你只是想快速理解一句话：

> gstack 的价值，不是“多几个提示词”，而是把一条完整的软件交付流程塞进 Codex。

---

## 这次我已经帮你做了什么

我采用的是 **repo-local 安装**，也就是把 gstack 安装到当前项目里，而不是装到全局目录。这样做的好处是：

- 当前项目可直接使用
- 以后这个仓库迁移、备份、协作都更清楚
- 不会和你其它项目的全局技能混在一起

本次安装结果：

- gstack 源码目录：`.agents/skills/gstack`
- 生成后的 Codex 技能入口目录：`.agents/skills/`
- 浏览器二进制：`.agents/skills/gstack/browse/dist/browse.exe`

已经生成的主要技能包括：

- `gstack-office-hours`
- `gstack-plan-ceo-review`
- `gstack-plan-eng-review`
- `gstack-plan-design-review`
- `gstack-review`
- `gstack-qa`
- `gstack-qa-only`
- `gstack-design-review`
- `gstack-ship`
- `gstack-land-and-deploy`
- `gstack-retro`
- `gstack-investigate`
- `gstack-browse`
- `gstack-cso`
- `gstack-careful`
- `gstack-freeze`
- `gstack-guard`
- `gstack-unfreeze`
- `gstack-upgrade`

---

## 先说结论：你接下来要做什么

最重要的一步只有一条：

**重启 Codex 或重新开一个新会话。**

原因有两个：

- 新安装的技能需要让 Codex 重新扫描 `.agents/skills/`
- 这次安装补了 `bun`，新终端会自动拿到它的 PATH

如果你不重启，文档在、技能也在，但当前会话未必会自动识别到。

---

## Windows 环境注意事项

这套仓库在 Windows 下可以跑，但要记住它的前置条件：

- 需要 `Git`
- 需要 `Node.js`
- 需要 `Bun`
- 最好通过 `Git Bash` 或 `WSL` 跑它的 `setup`

这次安装里我额外处理了两个 Windows 细节：

1. 机器里原本有 `node`，但没有 `bun`
2. `Git Bash` 没有在 PATH 里，需要显式调用

所以如果你以后手动重装，最稳妥的方式仍然是进入 `gstack` 目录后重新执行：

```bash
cd .agents/skills/gstack
./setup --host codex
```

如果是 PowerShell，建议先切到 Git Bash 再执行。

---

## Codex 里怎么用

### 方式 1：直接点名技能

这是最稳的用法，适合 Codex：

```text
请使用 gstack 的 office-hours 技能，帮我梳理这个产品想法：……
```

```text
请使用 gstack 的 review 技能，审查我当前分支相对 main 的改动。
```

```text
请使用 gstack 的 qa 技能，访问 https://staging.example.com 做一轮回归测试。
```

### 方式 2：按 gstack 的 slash 风格表达

gstack 的原始设计是围绕 `/office-hours`、`/review`、`/qa` 这种命令名来的。在 Codex 里，最保险的说法是：

```text
按 gstack 的 /office-hours 工作流来做
按 gstack 的 /review 工作流来做
按 gstack 的 /qa 工作流来做
```

这样即便宿主不是原生 slash-command 风格，模型也更容易匹配到对应技能。

---

## 我建议你这样用 gstack

### 1. 想法阶段

先用：

- `office-hours`
- `plan-ceo-review`
- `plan-eng-review`
- `plan-design-review`

这四个技能适合把“模糊想法”变成“能落地的方案”。

推荐顺序：

1. `office-hours`：先把问题和机会想清楚
2. `plan-ceo-review`：判断方向、边界和产品野心
3. `plan-eng-review`：补齐架构、边界、风险、测试
4. `plan-design-review`：补齐交互状态、视觉质量、避免 AI 味过重

### 2. 编码完成后

重点用：

- `review`
- `investigate`
- `design-review`
- `qa`

理解方式很简单：

- `review`：盯代码
- `investigate`：查根因
- `design-review`：盯界面质量
- `qa`：盯真实流程

### 3. 发布与收尾

重点用：

- `ship`
- `land-and-deploy`
- `document-release`
- `retro`

这四个更像是“把活做完整”的后半程。

---

## 最值得先记住的 8 个技能

| 技能 | 适合什么时候用 | 一句话理解 |
|---|---|---|
| `office-hours` | 还在想做什么 | 像 YC 合伙人一样拷问你的想法 |
| `plan-ceo-review` | 想把方向做大或做准 | 站在创始人视角重审产品 |
| `plan-eng-review` | 要开工前 | 站在技术负责人视角补方案漏洞 |
| `review` | 写完代码后 | 对当前 diff 做预合并审查 |
| `investigate` | 出 bug 了 | 先找根因，再决定怎么修 |
| `qa` | 要验收功能 | 真开浏览器做流程测试 |
| `ship` | 准备提 PR | 跑测试、补覆盖、整理发布动作 |
| `retro` | 一周结束后 | 做一次工程复盘 |

---

## 可直接复制的示例

### 示例 1：把一个产品想法梳理成可执行方案

```text
请使用 gstack 的 office-hours 技能，帮我梳理一个“餐饮门店经营看板”产品想法。
我希望它能服务连锁餐饮老板，解决门店销量、库存和员工排班分散的问题。
```

### 示例 2：让 gstack 从 CEO 视角重新看需求

```text
请使用 gstack 的 plan-ceo-review 技能，帮我评审这个功能方向：
“给餐饮 SaaS 增加一个数据大屏首页”。
请重点判断这个需求是不是太表面，真正应该解决的问题是什么。
```

### 示例 3：让 gstack 从工程角度补齐方案

```text
请使用 gstack 的 plan-eng-review 技能，审查我现在这个方案。
我需要你重点关注：数据流、边界条件、失败重试、权限隔离、测试策略。
```

### 示例 4：对当前分支做代码审查

```text
请使用 gstack 的 review 技能，审查我当前分支相对 main 的 diff。
优先关注：并发问题、空值处理、权限校验、数据库写入风险。
```

### 示例 5：系统化排查一个 bug

```text
请使用 gstack 的 investigate 技能，帮我查一个问题：
下单接口偶发重复扣库存，但我还不确定根因。请先做调查，不要直接先改代码。
```

### 示例 6：真实做一轮 QA

```text
请使用 gstack 的 qa 技能，访问 https://staging.example.com，
围绕“登录 -> 下单 -> 支付 -> 订单详情”做一轮回归测试，并输出问题清单。
```

### 示例 7：发布前收尾

```text
请使用 gstack 的 ship 技能，帮我检查当前分支是否具备提 PR 条件。
如果测试覆盖不足，也请直接指出来。
```

### 示例 8：一周结束做复盘

```text
请使用 gstack 的 retro 技能，基于当前仓库最近一周的提交记录做一次复盘：
关注提交节奏、测试占比、热点文件和可能的风险区域。
```

---

## 一个顺手的工作流模板

如果你想真正把 gstack 用起来，我建议照这个顺序走：

1. `office-hours`
2. `plan-ceo-review`
3. `plan-eng-review`
4. 开发实现
5. `review`
6. `qa`
7. `ship`
8. `retro`

你可以把它理解成：

**先想清楚，再写代码；写完以后，不是立刻合并，而是先审、先测、再发。**

---

## 常见问题

### 1. 为什么我已经安装了，但 Codex 没反应？

优先检查三件事：

1. 你有没有重启 Codex
2. 当前仓库下是否存在 `.agents/skills/`
3. `gstack` 是否已经完成 `setup --host codex`

### 2. 如果某些技能识别不到怎么办？

直接在提示里显式点名：

```text
请使用 gstack 的 review 技能……
```

这种方式通常比只写“帮我 review 一下”更稳。

### 3. 如果浏览器相关能力异常怎么办？

重新执行：

```bash
cd .agents/skills/gstack
./setup --host codex
```

这会重新生成技能并检查 Playwright/Chromium。

### 4. 如果以后想升级 gstack 怎么办？

可以重新进入 gstack 目录拉最新代码后再跑一次 setup，或者让 Codex 使用 `gstack-upgrade` 技能。

---

## 适合你的起手式

如果你现在就想开始，我建议第一句直接用这个：

```text
请使用 gstack 的 office-hours 技能，帮我把 food-world-pro 这个项目的目标、用户、核心场景和 MVP 范围梳理清楚。
```

这句最适合拿来验证 gstack 是否已经真正“活”起来了。

---

## 最后一句

如果普通 Codex 像“很能写代码的助手”，那 gstack 更像“给 Codex 加上一整套工程组织能力”。

它最强的地方不是单点能力，而是把“想法 -> 方案 -> 实现 -> 审查 -> QA -> 发布 -> 复盘”串成了一条线。
