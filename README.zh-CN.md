<p align="center"><img src="https://raw.githubusercontent.com/liudejua27-blip/fitmeet-dsh-plugin/main/assets/fitmeet-icon.png" alt="FitMeet" width="88"></p>
<h1 align="center">FitMeet</h1>
<h3 align="center">Personal Agent Network</h3>
<p align="center">说出你的需求，让 Agent 帮你找到合适的人。</p>
<p align="center"><a href="https://fitmeet.cn">Website</a> · <a href="https://fitmeet.cn/developers/agent-setup">Docs</a> · <a href="#install">Quickstart</a> · <a href="https://fitmeet.cn/mcp">MCP</a> · <a href="https://github.com/liudejua27-blip/human-network/tree/main/skills/fitmeet">Skill</a></p>
<p align="center"><a href="https://github.com/liudejua27-blip/human-network/stargazers"><img alt="GitHub Stars" src="https://img.shields.io/github/stars/liudejua27-blip/human-network?style=flat"></a>
<a href="https://www.npmjs.com/package/fitmeet-dsh-plugin"><img alt="npm version" src="https://img.shields.io/npm/v/fitmeet-dsh-plugin"></a>
<a href="https://www.npmjs.com/package/fitmeet-dsh-plugin"><img alt="npm downloads" src="https://img.shields.io/npm/dm/fitmeet-dsh-plugin"></a>
<a href="https://github.com/liudejua27-blip/fitmeet-dsh-plugin/releases"><img alt="GitHub Release" src="https://img.shields.io/github/v/release/liudejua27-blip/fitmeet-dsh-plugin"></a>
<a href="https://github.com/liudejua27-blip/fitmeet-dsh-plugin/blob/main/package.json"><img alt="Node.js 22.19+" src="https://img.shields.io/badge/Node.js-22.19%2B-339933"></a>
<a href="https://github.com/liudejua27-blip/fitmeet-dsh-plugin"><img alt="TypeScript" src="https://img.shields.io/badge/TypeScript-3178C6?logo=typescript&logoColor=white"></a>
<a href="https://fitmeet.cn/mcp"><img alt="MCP" src="https://img.shields.io/badge/MCP-Streamable_HTTP-111111"></a>
<a href="https://skills.sh/liudejua27-blip/human-network"><img alt="skills.sh" src="https://skills.sh/b/liudejua27-blip/human-network"></a>
<a href="https://github.com/liudejua27-blip/human-network/blob/main/LICENSE"><img alt="License MIT" src="https://img.shields.io/badge/License-MIT-blue"></a></p>

[English](README.md) · [简体中文](README.zh-CN.md)

## Install

**安装 FitMeet Skill**（为 Agent 提供使用指引）：

```sh
npx skills add liudejua27-blip/human-network --skill fitmeet
```

**DeepSeek Harness 插件**（要求 Node.js 22.19+，选择一个语言版本）：

```sh
npx --yes @deepseek-ai/dsh@latest plugin --profile web add fitmeet-dsh-plugin-zh@0.2.2
npx --yes @deepseek-ai/dsh@latest web
```

**其他 MCP 客户端**：添加以下远程地址，然后在浏览器登录自己的 FitMeet 账号。

```text
https://api.fitmeet.cn/api/v1/mcp
```

Skill 提供行为指引；连接 MCP 并完成授权后才能查询和执行。以上是独立可选入口，通用 MCP 客户端无需安装 Harness 插件。

## 连好后，试着这样说

- “使用 FitMeet，帮我找青岛的羽毛球球友。”
- “看看我有哪些已确认的需求或能力可以发布到 FitMeet。”
- “查看我的 FitMeet 组局和提醒。”
- “帮我联系这个人，问问周末能不能一起打球。”

以上是使用示例，不代表平台一定有对应人选。搜索依据用户允许被发现的信息，发布和发消息按照你为该连接授予的权限执行。

## 选择你的使用方式

