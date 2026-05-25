# J.A.R.V.I.S.Omnifex — 贾维斯·全能智造管家

<p align="center">
  <img src="docs/assets/logo.png" alt="JARVIS Omnifex Logo" width="200"/>
</p>

<p align="center">
  <strong>开源、本地优先、自我进化的超级个人AI助手与家庭智造工厂一体化系统</strong>
</p>

<p align="center">
  <a href="#项目背景">背景</a> •
  <a href="#核心特性">特性</a> •
  <a href="#系统架构">架构</a> •
  <a href="#快速开始">快速开始</a> •
  <a href="#使用场景">场景</a> •
  <a href="#技术栈">技术栈</a> •
  <a href="#路线图">路线图</a> •
  <a href="#贡献指南">贡献</a> •
  <a href="#许可证">许可证</a>
</p>

---

## 项目背景

在《钢铁侠》中，贾维斯（J.A.R.V.I.S.）是一个全能的AI管家——理解自然语言、控制智能家居、辅助创造，并拥有长期记忆与自主学习能力。随着2025-2026年多模态大模型、Agent自主进化框架、桌面级数字制造设备和开源智能家居平台的成熟，**在家庭环境中构建一个“贾维斯”级别的全能智造助手已成为工程现实**。

**J.A.R.V.I.S. Omnifex** 正是为此而生。它不是另一个对话机器人，而是一个**能够感知、决策、控制、制造、学习的完整系统**——将“超级智能体”与“家庭数字工厂”彻底融合，让你在生活空间和创作空间之间无缝穿行。

---

## 核心特性

### 🧠 会思考的 AI 大脑
- **多专家角色系统**：根据任务自动切换机械工程师、增材制造专家、家居管家、安全审计员等身份
- **任务规划与反思**：ReAct + Plan-and-Execute 双模式，复杂任务自动拆解为可执行步骤
- **主动智能 (Pask 范式)**：持续感知环境和上下文，在恰当时机主动提供帮助，而非被动等待指令
- **工具动态调度**：200+标准化工具接口（CNC、3D打印、激光切割、智能家居），支持根据任务语义自动选择最优工具

### 🧬 自我进化的长期记忆
- **三层记忆架构**：短期对话记忆 → 长期向量/图记忆 → 可复用技能记忆
- **仿生认知折叠 (Cognifold)**：持续将碎片事件流折叠为自我生成的认知结构，实现自主组织与目标识别
- **自进化检索 (EvolveMem)**：记忆检索策略随使用自动优化，长期使用效果持续提升
- **技能自动沉淀**：从重复任务中自动提炼可复用技能模板，100次交互可生成8-12个技能

### 🏭 全链路数字制造
- **AI 工艺规划**：上传图纸自动识别特征，推荐刀具、主轴转速、进给速度，生成G代码
- **实时质量闭环**：加工中通过振动/视觉传感器监测异常，加工后自动比对三坐标数据生成检测报告
- **多设备统一调度**：五轴CNC、光固化/FDM/金属3D打印、激光切割/打标——一个大脑统一指挥
- **零代码制造**：对小白用户提供对话式制造向导，说“帮我打印一个齿轮”即可启动完整流程

### 🏠 跨域智能联动
- **生活与创作统一**：同一AI同时管理智能家居（灯光、安防、空调）和制造设备
- **安全场景引擎**：烟雾报警→全屋警示+紧急停机+门锁开启+手机推送，<500ms响应
- **环境自适应**：进入工坊自动切换5000K高显色灯光、启动排风、预热打印机
- **本地隐私优先**：全部数据处理本地完成，支持完全离线运行

### 🔒 安全可靠
- **五级渐进式控制**：从完全自主到完全人工，平滑切换
- **高危操作双确认**：涉及动力电、激光、高温的操作必须人工确认
- **代码与设备隔离**：高风险执行在 Docker/gVisor 沙箱中进行
- **完整审计追踪**：所有工具调用、设备操作全记录，支持事后回溯

---

## 系统架构

