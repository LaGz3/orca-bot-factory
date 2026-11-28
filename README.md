<div align="center">

# orca-bot-factory

**专为 ORCA Bot 打造的全自治 Agent 建造工厂——用 `SOUL.md` + 看板状态机 + 本地 Git，把 ORCA Bot 升级为无人值守的项目负责人**

*Turn **ORCA Bots** into autonomous project owners using `SOUL.md`, a 4-level decision tree, Markdown state machine, and local Git guardrails. (Also works with Claude Code, Cursor, Codex & Antigravity.)*

[![Built for ORCA Bot](https://img.shields.io/badge/Built%20for-ORCA%20Bot-6366f1.svg)](#四orca-bot-原生-5-步上手指南)
[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)
[![Zero Dependencies](https://img.shields.io/badge/Dependencies-Zero-brightgreen.svg)](#二为什么这套框架最契合-orca-bot)
[![Also Works With](https://img.shields.io/badge/Also%20Works%20With-Claude%20Code%20%7C%20Cursor%20%7C%20Codex-orange.svg)](#六跨平台-10-秒兼容指南)
[![PRs Welcome](https://img.shields.io/badge/PRs-Welcome-ff69b4.svg)](#欢迎贡献你的-orca-bot-灵魂)

[ORCA 5 步上手](#四orca-bot-原生-5-步上手指南) · [真实运行演示](#三它跑起来到底长什么样真实效果演示) · [6 大实战案例抄作业](#五6-大高频场景实战案例直接抄作业) · [ORCA 避坑 FAQ](#八orca-高频避坑-faq)

</div>

---

## 一、为什么你的 ORCA Bot 还只是“问一句动一下的聊天框”？

很多人在 ORCA 里建了 Bot、写了 `SOUL.md`，用下来却发现还是得每天给 AI 当“传话筒”：
- 每次对话都得重新喂网址、写长指令，AI 干完一步就停下来反问“接下来需要我做什么？”；
- Bot 默认工作区和你的本地项目目录隔离，聊完的内容全埋在对话流里，没沉淀成任何资产；
- 想配斜杠命令（如 `/选题`），结果 ORCA 报错“没有匹配的命令或技能”；想挂左侧 `自动化` 定时跑，却被权限弹窗或无状态记忆卡死。

**本质原因**：普通 `SOUL.md` 只写了“角色人设”，没给 ORCA Bot 装上 **项目目录绑定**、**持久化状态机**、**4 级决策树** 和 **Git 安全保险丝**。

`orca-bot-factory` 把这套实战跑通的工程骨架沉淀成纯 Markdown 模板——**让 ORCA Bot 自主完成 80% 的调研、产出、自审、落盘与本地 Git 留痕，你只花 3 分钟看验收单拍板。**

### 对比：普通 ORCA Bot 用法 vs. `orca-bot-factory` 全自治模式

| 维度 | 普通 `SOUL.md` 写法 | `orca-bot-factory` 全自治架构 |
| --- | --- | --- |
| **日常唤醒方式** | 每次写几百字长 Prompt、一步步催促 | 平时只需发两个字 **`继续`**（甚至挂 ORCA `自动化` 定时发 `继续`） |
| **工作区与资产沉淀** | 聊完散落在对话流，换个会话就失忆 | `SOUL.md` 首行绑定本地项目目录，按日期落盘为 Markdown + `00_运营看板.md` |
| **防卡死 / 防乱干** | 要么不动弹，要么乱囤一堆低质量草稿 | 内置 **4 级唤醒决策树** + **每次只做 1 个最小闭环** + **待验收防囤货锁** |
| **反馈持续进化** | 同样的错反复犯，每次都要重新叮嘱 | 你的修改意见自动写入看板“经验教训”栏，越跑越贴合你的口味 |
| **安全与防误改** | 放开权限怕删档、怕乱推远程仓库 | 每次变动自动本地 `git commit` 一键可回滚；硬红线 `NEVER` 禁止 `git push` 与外发 |
| **新建 Bot 效率** | 每开一个新方向都要从头磨半天提示词 | 内置「灵魂编译元提示词」，30 秒把 4 行口语需求编译成标准 `SOUL.md` |

---

## 二、为什么这套框架最契合 ORCA Bot？

市面上的 Agent 框架动辄要配 Docker、写几百行 Python 编排；`orca-bot-factory` 专门顺着 **ORCA 的原生机制** 做到了极致轻量化：

1. **100% 原生契合 ORCA 能力**：无缝串联 ORCA 的 **`SOUL.md` 灵魂 + 左侧 `项目` 目录 + 本地文件/终端权限 + `自动化` 定时触发 + 右侧 `通知` 验收**，不需要装任何复杂插件。
2. **零代码、零依赖、零黑盒**：全部是可读可改的纯 Markdown 文件，你可以 10 秒看懂每条规则并按需微调。
3. **一次编译，批量复制**：用 [`core/META_PROMPT.md`](core/META_PROMPT.md) 把任意想法（科研、财务、开发、求职、运营）30 秒编译成标准 ORCA `SOUL.md`，甚至可以孵化一个专门用来建新 Bot 的“母体 Bot 工厂”。
4. **放权不失控**：本地读写与 `git commit` 放权给 Bot 自动跑，**云端 `git push`、删档与一切外部发布永远锁死在人类手中**。

---

## 三、它跑起来到底长什么样？（真实效果演示）

以「科研论文雷达 ORCA Bot」为例，完成冷启动交接后，你的日常体验只有这样：

```text
👤 你（或 ORCA 左侧“自动化”定时触发）：继续

🤖 ORCA Bot（后台自主跑完，聊天框不刷屏）：
   1. 读取 00_运营看板.md → 确认无“待验收”积压
   2. 查重 02_精读拆解/ → 检索近 7 天 arXiv 目标领域新作并锁死 Top 1
   3. 精读原文拆解公式假设与消融漏洞 → 写入 02_精读拆解/2026-11-27-xxx.md
   4. 更新 03_横向综述对比表.md 与 00_运营看板.md（标记为“待验收”）
   5. 执行本地 git add & git commit -m "auto: 2026-11-27-xxx"

🔔 ORCA 弹出“任务完成”通知 → Bot 聊天框只输出极简三项验收单：
   ① 【核心评述（500字内）】结论：推荐关注思路，暂不复现……
   ② 【一手依据】arXiv 原文链接 / 官方代码仓 / Table 3 消融对比出处
   ③ 【需你拍板的风险点】实验未在长序列基准验证，疑似存在显存瓶颈……
   👉 看板已更新。请给出验收意见（通过 / 修改 / 作废），或直接回复“继续”，下次我将自动执行：[下一篇论文追踪]。

👤 你：通过，以后帮我重点关注带开源代码且单卡能跑的论文

🤖 ORCA Bot：已将上一篇标为“已通过”，并把“优先带开源代码 + 单卡可复现”写入看板【经验教训与策略迭代】栏……
```

**你不再是 AI 的操作工，而是只看验收单、拍板和给反馈的项目老板。**

---

## 四、ORCA Bot 原生 5 步上手指南

### 先看懂仓库里的 3 个核心文件

| 文件 | 角色定位 | 放哪里 / 怎么用？ |
| --- | --- | --- |
| [`core/META_PROMPT.md`](core/META_PROMPT.md) | **ORCA 灵魂编译器**（元提示词） | **发给任意大模型**，把你的 4 行需求自动编译成可直接贴进 ORCA 的定制 `SOUL.md` |
| [`core/SOUL_TEMPLATE.md`](core/SOUL_TEMPLATE.md) | **全自治 `SOUL.md` 母版** | 想手动精细调教时复制，替换 `{{ }}` 占位符后贴进 ORCA `设置 → 灵魂` |
| [`core/BOARD_TEMPLATE.md`](core/BOARD_TEMPLATE.md) | **`00_运营看板.md` 状态机模板** | 放在每个本地项目根目录，**无需手写**——Bot 首次冷启动交接时会自动创建并持续更新 |

---

### 5 步在 ORCA 跑通你的第一个全自治 Bot（约 3 分钟）

1. **新建并导入本地项目目录**
   - 在电脑本地建一个空项目文件夹（如 `D:\Projects\paper-radar`）。
   - 打开 ORCA，在左侧边栏 `项目` 旁点 `+` 导入该文件夹，方便随时查看 Bot 沉淀的 Markdown 与 Git 提交记录。

2. **获取定制 `SOUL.md`（二选一）**
   - **最快 1 分钟（直接抄作业）**：从下方 [第 5 节实战案例](#五6-大高频场景实战案例直接抄作业) 挑 1 份，把第一行 `{{YOUR_PROJECT_PATH}}` 改成你的本地文件夹路径。
   - **3 分钟自由定制**：复制 [`core/META_PROMPT.md`](core/META_PROMPT.md) 里的「灵魂编译元提示词」，只改底部 4 行需求发给任意大模型，拿到定制 `SOUL.md`。

3. **新建 ORCA Bot 并粘贴灵魂**
   - 在 ORCA 左侧 `Bots` 新建一个 Bot，进入右侧 `设置 → 灵魂（SOUL.md）` 点击编辑，粘贴上面的 `SOUL.md` 并保存。
   - *(关键)* 确保 `SOUL.md` 第一行已写死 `工作项目绝对路径：...`，彻底打通 Bot 与本地项目的访问边界。

4. **配置执行权限 + 发送冷启动交接指令**
   - 前期试跑可先保留默认审批模式观察它每一步改了什么；跑顺后在 `设置 → 智能体 → 权限` 放开本地文件读写与终端命令执行（安全由 `NEVER` 红线与本地 Git 兜底）。
   - 在该 Bot 聊天框发送下面这段**最后一次长指令**，正式交权开机：

```plaintext
从现在起，你全权接管本项目。请立刻按你的 SOUL.md 完成冷启动交接：
1. 检查并补齐项目目录、.gitignore、本地 git init，以及 00_运营看板.md（写入阶段目标与当前状态）。
2. 立刻运行一次“唤醒自检决策树”，自主补齐当前最缺的核心基建或完成第 1 个最小闭环产物，完成后本地 git commit。
3. 按规定格式交付极简验收单，并告诉我下一步你打算做什么。
```

5. **（可选进阶）挂接 ORCA 定时 `自动化`，彻底解放双手**
   - 点击 ORCA 左上角 `自动化` 新建定时任务（如每周一、三、五早上 08:30），执行对象选该 Bot，触发指令只填两个字：**`继续`**。
   - 保持右侧 `通知` 中的 `任务完成` 和 `无法完成` 开启。以后定时跑完弹窗提醒，你打开聊天框花 3 分钟看验收单拍板即可！

---

## 五、6 大高频场景实战案例（直接抄作业）

所有案例均已完成隐私脱敏，严格内置「4 级决策树 + 看板状态机 + 本地 Git 安全红线」，复制到 ORCA `SOUL.md` 改一行路径即可上岗：

| 场景 | 案例文件 | 适合谁？ | ORCA Bot 核心自治流水线 |
| --- | --- | --- | --- |
| **科研学术** | [`examples/paper-radar-soul.md`](examples/paper-radar-soul.md) | 研究生 / 算法研究员 | 盯 arXiv 与顶会新作 → 拒绝翻译腔，专抓公式假设缺陷与消融漏洞 → 维护横向综述表 |
| **财务研究** | [`examples/finance-analyst-soul.md`](examples/finance-analyst-soul.md) | 财务学习 / 基本面分析 | 只看官方年报/10-K 原文 → 三张表勾稽算账排雷 → 自动沉淀财务知识点卡片 |
| **软件工程** | [`examples/github-indie-dev-soul.md`](examples/github-indie-dev-soul.md) | 独立开发者 / 程序员 | 读 MVP 路线图 → 单次最小代码改动 → 跑通单测/构建验证 → 更新 `CHANGELOG.md` |
| **求职面试** | [`examples/job-prep-coach-soul.md`](examples/job-prep-coach-soul.md) | 秋招 / 实习 / 跳槽备战 | 拆目标 JD 考点矩阵 → 每日 1 道场景深挖题 → 面试官视角犀利批改 → 错题本加练 |
| **自媒体运营** | [`examples/media-ops-soul.md`](examples/media-ops-soul.md) | 小红书 / 抖音图文创作者 | 只读质检上游内容 Bot 产出 → 6 项硬指标守门 + 周 3 更黄金档排期 → 24h 数据复盘满 3 篇反哺调优 |
| **提示词工程** | [`examples/prompt-optimizer-soul.md`](examples/prompt-optimizer-soul.md) | 全场景 AI 重度用户 | 先 1–2 句意图复述 + 2–4 个带选项反问补齐条件 → 零脑补精准改写 → 沉淀个人提示词资产库 |

> **高阶玩法：在 ORCA 里建一个“母体 Bot工厂”**
> 把本仓库克隆并导入 ORCA，用 [`core/META_PROMPT.md`](core/META_PROMPT.md) 编译一个绑定本仓库的“母体 Bot”。以后想开任何新项目，只需对它说一句人话，它会自动读取 `core/` 母版，替你在本地建目录、写 `.gitignore` 和看板、执行 `git init`，并直接吐出可直接复制的新 Bot `SOUL.md`！

---

## 六、跨平台 10 秒兼容指南

虽然本项目以 **ORCA Bot** 为第一优先级打磨，但因为核心全是纯 Markdown 规范，同样可以无缝用于任意支持本地读写与终端的 Agent 工具：

| 工具 / 客户端 | 放置位置 | 说明 |
| --- | --- | --- |
| **ORCA Bot（原生推荐）** | Bot `设置 → 灵魂（SOUL.md）` | 原生配合 `项目`、`自动化`、`通知`、`记忆` 完整闭环 |
| **Claude Code** | 目标项目根目录 `CLAUDE.md` | 放行本地读写与 `git add/commit`，禁止 `git push` |
| **Cursor / Windsurf** | `.cursor/rules/autonomous-agent.mdc` | 开启 Always Apply，配合 Agent 模式使用 |
| **OpenAI Codex / OpenClaw** | 目标项目根目录 `AGENTS.md` | 沙盒内本地读写与本地 `git commit` |
| **Antigravity** | Workspace Rules 或自定义 Skill | 直接绑定工作区目录即可运行 |

---

## 七、核心架构原理（为什么它稳且不失控？）

`orca-bot-factory` 用确定性的“看板状态机 + 4 级唤醒决策树”约束大模型的发散性：

```mermaid
flowchart TD
    A["唤醒 ORCA Bot（手动发“继续”或由“自动化”定时触发）"] --> B["扫描项目目录 + 读取 00_运营看板.md"]
    B --> C{"1. 缺基建或未 git init？"}
    C -- 是 --> C1["自动补齐目录 / 看板 / git init 并本地 commit"]
    C -- 否 --> D{"2. 本轮收到用户验收或修改反馈？"}
    D -- 修改/数据反馈 --> D1["修正产物 + 写入看板“经验教训”栏 + 本地 commit"]
    D -- 确认通过 --> D2["将积压项标为“已通过”"] --> F
    D -- 无新反馈 --> E{"3. 看板仍有“待验收”积压？"}
    E -- 是 --> E1["禁止盲目囤货：推送积压摘要请人类拍板"]
    E -- 否 --> F["4. 空闲：执行单次最小闭环（查重 → 调研 → 产出 → 自审 → 落盘 → 本地 commit）"]
    C1 --> G["同步更新 00_运营看板.md + 输出极简三项验收单"]
    D1 --> G
    E1 --> G
    F --> G
```

### 安全与可控性红线（NEVER）
所有模板强制内置 `NEVER` 安全边界：
- **目录隔离**：仅读写 `SOUL.md` 绑定的本地项目目录，绝不越界碰系统文件。
- **防误改回滚**：每次产物变更都在本地 `git commit`，随时可 `git diff` 审计或一键回滚。
- **人机权责锁死**：**NEVER 删除已有资产、NEVER 自动 `git push`、NEVER 未经明确批准对外发布或改动线上环境。**

---

## 八、ORCA 高频避坑 FAQ

<details>
<summary><b>Q1：在 ORCA 聊天框输入 `/选题` 等斜杠指令，提示“没有匹配的命令或技能”怎么办？</b></summary>

ORCA 输入框里的 `/` 只识别系统内置命令或已安装的 `技能`（Skills），写在 `SOUL.md` 里的普通文本不会被识别为斜杠命令。
**解决方案**：不要使用手动分段斜杠命令！使用本仓库的全自治 `SOUL.md`，彻底免去手动命令，日常只需发自然语言 **`继续`** 或直接提修改意见即可。
</details>

<details>
<summary><b>Q2：ORCA Bot 说找不到我的项目文件夹，或者把文件写到了别处？</b></summary>

ORCA 新建的 Bot 默认绑定它自己的独立工作区目录，不会自动关联左侧 `项目` 里的其他文件夹。
**解决方案**：必须在 `SOUL.md` 开头显式写明 `工作项目绝对路径：你的真实路径`（如 `D:\Projects\paper-radar`），Bot 就会精准读写你的本地项目目录。
</details>

<details>
<summary><b>Q3：Bot 每次干一半停下来弹窗等确认，或者老反问“请问先做哪一步”？</b></summary>

检查两处：
1. 是否已发过「首次冷启动交接指令」并生成了 `00_运营看板.md`；
2. 在 ORCA 右侧 `设置 → 智能体 → 权限` 中，默认权限会在每次读写和运行命令前拦截确认；确认规则跑顺后放开项目内自动执行权限，即可真正无人值守运行。
</details>

<details>
<summary><b>Q4：为什么我发了“继续”，它却一直提醒我验收上一份内容、不产新的？</b></summary>

这是**防囤货保护锁（决策树第 3 级）**在生效，防止 Bot 在你没验收前不断堆砌垃圾内容。明确回复 **`通过，继续`** 或 **`作废这篇，继续下一篇`**，它会自动更新看板状态并立刻推进下一轮。
</details>

<details>
<summary><b>Q5：想在本地存自己私用的 Bot 灵魂，怎么防止误推到公开 GitHub 仓库？</b></summary>

本仓库 [.gitignore](.gitignore) 已默认排除 `.env`、`*.key`、图片及 `local/` 目录。把带真实本机路径或私有业务的 `SOUL.md` 放进本地 `local/` 目录即可完全隔离。
</details>

---

## 仓库结构

```text
orca-bot-factory/
├── README.md                        # ORCA 原生教程、效果演示、架构图与避坑 FAQ
├── .gitignore                       # 默认排除密钥、大体积媒体与 local/ 私有目录
├── core/
│   ├── SOUL_TEMPLATE.md             # 通用全自治 ORCA SOUL.md 母版
│   ├── META_PROMPT.md               # 30 秒灵魂编译元提示词 + 交接指令 + 排坑指南
│   └── BOARD_TEMPLATE.md            # 00_运营看板.md 标准状态机模板
└── examples/
    ├── paper-radar-soul.md          # 案例 1：顶会论文追踪与缺陷拆解官
    ├── finance-analyst-soul.md      # 案例 2：财报与基本面研报拆解员
    ├── github-indie-dev-soul.md     # 案例 3：独立开发 Micro-SaaS 推进官
    ├── job-prep-coach-soul.md       # 案例 4：求职面试全自治备战教练
    ├── media-ops-soul.md            # 案例 5：自媒体质检、排期与数据复盘管家
    └── prompt-optimizer-soul.md     # 案例 6：先反问对齐再改写的提示词优化管家
```

---

## 欢迎贡献你的 ORCA Bot 灵魂

如果你在 ORCA 里跑通了好用的垂直场景自治 Bot（如英语精读教练、竞品监控雷达、开源 Issue 管家、健身饮食复盘等）：

- 欢迎直接提交 **Pull Request**，把脱敏后的 `*-soul.md`（本地路径统一替换为 `{{YOUR_PROJECT_PATH}}`）放进 `examples/` 目录；
- 如果这套极简框架帮你把 ORCA Bot 从“聊天玩具”真正变成了“自动推进项目的数字员工”，**欢迎点一个 ⭐ Star 支持**，也欢迎在 Issue 中分享你的实战玩法！

## License

MIT
