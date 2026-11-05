# codex-study
Codex CLI + Ollama 本地学习实验仓库
环境基线
- Mac Mini 64G
- Ollama: 0.40.10
- Codex CLI: 0.162.1
- 主模型：qwen-local（Qwen3.8 27B q4_K_M-64k）
- 备用模型：Qwen2.5-Coder-32B q4_K_M
- 启动别名：
  - codex-local：默认，禁用网页搜索（日常主力）
  - codex-search：开启Ollama搜索，仅公开信息临时查询

## 仓库结构
- checklist.md ｜4周学习打卡清单
- AGENTS.md   ｜Agent行为规则模板（持续迭代）
- troubleshoot.md ｜报错与排错知识库
- model-compare.md ｜不同模型能力对比记录
- scripts/ ｜练习代码、DuckDB、绘图脚本
- data/ ｜练习时序数据、行业快报、研报片段
- notes/ ｜每周复盘笔记

## 使用纪律
1. 默认禁用web_search，敏感投研内容绝不开启联网搜索
2. 所有模型输出必须人工交叉核验，不直接采信
3. 所有修改提交Git，迭代留存版本
4. 本仓库仅用于学习实验，正式投研项目分开存放
