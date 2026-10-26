# my-vibe-coding-notes

本项目记录了我当前的 vibe coding 配置及一些经验，可供大家参考。

文档更新时间：2026年10月26日

## Agent 框架

我需要一个轻量、稳定、且口碑经社区验证的 Agent；而 [Pi](https://pi.dev/) 的设计哲学满足了第一点，实际表现则满足了后两点。

仓库地址：[earendil-works/pi](https://github.com/earendil-works/pi)

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

- 开放平台：[platform.deepseek.com/usage](https://platform.deepseek.com/usage)
- 接口文档：[api-docs.deepseek.com/zh-cn](https://api-docs.deepseek.com/zh-cn/)

## 技能

### karpathy-guidelines

约束 LLM 的编码过程，减少未经确认的假设、过度设计、非必要改动及缺乏验证标准等常见失误。

仓库地址：[multica-ai/andrej-karpathy-skills](https://github.com/multica-ai/andrej-karpathy-skills/)

### superpowers

一套完整的软件开发方法论，规范化 Agent 的开发流程。

仓库地址：[obra/superpowers](https://github.com/obra/superpowers)

> 如果你正在使用 Pi，可通过扩展安装 superpowers：

```bash
pi install git:github.com/obra/superpowers
```

## 规则

本章节将列出一些我正在使用且具有通用性的规则，你可以将它们添加到本地的 `AGENTS.md` 文件中。

> 上述技能已包含大量规则，这里只补充我个人额外使用的部分。

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

作用：避免重复造轮子。

### 长期思维

```markdown
- 运行时确定的值，应写自适应逻辑处理，不得硬编码。
```

作用：减少魔法数字，避免用固定值应对变化场景。

### 注释

```markdown
- 注释应仅写代码无法表达的原因与出处；不得"达到预期"式复述代码行为，不得保留与代码不符的注释。
  > 原因只写结论，不写推导过程。

- 不得写没有防错价值的注释。
```

作用：避免留下无价值或带有误导性、影响阅读的注释。

### 漏洞修复

```markdown
- 补丁式修复应覆盖所有的同类变体，不得只针对当前样本。
```

作用：避免做表面修复。

### 命令

```markdown
- 执行命令时应设立看门狗，避免在执行命令时卡住。
```
作用：避免因命令语法错误导致任务卡死。

