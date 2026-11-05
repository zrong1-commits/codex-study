# Codex CLI 学习打卡清单
> 适配环境：Mac Mini 64G | Ollama 0.40.10 | Codex CLI 0.162.1
> 模型：qwen-local（Qwen3.8 27B 64K）、Qwen2.5-Coder-32B
> 仓库：codex-study
> 原则：默认禁用网页搜索 web_search="disabled"；所有产出提交Git；投研输出必须交叉核验
> 资料索引
> D0：专属上手手册《Codex CLI + Ollama（Mac Mini）上手手册（完整版）》
> D1：Codex Github https://github.com/openai/codex
> D2：NVIDIA Playbook https://build.nvidia.com/playbooks/cli-coding-agent/codex
> D3：Your First 30 Minutes with Codex CLI https://codex.danielvaughan.com/2026/04/18/your-first-30-minutes-with-codex-cli/
> D4：Becoming Codex CLI Expert https://codex.danielvaughan.com/2026/04/07/learning-plan-becoming-codex-cli-expert/
> D5：Codex 官方帮助文档 https://help.openai.com/en/collections/11044748-codex

## 前置准备（一次性完成）
- [ ] 配置 zsh 别名：codex-local / codex-search，验证启动正常
- [ ] 新建 git 仓库 codex-study，初始化
- [ ] 校验环境：ollama list、codex --version、pkill -f codex 可用
- [ ] 拉取 Qwen2.5-Coder-32B q4_K_M 备用模型

---

# 第1周｜基础搭建 + TUI交互 + 权限沙箱
目标：稳定启停、看懂TUI、理解沙箱权限，规避自动下载远端模型坑
每日投入：40–60min

### Day1 环境校验 & 架构认知
- [ ] 必读：D0【前置依赖、推荐启动方式、进程管理】；D1 README 前半段
- [ ] 实操：codex-local 启动、pkill 干净退出；测试 codex --oss 观察异常行为
- [ ] 实操：git init，README 记录环境版本信息
- [ ] 复盘：写下3条启动红线，存入README
- [ ] ✅ 打卡完成

### Day2 TUI基础斜杠命令
- [ ] 必读：D0【Codex TUI 基础操作】；D1 Slash commands 小节
- [ ] 实操：依次执行 ? /new /list /model /permissions /delete
- [ ] 实操：提问查看Agent可用工具列表
- [ ] 实操：整理斜杠命令速查表 markdown
- [ ] ✅ 打卡完成

### Day3 /init 生成 AGENTS.md
- [ ] 必读：D0 /init 段落；D3 前半部分 AGENTS.md 介绍
- [ ] 实操：项目内执行 /init，生成默认 AGENTS.md
- [ ] 实操：对比有无AGENTS.md 的输出差异
- [ ] 实操：git add + commit 提交初始AGENTS.md
- [ ] 复盘：记录AGENTS.md生效边界
- [ ] ✅ 打卡完成

### Day4 权限策略 & sandbox沙箱
- [ ] 必读：D0 approval_policy / sandbox_mode；D1 discussion 搜索相关话题
- [ ] 实操：理解 on-request / auto / deny 三种审批策略
- [ ] 实操：测试 read-only / workspace-write 沙箱模式
- [ ] 实操：测试跨目录写入，验证沙箱拦截
- [ ] 复盘：记录沙箱保护范围
- [ ] ✅ 打卡完成

### Day5 第一个代码任务：基础数据分析脚本
- [ ] 必读：D0【模型选择策略】；D1官方代码示例
- [ ] 实操：让Codex编写Python读取csv、统计、matplotlib绘图
- [ ] 实操：观察工具调用、审批交互、自主debug
- [ ] 实操：样例csv+脚本提交git
- [ ] 复盘：记录代码幻觉高发场景
- [ ] ✅ 打卡完成

### Day6 排错专项训练
- [ ] 必读：D0【常见报错排查清单】全文
- [ ] 实操：复现 `provider name must not be empty` 并修复
- [ ] 实操：不登录账号测试网页搜索，观察鉴权报错
- [ ] 实操：新建 troubleshoot.md 记录现象、根因、修复步骤
- [ ] ✅ 打卡完成

### Day7 第1周验收 & 复盘
- [ ] 必读：回看本周笔记；D2 NVIDIA Playbook通读
- [ ] 实操：所有产出统一git提交
- [ ] 实操：完整走通 SSH → codex-local → 生成代码 → 审批 → git 流程
- [ ] 自测：独立启停、切换模型、清理进程、生成脚本
- [ ] 复盘：记录本周卡点TOP2
- [ ] ✅ 第1周全部完成