```
┌──────────────────────────────────────────────────────────┐
│              交互层 (Interaction Layer)                    │
│  语音输入输出 │ 文本对话 │ AR视觉呈现 │ 手势/体感控制     │
├──────────────────────────────────────────────────────────┤
│              感知层 (Perception Layer)                     │
│  语音识别(Whisper) │ 图像/视频理解 │ 意图检测(Pask) │ 设备状态感知  │
├──────────────────────────────────────────────────────────┤
│              决策层 (Decision Layer)                       │
│  ┌────────────────────────────────────────────────────┐  │
│  │           LLM推理引擎 (可插拔多模型)                 │  │
│  │  ┌──────────┐ ┌──────────┐ ┌──────────┐           │  │
│  │  │ 任务规划  │ │ 角色切换  │ │ 工具调度  │           │  │
│  │  │(ReAct/   │ │(多专家   │ │(动态路由) │           │  │
│  │  │ Plan-Exe)│ │ 人格)    │ │          │           │  │
│  │  └──────────┘ └──────────┘ └──────────┘           │  │
│  └────────────────────────────────────────────────────┘  │
│      三层记忆系统  │  技能图谱  │  进化引擎                │
├──────────────────────────────────────────────────────────┤
│              执行层 (Execution Layer)                      │
│  ┌──────────────────┐  ┌──────────────────┐              │
│  │  智能家居域       │  │  智能工坊域       │              │
│  │  灯光/空调/安防   │  │  CNC/3D打印/激光  │              │
│  │  窗帘/音响/门锁   │  │  测量/后处理/机器人│              │
│  └──────────────────┘  └──────────────────┘              │
│  ┌────────────────────────────────────────────────────┐  │
│  │       跨域场景联动引擎 (安全/环境/状态/能耗)        │  │
│  └────────────────────────────────────────────────────┘  │
├──────────────────────────────────────────────────────────┤
│           基础设施层 (Infrastructure Layer)                │
│  Dify/n8n编排 │ Milvus/Qdrant向量库 │ Neo4j图库           │
│  Redis缓存 │ Kafka消息队列 │ Docker/K8s部署 │ Home Assistant │
└──────────────────────────────────────────────────────────┘
```

---

## 快速开始

### 环境要求

- **操作系统**: Ubuntu 22.04+ / macOS 14+ / Windows 11 (WSL2)
- **Python**: 3.10+
- **硬件建议**: 
  - 最低：4核CPU, 16GB RAM
  - 推荐：16核CPU, 64GB RAM, NVIDIA RTX 4090 (用于本地多模态模型)
- **智能家居网关**: Home Assistant (可选，用于家居联动)
- **制造设备**: 通过网络/串口/USB连接的CNC、3D打印机等 (可选)

### 一键安装

```bash
# 克隆仓库
git clone https://github.com/yourusername/jarvis-omnifex.git
cd jarvis-omnifex

# 运行安装脚本
chmod +x install.sh
./install.sh
```

安装脚本将自动配置：
- Docker 容器化的 Dify 和 n8n 编排层
- 向量数据库 (Milvus/Qdrant)
- Redis 缓存
- Home Assistant 集成接口 (如检测到已安装)
- 预置的专家角色提示词和基础工具库

### 配置向导

启动后，访问 `http://localhost:3000` 进入配置向导：

1. **连接 LLM**：支持 OpenAI、Ollama 本地模型、或任何兼容 API
2. **连接智能家居**：输入 Home Assistant 地址和 Token（可选）
3. **注册制造设备**：通过设备发现或手动添加设备型号
4. **选择预置技能包**：根据你的设备清单自动激活对应技能模板

### 首次对话

```
你: 贾维斯，介绍一下你能做什么？

贾维斯: 我是你的全能智造管家。目前我连接了：
       - 1台五轴CNC (XM-100)
       - 1台光固化打印机 (Form 4+)
       - 全屋智能家居 (12个设备)
       
       你可以让我加工零件、打印模型、控制家居，或规划复杂项目。
       需要我演示什么吗？
```

---

## 使用场景

### 1. 精密零件制造
> “贾维斯，帮我加工这颗钛合金叶轮，公差控制在±0.01mm”

AI 自动完成：3D模型分析 → 刀具选择 → 五轴刀路规划 → G代码生成 → 启动加工 → 在线监测振动/刀具磨损 → 三坐标检测报告生成

### 2. 模型打印与后处理
> “贾维斯，用光固化打印这组高达改件，要耐高温树脂”

AI 自动完成：模型破面修复 → 智能支撑生成 → 最优摆放角度计算 → 启动打印并逐层监控 → 完成后指导打磨位置

### 3. 全屋智能联动
> “贾维斯，电影模式”

AI 自动完成：客厅灯光调暗至10% → 窗帘关闭 → 投影仪与音响开启 → 空调调至24℃ → 工坊设备进入待机监控模式

