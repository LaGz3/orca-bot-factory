# bot-factory

**用“状态机 + 4 级决策树 + 本地 Git 红线”批量孵化全自治 AI Bot 的开源提示词与工程模板库。**

> 告别每次开新方向都要从零磨 Prompt、每天给 AI 当“传话筒”。
> 把任意本地 AI Agent（**ORCA Bot / Claude Code / Cursor / Codex / Antigravity**）从**被动聊天工具**改造成**主动推进项目的全自治负责人**——AI 干 80% 重复推进，你只负责最后 20% 验收拍板。

---

## 1. 先搞懂：仓库里 3 个核心文件分别怎么用？

很多人拿到提示词仓库会懵：“这么多 `.md`，到底哪个贴给 AI、哪个放文件夹里？”看下面这张表 10 秒就懂：

| 文件 | 它是干嘛的？ | 放哪里 / 怎么用？ |
| --- | --- | --- |
| [`core/META_PROMPT.md`](core/META_PROMPT.md) | **提示词编译器**（元提示词） | **发给任意大模型**（ChatGPT / Gemini / Claude），把你的 4 行口语需求自动编译成定制 `SOUL.md` |
| [`core/SOUL_TEMPLATE.md`](core/SOUL_TEMPLATE.md) | **全自治灵魂母版** | 想手动微调时直接复制，替换里面的 `{{ }}` 后，**贴进 Bot 的系统提示词 / `SOUL.md` / `CLAUDE.md`** |
| [`core/BOARD_TEMPLATE.md`](core/BOARD_TEMPLATE.md) | **状态机看板模板** | 放在每个项目根目录（命名 `00_运营看板.md`），**无需手写**——Bot 首次开机交接时会自动创建并持续更新 |

---

## 2. 三种上手方式（从 1 分钟到批量孵化）

### 方式 1：直接抄作业（1 分钟最快体验）
1. 在下面「实战案例矩阵」里挑一个最接近你需求的案例（如科研论文追踪、财报拆解、独立开发、求职面试）。
2. 复制该文件全文，把第一行的 `{{YOUR_PROJECT_PATH}}` 改成你电脑上的真实项目目录路径。
3. 粘贴进你的 Bot 灵魂/规则配置，然后发送 [`core/META_PROMPT.md`](core/META_PROMPT.md) 中的**「通用冷启动交接指令」**即可开工。

### 方式 2：定制你自己的专属自治 Bot（3 分钟）
1. 打开 [`core/META_PROMPT.md`](core/META_PROMPT.md)，复制「一、灵魂编译元提示词」代码块。
2. 只改底部的 **4 行需求**（目标角色、本地路径、交付标准与禁忌、验收方式），发给任意大模型。
3. 把大模型吐出的 `SOUL.md` 贴进你的 Bot 设置，再发送「二、通用冷启动交接指令」。
4. **从此告别长 Prompt**：以后每次推进项目，聊天框只需发两个字——**`继续`**（或直接丢修改意见/反馈数据）。

### 方式 3：进阶玩法——搭建你自己的“母体 Bot工厂”（30 秒/个）
如果你同时推进多个方向，可以用 [`core/META_PROMPT.md`](core/META_PROMPT.md) 先编译一个专门绑定本仓库目录的“母体 Bot”，让它读取 `core/` 母版，在你提出一句话需求后自动创建目标目录、`.gitignore`、`00_运营看板.md`、执行 `git init` 并输出定制 `SOUL.md`。

---

## 3. 实战案例矩阵（4 大高频场景直接抄作业）

所有案例均已完成隐私脱敏，严格遵循同一套“6 模块自治骨架”：

