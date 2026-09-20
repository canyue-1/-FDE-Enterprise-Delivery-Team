# FDE 企业交付专家团（FDE Enterprise Delivery Team）

把客户现场的问题，变成一条可验收、可回滚、可交接的交付链路。六人协作，覆盖从客户发现到生产上线与证据交付的完整链路。

一个可直接安装到 WorkBuddy 的 **Team 型专家包**。

---

## 团队构成

| 成员 ID | 花名 | 职业头衔 | 职责 |
|---------|------|---------|------|
| fde-delivery-team-lead | 甄落地 | 企业AI交付总监 | 任务分诊、编排调度、跨阶段裁决、交付包汇编 |
| fde-discovery-officer | 闻清源 | 客户发现官 | 客户现场发现、真问题定位、场景优先级与价值证明 |
| fde-solution-architect | 计周全 | AI方案架构师 | 方案选型、NFR/SLO、PoC→Production 决策门、行业方案与资产复用 |
| fde-agent-engineer | 陈稳当 | Agent工程专家 | 任务合同、Prompt 与消息设计、工具权限门禁、可靠性恢复、HITL |
| fde-integration-engineer | 连得顺 | 企业系统集成工程师 | 数据血缘、知识入库与 RAG、API/消息集成、幂等补偿、切换回滚 |
| fde-assurance-officer | 严守界 | 质量与安全官 | 评测回归、Trace 定位、安全边界、灰度、生产证据包 |

主理人为「甄落地」，负责任务分诊并按需把工作分派给其余五名成员。

---

## 功能

### 四条预设工作流

- **Workflow A · 新项目端到端交付**：问题定义（并行）→ 方案设计 → 实现设计（并行）→ 验证加固 → 汇编交付
- **Workflow B · 场景评估与立项**：价值判断 → 可行性量级 → 风险否决项 → 立项建议
- **Workflow C · Agent 上线攻坚**：可靠性设计 → 数据与集成根因 → 评测门槛与灰度预案
- **Workflow D · 故障复盘与加固**：Trace 定位根因层 → 定向调人 → 加固与复验

单点问题也可以直接路由到对应成员，不必走完整链路。

### 知识底座

随包附带 `fde-delivery-knowledge` Skill：

- `references/article-index.md` —— 《FDE 工程师成长指南》三阶十五模块 × 73 篇全量索引，含可点击原文链接、归档状态与缺篇清单
- `references/method-cheatsheet.md` —— 核心方法论速查表（问题合同、五维评分、三笔 ROI、五层选择树、NFR/SLO、三道决策门、Golden Set、Trace、幂等补偿、Source-of-Truth 等），每条标注出处篇号

### 交付裁决原则

- 先问值不值得，再问怎么做
- 质量与安全官对合规与越权风险有一票否决权
- 有分歧必须给明确结论，不得以「各有优劣」收尾
- 不过度设计：不需要 Agent 时就说不需要

---

## 仓库结构

```
.
├── .codebuddy-plugin/
│   └── plugin.json                     # 专家包清单（团队结构、成员、分类、引导语）
├── agents/                             # 六个角色的定义文件
│   ├── fde-delivery-team-lead.md
│   ├── fde-discovery-officer.md
│   ├── fde-solution-architect.md
│   ├── fde-agent-engineer.md
│   ├── fde-integration-engineer.md
│   └── fde-assurance-officer.md
├── avatars/                            # 团队与各成员头像（512×512 PNG）
├── skills/
│   └── fde-delivery-knowledge/         # 随包知识库
│       ├── SKILL.md
│       └── references/
│           ├── article-index.md
│           └── method-cheatsheet.md
├── settings.json
└── README.md
```

---

## 安装到 WorkBuddy

### 方式一：注册为本地专家（推荐）

1. 克隆本仓库：

   ```bash
   git clone <repo-url> fde-delivery
   ```

2. 放入本地专家目录。WorkBuddy 会把该目录作为「我的专家」的来源：

   | 平台 | 路径 |
   |------|------|
   | Windows | `%USERPROFILE%\.workbuddy\plugins\marketplaces\my-experts\plugins\` |
   | macOS / Linux | `~/.workbuddy/plugins/marketplaces/my-experts/plugins/` |

   ```bash
   cp -r fde-delivery ~/.workbuddy/plugins/marketplaces/my-experts/plugins/
   ```

3. 校验并注册（脚本随 WorkBuddy 内置的 `expert-manager` 技能提供）：

   ```bash
   python3 <expert-manager>/scripts/validate_expert.py <expert-dir>
   python3 <expert-manager>/scripts/register_expert.py <expert-dir>
   ```

4. **重启 WorkBuddy**，在左侧边栏「专家」→「我的专家」中即可看到「FDE 企业交付专家团」。若已能看到卡片，点进去时请**新建会话**，已开启的会话不会切换专家。

### 方式二：从 zip 导入

在 Releases 下载 `fde-delivery.zip`，通过 WorkBuddy 的专家导入入口加载。

---

## 使用示例

- 我手上有个企业AI项目，帮我从客户需求发现一路推到上线交付
- 帮我评估这个AI场景值不值得投入，把基线、TCO和风险成本算清楚
- 我的Agent上线后检索不准、没人用，帮我定位问题并给出加固方案
- 客户说要个智能客服，帮我判断这是不是真需求
- 改了 Prompt 怎么知道有没有变好？帮我设计一套评测
- 这个 Agent 要接客户的老 ERP，帮我把数据源和幂等方案定下来

---

## 自定义头像

头像位于 `avatars/` 目录。替换要求：

- 格式：PNG（推荐）或 JPG
- 尺寸：512×512 px
- 大小：单张不超过 500KB

---

## 打包分享

```bash
python3 <expert-manager>/scripts/package_expert.py <expert-dir>
```

---

## 知识来源

内容提炼自《人人会AI-智能体进阶（FDE成长指南73篇）》。

该系列原规划为三阶十五模块共 75 篇正文，当前归档正文 63 篇 + 专栏 10 篇。指南 64—75 尚未归档，`method-cheatsheet.md` 中已显式标注「原文待归档」，专家成员被要求不得虚构该部分细节。缺篇清单见 `article-index.md`。

---

## 许可证

暂未指定（All rights reserved）。