| 使用方式 | 从这里开始 |
| --- | --- |
| 直接体验 FitMeet | [打开 FitMeet](https://fitmeet.cn) |
| 豆包、WorkBuddy 等兼容 MCP 客户端 | 添加 `https://api.fitmeet.cn/api/v1/mcp` 并登录；[连接指南](https://fitmeet.cn/mcp) |
| DeepSeek Harness | 安装下方一个语言版本的 FitMeet npm 插件 |

## 自动执行与工具可用性

新连接默认请求完整六权限，刷新后的工具列表只返回已授权工具。旧客户端缓存可能需要刷新。授权页可独立开启自动发布、开聊和发消息；开启后按 prepare 的 AUTOMATIC 回执连续提交，不再逐次询问。未开启的连接仍使用下文逐次确认流程。自动模式不创建或确认 Need，不绕过来源、对象、内容与幂等校验。撤销连接可停止后续自动执行。


## 连接

使用支持远程 Streamable HTTP MCP 和浏览器 OAuth 的客户端。WorkBuddy 配置示例；保留并合并原有其他服务：

```json
{"mcpServers":{"fitmeet":{"type":"streamableHttp","url":"https://api.fitmeet.cn/api/v1/mcp","timeout":30000}}}
```

在浏览器登录自己的 FitMeet 账号，查看并决定授权范围。不需要 API Key、固定 Authorization Header 或复制 Token。客户端负责协议发现，无需用户纠结 DCR 或 CIMD。

## 工具与权限

MCP 2.2 共有 17 个工具、6 类权限。完整工具表见[中文 Skill](skills/fitmeet/SKILL.md)和[服务清单](service.json)。

| 能力 | 权限 |
| --- | --- |
| 本人资料 | profile:read |
| 人物、需求与能力搜索及详情 | people:search |
| 可发布来源、发布预览及确认 | hall:publish |
| 本人私聊会话与消息 | messages:read |
| 开聊与发消息的预览及确认 | messages:write；开聊还需 people:search |
| 组局、提醒、个人事项与反馈 | social:read |

**17/17 tools enabled 只代表工具已加载，不代表全部已授权。** 应实际调用一个权限匹配的只读工具验收。403 insufficient_scope 是缺少权限，不一定是登录过期；刷新令牌不会增加权限。需要重新完成同意流程。若宿主只反复刷新，请在[连接管理](https://fitmeet.cn/mcp/connections)只撤销对应客户端，再重连。

发布必须先选匹配的已确认需求或能力并生成准确预览。手动模式逐次确认；明确开启自动执行的连接可以直接提交已准备的操作。不能把找球友需求改成能力介绍。新回执提供发布类型、到期时间和查看入口；重放返回原操作回执，不重复发布。旧回执可能没有新增字段。

组局、提醒和反馈工具只读。创建、加入、改期、完成组局及修改反馈使用返回的网页入口。站内 Agent 的记忆、地图、天气等功能没有自动开放为外部 MCP 工具。

## 中英文版本

- [中文 Skill](skills/fitmeet/SKILL.md)及[配置说明](skills/fitmeet/references/setup.md)。
- [English Skill](skills/fitmeet/SKILL.en.md)及[英文配置说明](skills/fitmeet/references/setup.en.md)。宿主要求标准文件名时，将所选英文文件复制为 SKILL.md，并保留英文 references。
- DeepSeek Harness：[中文 npm](https://www.npmjs.com/package/fitmeet-dsh-plugin-zh) / [English npm](https://www.npmjs.com/package/fitmeet-dsh-plugin)。选择一个语言包安装，[源码仓库](https://github.com/liudejua27-blip/fitmeet-dsh-plugin)。通用 MCP 客户端不需要这个 Harness 专用包。

Skill 提供行为指引，加载 Skill 不等于连接或授权成功。GitHub 更新、npm 发布、生产部署和真实客户端验收分别记录，不代表插件商店上架。

[FitMeet](https://fitmeet.cn) · [MCP 指南](https://fitmeet.cn/mcp) · [接入步骤](https://fitmeet.cn/developers/agent-setup)

## 联系 FitMeet

[官网](https://fitmeet.cn) · [使用文档](https://fitmeet.cn/developers/agent-setup) · [邮箱](mailto:15253005312@163.com)

微信：**angji01**。Discord 和 X 尚未开通。