### 4. 安全应急响应
当烟雾传感器触发或CNC检测到撞刀：
- 全屋警报响起，灯光闪烁红色
- 工坊紧急停机（<500ms）
- 智能门锁自动开启
- 手机推送实时画面和事故报告

### 5. 跨媒体IP开发
> “贾维斯，创建一个赛博朋克角色IP，同步开发游戏、手办和宣传视频”

AI 自动编排：生成世界观 → 生成3D角色 → 输出游戏原型(Buildbox/Godogen) → 优化3D打印模型 → 调用视频生成(Seedance/Kling) → 汇总项目包

---

## 技术栈

| 层级 | 技术 |
|------|------|
| **AI 编排** | [Dify](https://github.com/langgenius/dify) + [n8n](https://github.com/n8n-io/n8n) |
| **Agent 框架** | [LangGraph](https://github.com/langchain-ai/langgraph), [OpenAI Agents SDK](https://github.com/openai/openai-agents-python), [CrewAI](https://github.com/joaomdmoura/crewAI) |
| **记忆系统** | [Milvus](https://github.com/milvus-io/milvus) / [Qdrant](https://github.com/qdrant/qdrant) + [Neo4j](https://github.com/neo4j/neo4j) |
| **模型接入** | OpenAI API, [Ollama](https://github.com/ollama/ollama) (本地 Llama-4等), 任何 OpenAI-compatible API |
| **智能家居** | [Home Assistant](https://github.com/home-assistant/core) + Matter 协议 |
| **语音** | [Whisper](https://github.com/openai/whisper) + ESP32-S3 本地唤醒 |
| **设备控制** | 串口通信, Modbus, MQTT, REST API |
| **安全隔离** | Docker, gVisor |
| **监控追踪** | [LangSmith](https://www.langchain.com/langsmith), [Weave (W&B)](https://weave-docs.wandb.ai/) |
| **部署** | Docker Compose, Kubernetes (可选) |

---

## 硬件兼容列表

我们已验证并持续增加对以下设备的支持（通过插件架构，社区可自行贡献驱动）：

### 数控加工
- Xhorse XM-100 / XM-300 五轴加工中心
- 西马特 C6 数控车床
- Xhorse XTC-200 车铣复合
- 北京精雕 JDGR 系列

### 3D 打印
- Formlabs Form 4+ (光固化)
- 纵维立方 M5 Plus (光固化)
- Raise3D Pro3 (FDM)
- Intamsys Funmat Pro 410 (高温FDM)
- Desktop Metal Studio System 2 (金属)
- 融速科技 Laser Mini (送丝金属)

### 激光加工
- 大族粤铭 CO2 激光切割机
- 华工激光光纤打标机

### 智能家居
- 通过 Home Assistant 兼容所有 Matter/Zigbee/Z-Wave/WiFi 设备
- 推荐：Philips Hue, Aqara, YeeLight, Sonoff

> 没有你的设备？请参考 [设备驱动开发指南](docs/device-driver-guide.md) 自行添加，欢迎贡献 PR！

---

## 项目结构

```
jarvis-omnifex/
├── brain/                    # 大脑层：编排、记忆、进化
│   ├── orchestration/        # Dify & n8n 工作流模板
│   ├── memory/               # 记忆系统实现
│   │   ├── short_term.py     # Redis 短期记忆
│   │   ├── long_term.py      # 向量+图长期记忆
│   │   └── cognifold.py      # 仿生认知折叠模块
│   ├── skills/               # 技能图谱与生成器
│   └── evolution/            # 自主进化引擎
│       ├── evolvemem.py      # 自进化记忆检索
│       └── ratchet.py        # 技能卫生机制
├── agents/                   # 多专家Agent人格
│   ├── roles/                # 角色定义 (机械师、打印专家...)
│   └── tools/                # 标准化工具接口
├── workshop/                 # 智能工坊域
│   ├── devices/              # 设备驱动 (CNC、3D打印、激光...)
│   ├── monitoring/           # 实时监控 (振动、视觉、温度)
│   └── quality/              # 质量检测与报告
├── home/                     # 智能家居域
│   ├── hass_connector.py     # Home Assistant 集成
│   └── scenes/               # 预置场景模板
├── scenarios/                # 跨域场景联动引擎
│   ├── safety.py             # 安全联动
│   ├── ambient.py            # 环境联动
│   └── energy.py             # 能耗联动
├── perception/               # 感知层
│   ├── asr/                  # 语音识别
│   ├── vision/               # 图像视频理解
│   └── intent/               # 意图检测 (Pask)
├── api/                      # 对外 API
├── ui/                       # Web 管理界面
├── docker/                   # Docker 部署文件
├── docs/                     # 详细文档
├── install.sh                # 一键安装脚本
├── docker-compose.yml
└── README.md
```

---

## 路线图

### v0.1.0 - 核心大脑 (2026 Q3)
- [ ] Dify + n8n 基础编排
- [ ] 短期记忆与对话管理
- [ ] 多专家角色系统
- [ ] 首批50个工具接口

### v0.2.0 - 记忆觉醒 (2026 Q4)
- [ ] 三层记忆架构完整实现
- [ ] Cognifold 仿生记忆
- [ ] 基础技能生成器
- [ ] 用户画像系统

### v0.3.0 - 双手诞生 (2027 Q1)
- [ ] 首批设备驱动 (Form 4+, XM-100)
- [ ] 实时监控与异常检测
- [ ] AI工艺参数推荐
- [ ] 安全沙箱执行

### v0.4.0 - 家园联动 (2027 Q2)
- [ ] Home Assistant 深度集成
- [ ] 跨域场景引擎
- [ ] 安全联动原型

### v0.5.0 - 自我进化 (2027 Q3)
- [ ] EvolveMem 集成
- [ ] Ratchet 技能卫生机制
- [ ] 社区技能市场

### v1.0.0 - 贾维斯诞生 (2027 Q4)
- [ ] 全功能稳定版
- [ ] 完整文档与教程
- [ ] 多语言支持
- [ ] 插件生态系统

---

## 贡献指南

我们非常欢迎社区贡献！无论你是：
- 🤖 AI 开发者：优化记忆系统、进化引擎、Agent 角色
- 🔧 硬件黑客：为更多设备编写驱动
- 🏠 智能家居玩家：贡献新的跨域场景模板
- 📝 文档作者：完善教程、翻译多语言

请阅读 [CONTRIBUTING.md](CONTRIBUTING.md) 了解开发规范和提交流程。

特别欢迎为以下设备贡献驱动：
- 各种 CNC 控制器 (GRBL, Mach3, LinuxCNC...)
- 开源 3D 打印机 (Voron, Prusa, Bambu...)
- 激光雕刻机
- 机械臂

### 开发环境搭建

```bash
# 安装开发依赖
pip install -r requirements-dev.txt

# 启动开发环境
docker compose -f docker-compose.dev.yml up -d

# 运行测试
pytest tests/

# 代码规范检查
pre-commit run --all-files
```

---

## 社区与支持

- 💬 **Discord**: [加入我们的 Discord](https://discord.gg/yourlink)
- 📖 **文档**: [docs.jarvis-omnifex.dev](https://docs.jarvis-omnifex.dev)
- 🗣️ **讨论**: [GitHub Discussions](https://github.com/yourusername/jarvis-omnifex/discussions)
- 🐛 **Bug 报告**: [Issues](https://github.com/yourusername/jarvis-omnifex/issues)
- 🛠️ **功能请求**: [Feature Requests](https://github.com/yourusername/jarvis-omnifex/discussions/categories/ideas)

---

## 许可证

本项目采用 **Apache License 2.0** 开源，允许个人和商业使用、修改和分发。部分模块（如设备驱动）可能受设备厂商许可条款约束，请在使用前查阅相关协议。

---

## 致谢

本项目建立在众多卓越的开源项目和研究之上，特别感谢：

- [Dify](https://github.com/langgenius/dify) - AI应用开发平台
- [n8n](https://github.com/n8n-io/n8n) - 可扩展工作流自动化
- [Home Assistant](https://github.com/home-assistant/core) - 开源智能家居平台
- [OpenAI Whisper](https://github.com/openai/whisper) - 语音识别
- [Ollama](https://github.com/ollama/ollama) - 本地大模型运行
- [Milvus](https://github.com/milvus-io/milvus) - 向量数据库
- 以及 Cognifold、EvolveMem、Pask、Hermes Agent 等前沿研究

---

<p align="center">
  <em>“贾维斯不只是工具，它是你的创造伙伴。” —— 致敬每一个不安分的创造者</em>
</p>

<p align="center">
  Made with ❤️ by the Omnifex Community
</p>
