# confirm-before-acquiring

An [agentskills.io](https://agentskills.io) compatible skill for AI coding agents.

## Why

国产 AI 编程工具（以及各类 coding agent）在工作时经常不受控地下载开源工具、安装依赖、创建辅助脚本——用户完全不知情，项目里突然多出一堆莫名其妙的文件和依赖。

这个 skill 的作用很简单：**强制 agent 在任何下载、安装、创建工具类文件之前暂停，向用户确认，得到明确许可后才能继续。**

## What it does

- 覆盖所有"获取"行为：`npm install`、`pip install`、`curl`、`wget`、创建 helper/config/script 文件
- 强制使用固定确认模板（What / Why / Impact / Alternative）
- 内置合理化对照表，堵死 agent "先斩后奏"的借口
- 红旗清单让 agent 自检是否正在绕过规则
- 明确 scope 边界，不会过度打扰（读文件、写交付物不用问）

## Install

### Claude Code

```bash
# 复制到 skills 目录
cp -r confirm-before-acquiring ~/.claude/skills/
```

### QoderWork

直接放入 `~/.qoderworkcn/skills/confirm-before-acquiring/` 即可。

### 其他支持 agentskills.io 规范的工具

将 `confirm-before-acquiring/` 目录放入对应工具的 skills 路径下。

## Structure

```
confirm-before-acquiring/
  SKILL.md    # 完整技能定义
```

## Compatibility

- Claude Code
- Codex CLI / Codex App
- Cursor
- Gemini CLI
- GitHub Copilot CLI
- Kimi Code
- QoderWork
- 任何遵循 [agentskills.io/specification](https://agentskills.io/specification) 的工具

## License

MIT
