# Skill Develop

高星 Agent Skills 合集，接入任何模型（Claude Code / Codex / Gemini CLI / Hermes 等）时，克隆本仓库到 skills 目录即可直接调用。

## 收录内容

| 目录 | 来源 | Stars | 说明 |
|---|---|---|---|
| `superpowers/` | [obra/superpowers](https://github.com/obra/superpowers) | 293k | 社区最全的核心 skill 库：TDD、系统化调试、brainstorming、并行子代理、代码审查、计划执行等 20+ 实战验证 skill |
| `anthropic-skills/` | [anthropics/skills](https://github.com/anthropics/skills) | 179k | Anthropic 官方 skill 库：PDF/DOCX/XLSX/PPTX 文档处理、艺术创作等 |
| `prompt-master/` | [nidhinjs/prompt-master](https://github.com/nidhinjs/prompt-master) | 13.9k | 精准 prompt 编写，零 token 浪费 |
| `TOKEN-OPTIMIZATION.md` | 精选整理 | — | 省 token 技巧汇总：缓存管理、context 分叉、模型选择、输入过滤 |

## 使用方法

```bash
# 克隆到本地
git clone https://github.com/rm66nftvmc-lab/Skill-Develop.git

# 按需把某个 skill 目录复制/链接到你的 agent skills 目录，例如：
cp -r Skill-Develop/superpowers/skills/* ~/.claude/skills/     # Claude Code
cp -r Skill-Develop/superpowers/skills/* ~/.hermes/skills/     # Hermes
```

每个 skill 都是一个含 `SKILL.md` 的自包含文件夹，可独立取用。

## 分工建议

- **省 token**：先读 `TOKEN-OPTIMIZATION.md`，再配合 `prompt-master`
- **精进产出质量**：`superpowers` 的 TDD、systematic-debugging、requesting-code-review
- **文档产出**：`anthropic-skills` 的 pdf/docx/xlsx/pptx skill

## 致谢

本仓库收录的 skill 版权归各原作者所有（见各目录 LICENSE / THIRD_PARTY_NOTICES）。
