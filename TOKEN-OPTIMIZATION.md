# Token Optimization 省 Token 技巧汇总

来源：社区高星实践整理（valorisa/Claude-Skills token-optimization 等）。有团队用这些方法把月成本从 $750 降到 $100。

## 四大浪费源与对策

### 1. 缓存失效（Cache misses）
- 保持文件前缀稳定：不要在会话中途修改 CLAUDE.md / 系统提示开头的文件
- 环境变量、agent 定义放配置文件，避免每次注入不同内容
- 工具结果顺序固定，避免重排导致缓存重算

### 2. Context 膨胀（Context bloating）
- 只加载必要的 MCP：保持 2-3 个核心 MCP，其余按需启用（每多一个 MCP，基础消耗可增数千 token）
- 大输出过滤：git log / 构建日志 / 测试输出先 grep/head 再进上下文
- 会话基础消耗目标 < 5,000 token（默认 20,000+）
- 用 context forking：把 research、大规模阅读丢给子代理（subagent），只回传摘要——5k 的调研只占主上下文 ~500 token

### 3. 模型/推理档位选错（Wrong model/effort）
- 简单机械任务用轻量模型/低推理档，复杂架构决策才用旗舰
- 按 codebase 大小配 context window：23k LOC ≈ 200k token 足够，别默认 1M

### 4. 冗长输入（Verbose inputs）
- 指令写具体、写短：与其贴 500 行日志，不如贴 grep 后的 20 行关键错误
- 让 agent 用 `--quiet`、`--porcelain`、`--json` 等机器友好输出
- CLAUDE.md / 系统指令保持精炼，删掉不再需要的规则

## 快速自查清单

```
□ 会话基础 token < 5k？
□ MCP 数量 ≤ 3？
□ 大输出是否经过过滤/子代理？
□ 是否为任务选了合适档位的模型？
□ 系统指令是否每周清理一次？
```

预期效果：整体降低 70-80% token 消耗。