| 场景分类 | 案例文件 | 适用人群 | Bot 核心自治流水线 |
| --- | --- | --- | --- |
| **科研学术** | [`examples/paper-radar-soul.md`](examples/paper-radar-soul.md) | 研究生 / 算法研究员 | 盯 arXiv 顶会 → 抓公式假设缺陷与消融漏洞 → 维护横向综述表 |
| **财务投资** | [`examples/finance-analyst-soul.md`](examples/finance-analyst-soul.md) | 财务学习 / 基本面研究 | 读官方年报/10-K 原文 → 三张表勾稽排雷 → 沉淀财务知识点卡 |
| **软件工程** | [`examples/github-indie-dev-soul.md`](examples/github-indie-dev-soul.md) | 独立开发者 / 程序员 | 读 MVP 路线图 → 单次最小代码改动 → 跑单测验证 → 更新 CHANGELOG |
| **求职面试** | [`examples/job-prep-coach-soul.md`](examples/job-prep-coach-soul.md) | 秋招 / 实习 / 跳槽备战 | 拆目标 JD 考点 → 每日 1 道场景深挖题 → 犀利批改 → 错题本加练 |

---

## 4. 为什么这套提示词能让 Bot 真正“全自治”？

普通 Prompt 每次对话都是失忆状态；`bot-factory` 给每个 Bot 装上了完整的 **6 模块工程骨架**：

```text
唤醒（你只需说“继续”或给反馈）
  │
  ▼
扫描项目目录 + 读取 00_运营看板.md（持久化状态机）
  │
  ├─▶ [优先级 1] 缺基建/未 git init ──▶ 自动搭目录、建看板并本地 commit
  ├─▶ [优先级 2] 有新反馈/验收结论  ──▶ 改稿/关闭积压，把教训写入看板“经验教训”栏
  ├─▶ [优先级 3] 仍有待验收积压     ──▶ 禁止盲目囤货，推送摘要请人类拍板
  └─▶ [优先级 4] 状态空闲           ──▶ 查重 → 调研 → 产出 → 自审 → 落盘 → 本地 git commit
                                          │
                                          ▼
                         输出极简三项验收单（交付物 / 一手依据 / 1–2 个风险点）
```

---

## 5. 跨平台适配指南

这套规范不绑定任何单一软件，只要工具支持**系统提示词 + 本地文件读写 + 终端命令**即可直接运行：

- **ORCA Bot**：直接粘贴进 Bot 的 `设置 → 灵魂（SOUL.md）`，并允许项目内文件读写与本地终端权限。
- **Claude Code**：保存为目标项目根目录的 `CLAUDE.md`。
- **Cursor / Windsurf**：放入 `.cursor/rules/autonomous-agent.mdc`（开启 Always Apply）。
- **OpenAI Codex / OpenClaw**：保存为项目根目录的 `AGENTS.md`。
- **Antigravity**：配置为 Workspace Rules 或自定义 Skill。

---

## 6. 仓库结构与安全红线

```text
bot-factory/
├── README.md                        # 使用指南、架构图与案例矩阵
├── .gitignore                       # 默认排除密钥、大体积媒体与 local/ 私有目录
├── core/
│   ├── SOUL_TEMPLATE.md             # 通用全自治 SOUL.md 母版
│   ├── META_PROMPT.md               # 30 秒灵魂编译元提示词 + 交接指令 + 排坑指南
│   └── BOARD_TEMPLATE.md            # 00_运营看板.md 标准状态机模板
└── examples/
    ├── paper-radar-soul.md          # 案例 1：顶会论文追踪与缺陷拆解官
    ├── finance-analyst-soul.md      # 案例 2：财报与基本面研报拆解员
    ├── github-indie-dev-soul.md     # 案例 3：独立开发 Micro-SaaS 推进官
    └── job-prep-coach-soul.md       # 案例 4：求职面试全自治备战教练
```

### 安全与开源原则（NEVER 红线）
- **零隐私泄露**：所有模板与案例均使用 `{{YOUR_PROJECT_PATH}}` 占位符，禁止写入真实本机路径、私人邮箱或 API Key。
- **人机权责隔离**：AI 仅负责本地搜集、起草、测试与本地 `git commit` 留痕；**`git push`、删档及一切对外发布动作永远保留在人类手中**。

## License

MIT