---

# 第2周｜上下文控制、AGENTS.md定制、提示词工程、模型对比
目标：掌握64K上下文边界、定制投研Agent规则、控制输出风格
每日投入：40–60min

### Day1 Token、上下文窗口原理与64K边界
- [ ] 必读：D0 Modelfile参数、RAG注意事项；D1 discussion context window
- [ ] 实操：理解65536上下文，安全输入上限≈55k token
- [ ] 实操：长文档分批投喂，测试截断、信息丢失现象
- [ ] 实操：指令Codex统计token占用、做摘要压缩
- [ ] 复盘：建立上下文预算规则
- [ ] ✅ 打卡完成

### Day2 定制【投研+代码双场景】AGENTS.md V1
- [ ] 必读：D3 全文精读
- [ ] 实操：修改AGENTS.md，写入金融分析固定约束（收益/成本、DDM/ROCE、风险识别等）
- [ ] 实操：git commit 保存版本
- [ ] 实操：提问周期股存货周期问题，校验规则生效
- [ ] 复盘：区分稳定常驻规则 / 临时单次prompt
- [ ] ✅ 打卡完成

### Day3 提示词范式对比
- [ ] 必读：D3 提示词结构、任务分解段落
- [ ] 实操：同一任务（乘联会数据整理制表绘图）两组对照：纯单次prompt / AGENTS.md+简短prompt
- [ ] 实操：记录两份输出差异
- [ ] 复盘：沉淀自己的提示词范式
- [ ] ✅ 打卡完成

### Day4 模型对照实验：qwen-local VS Qwen2.5-Coder-32B
- [ ] 必读：D0【模型选择策略】重读
- [ ] 实操：同一代码重构任务，双模型轮换测试
- [ ] 实操：同一财报解读任务，双模型轮换测试
- [ ] 实操：model-compare.md 记录速度、幻觉、代码质量差异
- [ ] 复盘：固化模型切换策略
- [ ] ✅ 打卡完成

### Day5 长文档RAG前置：分块、摘要、事实提炼
- [ ] 必读：D0 RAG章节
- [ ] 实操：长研报交给Codex，自动分块、摘要、区分原文事实与模型推断
- [ ] 复盘：建立事实/推断分离习惯
- [ ] ✅ 打卡完成

### Day6 采样参数：temperature、top_p
- [ ] 必读：Ollama Modelfile Parameter文档；D0参数说明
- [ ] 实操：对比 temperature=0.2（投研严谨）和0.7（代码探索）输出差异
- [ ] 复盘：固化两套参数模板
- [ ] ✅ 打卡完成

### Day7 第2周验收，定稿AGENTS.md V2
- [ ] 必读：回看本周笔记；D4前半部分Agent控制
- [ ] 实操：迭代AGENTS.md到V2，git打tag agents-v2
- [ ] 实操：完整链路测试：长文档解读→制表→绘图
- [ ] 复盘：记录AGENTS.md待优化点
- [ ] ✅ 第2周全部完成

---

# 第3周｜工具调用、远程VS Code、Shell、RAG联动
目标：熟练文件读写、shell审批；打通SSH远程；建立本地RAG标准工作流
每日投入：60min

### Day1 远程SSH VS Code + Codex 工作流
- [ ] 必读：D0【远程工作流】章节
- [ ] 实操：Windows VS Code Remote-SSH 连接Mac Mini，远端终端启动codex-local
- [ ] 实操：读取py文件 → 修改 → 审批 → git diff评审
- [ ] 复盘：远程延迟、行为差异
- [ ] ✅ 打卡完成

### Day2 Shell工具调用，DuckDB时序查询练习
- [ ] 必读：D1 shell tool、tool calling文档
- [ ] 实操：乘联会csv时序数据，让Codex编写DuckDB入库、聚合、同比计算脚本
- [ ] 实操：审批执行、核对计算结果
- [ ] 复盘：SQL幻觉校验要点
- [ ] ✅ 打卡完成

### Day3 Codex直读文档 vs LlamaIndex向量检索
- [ ] 必读：D0 RAG章节
- [ ] 实操：多篇行业报告对照两种方案测试
- [ ] 实操：记录token消耗、幻觉差异
- [ ] 复盘：确定RAG选型策略
- [ ] ✅ 打卡完成

