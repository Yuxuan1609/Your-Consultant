# consulting-agent

将管理咨询行业的商业化咨询能力，标准化为 opencode Agent 可执行的标准化工作流。**不内置行业方法论，而是提供「生成方法论的方法论」——元准则引擎。**

---

## 核心理念

传统咨询工具给你现成的框架（SWOT、Porter 五力...），但不会告诉你怎么针对具体问题定制方法论。consulting-agent 反过来：输入客户信息，输出专属诊断框架 + 结构化分析 + 初版报告。用户零门槛——只需告诉 Agent 公司名和痛点，剩下的由 Agent 牵引完成。

### 三段式工作流

```
抽象 ──────────────────────────────────→ 具象

Step 1: 项目设立   →  用户提供最少信息，Agent 自动补全客户画像
Step 2: 方法论+初版 →  模板匹配→融合→内外诊断→假设生成→HTML 报告  
Step 3: 细化交付    →  数据验证→深度图表→终版方案
```

### 技术架构

```
SKILL.md (主编排) ──→ search-agent  (Tavily → tofu fallback)
                 ──→ analyst-agent (框架融合+内诊+对照)
                 ──→ data-agent    (年报PDF→时间序列提取)
                 ──→ report-agent  (HTML 报告生成)
```

纯 opencode 原生配置（Skill + Sub-Agent + MCP），零代码开发。

---

## 快速开始

### 环境

- [opencode](https://opencode.ai) 已安装
- Tavily API Key ([免费注册](https://tavily.com))
- LLM API Key (Claude 或 DeepSeek)

### 3 步启动

```bash
# 1. 解压到项目根目录
unzip consulting-agent-light.zip -d your-project/

# 2. 设置环境变量
export TAVILY_API_KEY=tvly-...
export ANTHROPIC_API_KEY=sk-ant-...

# 3. 重启 opencode
# 然后说一句：新建咨询项目
```

详见 `INSTALL.md`。

---

## 文件结构

```
├── .opencode/skill/consulting-workflow/   # 主编排 Skill
├── .opencode/agents/                      # 4 个子 Agent
├── data/
│   ├── frameworks.json                    # 17 框架 + 路由 + 融合规则
│   └── project-schema.json                # 项目数据 Schema
├── servers/tofu_search/                   # tofu MCP Server (fallback)
└── INSTALL.md
```

---

## 版本

| 版本 | 搜索链 | 额外依赖 |
|------|--------|----------|
| **轻量版** ← 当前 | Tavily + tofu-search | 仅需 Tavily API Key |
| 重度版（开发中） | + SearXNG + lite_txtai | Docker + Python torch |

---
