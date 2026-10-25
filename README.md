# my-vibe-coding-notes

本项目记录了我当前的 vibe coding 配置及一些经验，可供大家参考。

## Agent Harness

我需要一个轻量、稳定、且口碑经社区验证的 agent；而 [Pi](https://pi.dev/) 的设计哲学满足了第一点，实际表现则满足了后两点。

仓库地址：https://github.com/earendil-works/pi

### 扩展

Pi 具备优秀的可定制性，你可以在[这里](https://pi.dev/packages)下载所有被官方收录的扩展。

以下是我在用的一些扩展：

| 扩展 | 功能 | 安装 |
| --- | --- | --- |
| `pi-web-access` | 提供网页搜索、内容提取和视频理解 | `pi install npm:pi-web-access` |
| `pi-tool-one-line` | 折叠工具输出及思维链 | 前往[仓库](https://github.com/Polyaris-0413/pi-tool-one-line)下载 `.ts` 文件 |

## 模型

[DeepSeek](https://www.deepseek.com/) 凭借极致的性价比与优秀的信誉，成为了我和许多人的首选。

模型推荐 `deepseek-flash`，思考档位推荐 `high`，这是日常开发中的甜点配置。

- 开放平台：https://platform.deepseek.com/usage
- 接口文档：https://api-docs.deepseek.com/zh-cn/

## Skill

### karpathy-guidelines

约束 LLM 的编码过程，减少未经确认的假设、过度设计、非必要改动及缺乏验证标准等常见失误。

仓库地址：https://github.com/multica-ai/andrej-karpathy-skills/

### superpowers

一套完整的软件开发方法论，规范化 agent 的开发流程。

仓库地址：https://github.com/obra/superpowers

> 如果你正在使用 Pi：superpowers 允许以扩展的形式安装，命令如下↓

```bash
pi install git:github.com/obra/superpowers
```

## 规则

本章节将列出一些我正在使用且具有通用性的规则，你可以将它们添加到本地的 `AGENTS.md` 文件中。

  > 上述 skills 已内置大量规则，这里只补充我个人额外使用的部分。
 
### 减少冗余

```markdown
实现功能前先检索项目内可复用代码：

1. 有可复用代码：直接调用。
2. 调用不便：先封装，再调用。
3. 无现成代码：按以下优先级选择实现手段：
   - 语言/框架原生 API
   - 成熟第三方库
   - 自行实现
```

作用：避免 AI 重复造轮子。

### 长期思维

```markdown
- 运行时确定的值，应写自适应逻辑处理，不得硬编码。
```

作用：减少魔法数字，避免 AI 用固定值应对变化场景。

### 漏洞修复

```markdown
- 补丁式修复应覆盖所有的同类变体，不得只针对当前样本。
```

作用：避免 AI 做表现修复。