### Day4 网页搜索取舍与隐私边界
- [ ] 必读：D0【网页搜索能力说明】全章节精读
- [ ] 实操：ollama signin登录，测试 codex-search 联网查询乘联会数据
- [ ] 实操：理解敏感内容红线，切回 codex-local
- [ ] 复盘：制定搜索启用纪律
- [ ] ✅ 打卡完成

### Day5 Agent日志调试，识别幻觉信号
- [ ] 必读：D1 discussion 搜索 hallucination / tool trace
- [ ] 实操：观察Agent思考链路，识别编造数据、工具重试场景
- [ ] 实操：使用交叉验证prompt，要求输出依据与不确定点
- [ ] 复盘：整理幻觉高频场景清单
- [ ] ✅ 打卡完成

### Day6 Git评审规范：Codex变更审核
- [ ] 必读：git diff / commit / reset 基础用法
- [ ] 实操：Codex批量修改代码，人工diff逐行评审
- [ ] 实操：指令Codex回滚不合理变更
- [ ] 复盘：确立Agent产出必须人工评审铁律
- [ ] ✅ 打卡完成

### Day7 第3周验收，沉淀RAG标准模板
- [ ] 必读：D2 NVIDIA Playbook 完整精读
- [ ] 实操：沉淀模板：原文摘录→事实统计→指标→假设→风险→结论
- [ ] 实操：完整闭环：原始快报→整理→绘图→风险标注→git归档
- [ ] 复盘：标记RAG链路卡点
- [ ] ✅ 第3周全部完成

---

# 第4周｜MCP、批量调用、多Agent分工、风控体系（高阶）
> 可放缓，生产稳定后再深挖
每日投入：60min

### Day1 MCP（Model Context Protocol）基础
- [ ] 必读：D1 README MCP章节、官方示例
- [ ] 实操：看懂MCP作用；跑通最简本地文件读取MCP demo
- [ ] 复盘：MCP扩展能力价值
- [ ] ✅ 打卡完成

### Day2 非交互式批量调用 codex exec
- [ ] 必读：D1 codex exec 文档
- [ ] 实操：批量对多个csv生成绘图脚本，无交互执行
- [ ] 实操：输出定向保存文件
- [ ] 复盘：区分交互式TUI探索 / exec批量自动化
- [ ] ✅ 打卡完成

### Day3 多模型Agent分工
- [ ] 必读：D4 Becoming Codex CLI Expert 全文
- [ ] 实操：分工演练：Coder32B负责代码SQL绘图；qwen-local负责估值、周期、风险
- [ ] 实操：完成一份完整行业小分析
- [ ] 复盘：固化模型分工边界
- [ ] ✅ 打卡完成

### Day4 自建搜索替代方案调研（DuckDuckGo/SerpAPI）
- [ ] 必读：D0 进阶备选搜索方案
- [ ] 实操：调研第三方搜索API调用方式
- [ ] 实操：设计MCP搜索工具方案（仅方案设计，不强制开发）
- [ ] 复盘：三条搜索路线对比
- [ ] ✅ 打卡完成

### Day5 压力测试 & 对抗幻觉测试
- [ ] 必读：D1 discussion 幻觉控制
- [ ] 实操：残缺、冲突数据输入，测试Codex是否编造信息
- [ ] 实操：建立三层校验流程：结论、数据、来源交叉核对
- [ ] 复盘：输出风控检查清单
- [ ] ✅ 打卡完成

### Day6 端到端全链路演练
- [ ] 必读：回顾全部笔记、troubleshoot.md
- [ ] 实操：独立完成完整投研小项目：数据收集→时序整理→测算→绘图→周期判断+风险→归档
- [ ] ✅ 打卡完成

### Day7 结业沉淀 & 长期路线规划
- [ ] 必读：选择性回看全部资料
- [ ] 实操：汇总资产：AGENTS.md、速查表、故障库、RAG模板
- [ ] 实操：编写个人生产SOP
- [ ] 实操：规划后续拓展：MCP行情工具、DuckDB时序库集成
- [ ] 复盘：写下长期使用纪律
- [ ] ✅ 第4周全部完成｜✅ 整体学习计划结业

---
## 长期使用纪律（固定放在清单末尾）
- [ ] 持仓、内部推演、敏感投研材料，永久禁用Ollama网页搜索
- [ ] 模型输出的数据、估值、SQL，必须交叉核验，不直接采信
- [ ] 模板、脚本、规则全部Git版本管理，可回滚对比
- [ ] 新能力优先在小练习仓库测试，不直接上正式报告

