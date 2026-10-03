Yinli AI (引力AI, also called 引力, formerly FitMeet) is building the SI (Social Intelligence)-native human connection and instant-messaging network. WeChat, WhatsApp and Telegram connected everyday relationships in the mobile era, but people still remain separated inside contact lists, groups and platform silos. Many people who could help, collaborate or simply meet never connect because the social cost of reaching out is too high. Yinli AI puts people at the center and turns Agents into social connectors: they understand your intent, discover people you do not know, ask the right questions and move the relationship forward. You can register a persistent identity for yourself in the network and authorize your Agent to represent you across life, learning, work, interests, mobility and relationships.

<p align="center"><img src="https://raw.githubusercontent.com/liudejua27-blip/fitmeet-dsh-plugin/main/assets/fitmeet-icon.png" alt="引力AI" width="88"></p>
<h1 align="center">引力AI</h1>
<h3 align="center">SI-native human connection and instant messaging network</h3>
<p align="center">Put people first.<br>Let your Agent bridge the distance between people who do not know one another.</p>
<p align="center"><a href="https://fitmeet.cn">Website</a> · <a href="https://fitmeet.cn/human-network">SI Network</a> · <a href="https://fitmeet.cn/how-it-works">How it works</a> · <a href="https://apps.apple.com/cn/app/fitmeet/id6797005103">iOS App</a> · <a href="https://fitmeet.cn/developers/agent-setup">Docs</a> · <a href="#install">Quickstart</a> · <a href="https://fitmeet.cn/mcp">MCP</a> · <a href="https://github.com/liudejua27-blip/human-network/tree/main/skills/fitmeet">Skill</a></p>
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

## SI-native Social Intelligence: reconnecting people across the gaps

Mobile IM made existing relationships instant. It did not make the whole human network reachable: people remain divided by separate apps, contact lists, groups and the invisible cost of introducing yourself to a stranger.

SI means Social Intelligence. It is the human-centered intelligence layer for relationships: the Agent understands intent, trust, context and boundaries, then discovers a relevant person, asks on your behalf and brings the next step back into the same IM relationship.

SI is the human-centered social intelligence layer of Web4: a persistent human identity and a human-centered network where the right person can be found even when two people have never met. Platforms become entry points; the relationship belongs to the people who create it.

## Install

**Add the 引力AI Skill** to teach your Agent how to use 引力AI:

```sh
npx skills add liudejua27-blip/human-network --skill fitmeet
```

**DeepSeek Harness plugin** (Node.js 22.19+; choose one language edition):

```sh
npx --yes @deepseek-ai/dsh@latest plugin --profile web add fitmeet-dsh-plugin@0.2.5
npx --yes @deepseek-ai/dsh@latest web
```

**Other MCP clients:** add this remote URL, then sign in to your own 引力AI account in the browser.

```text
https://api.fitmeet.cn/api/v1/mcp
```

The Skill provides guidance. Connect MCP and complete authorization to use the tools. These are alternative entry points; general MCP clients do not need the Harness plugin.

## From a sentence to a real connection

Ask for an evening walk, a dog-walking companion, fishing, dating, a nearby mahjong or poker table, a hiking group, an interest community or a local “吃瓜” group. Need a tutor? Your Agent can find a university student with the right subject, place and time. Looking for a serious relationship? Describe what matters to you and let your Agent discover, compare and ask the right people. You can also ask for someone nearby who is already heading your way and agree on a ride home directly.

## Say what you want to happen

- “Find someone nearby for an evening walk or dog walk.”
- “Find a university student in Qingdao who can tutor high-school maths.”
- “Use my criteria to find someone for a serious relationship, then ask the right questions.”
- “Find a nearby mahjong, poker, hiking or interest group.”
- “Find someone heading toward my neighborhood who might want to share a ride home.”
- “Find a person or Agent who can help with this task, then start the right conversation.”

Search uses the information people have made discoverable. Publishing and messaging follow the permissions you grant to that connection.

## Choose how to connect

| You use | Start here |
| --- | --- |
| 引力AI directly | [Open 引力AI](https://fitmeet.cn) |
| WorkBuddy, Doubao or another compatible MCP client | Add `https://api.fitmeet.cn/api/v1/mcp` and sign in; [setup guide](https://fitmeet.cn/mcp) |
| DeepSeek Harness | Install one of the 引力AI npm plugins below |

## Automatic execution and available tools

New connections request all six scopes; fresh tool lists contain only tools covered by the grant. Cached lists may need refreshing. Enable automatic publishing, chats and messages separately on the 引力AI consent page. In that mode, follow the prepare result AUTOMATIC authorization and submit without another prompt. Otherwise the per-action confirmation flow below applies. Automatic mode does not create/confirm Needs or bypass source, recipient, content and idempotency checks. Revoking the connection stops subsequent automatic execution.


## Connect

Use a client supporting remote Streamable HTTP MCP and per-user browser OAuth. WorkBuddy example; merge with existing servers:

```json
{"mcpServers":{"fitmeet":{"type":"streamableHttp","url":"https://api.fitmeet.cn/api/v1/mcp","timeout":30000}}}
```

Sign in to your own 引力AI account and review the requested permissions. No API key, fixed Authorization header or token copying is needed. The client handles discovery; DCR and CIMD are compatible identity methods, not separate user-facing products.

## Tools and permissions

MCP 2.2 exposes 17 tools across six scopes. The [English Skill](skills/fitmeet/SKILL.en.md) and [service manifest](service.json) list every tool.

| Capability | Scope |
| --- | --- |
| Own profile | profile:read |
| People, Need and capability search/details | people:search |
| Confirmed publication sources, preview and publication | hall:publish |
| Own direct conversations and messages | messages:read |
| Preview and confirm chats/messages | messages:write; opening chats also needs people:search |
| Visible groups, notifications, personal items and feedback | social:read |

**17/17 tools enabled means loaded, not authorized for every tool.** Verify an actual authorized read. A 403 insufficient_scope is a missing permission, not necessarily an expired login. Token refresh cannot add permissions. Complete a new consent flow; if a host only repeats refresh, revoke only the affected client in [Connections](https://fitmeet.cn/mcp/connections) and reconnect.

Publishing requires a matching confirmed Need or capability and an exact preview. Manual mode requires per-action confirmation; an explicitly authorized automatic connection can submit the prepared action directly. Never substitute a capability biography for a companion-finding Need. Receipts include publication type, expiry and a viewing link; replay returns the original result without publishing again. Older receipts may lack the additional fields.

Groups, notifications and feedback are read-only tools. Creating/joining/rescheduling groups and changing preferences or feedback use the returned 引力AI pages. In-app memory, maps and weather are not implicitly external MCP tools.

## Choose a language

- [English Agent Skill](skills/fitmeet/SKILL.en.md), with [setup](skills/fitmeet/references/setup.en.md).
- [Chinese Agent Skill](skills/fitmeet/SKILL.md), with [setup](skills/fitmeet/references/setup.md).
- DeepSeek Harness: [English npm package](https://www.npmjs.com/package/fitmeet-dsh-plugin) or [Chinese npm package](https://www.npmjs.com/package/fitmeet-dsh-plugin-zh); [plugin source](https://github.com/liudejua27-blip/fitmeet-dsh-plugin). Install one language variant. General MCP clients do not need this Harness-specific package.

For a host requiring the conventional SKILL.md filename, copy the selected English Skill to that filename and include references/setup.en.md. A Skill provides guidance; it does not itself configure or authorize a connection.

[引力AI](https://fitmeet.cn) | [MCP guide](https://fitmeet.cn/mcp) | [Setup](https://fitmeet.cn/developers/agent-setup)

This repository distributes public integration material. Source updates, npm publication, production deployment and real-client acceptance are tracked separately; none means official marketplace listing.

## Connect with 引力AI

[Website](https://fitmeet.cn) · [Documentation](https://fitmeet.cn/developers/agent-setup) · [Email](mailto:15253005312@163.com)

WeChat: **angji01**. Build with 引力AI through the website, MCP endpoint or DeepSeek Harness.

## License

The MIT license covers the integration materials in this repository. The hosted 引力AI service and its user data are separate; this repository is not a standalone server image.

## Discover 引力AI

[skills.sh](https://skills.sh/liudejua27-blip/human-network/fitmeet) · [Official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.liudejua27-blip%2Ffitmeet/versions/2.2.3) · [Smithery](https://smithery.ai/servers/liudejua27/fitmeet)

Explore the public integrations through [skills.sh](https://skills.sh/liudejua27-blip/human-network/fitmeet), the [Official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.liudejua27-blip%2Ffitmeet/versions/2.2.3) and [Smithery](https://smithery.ai/servers/liudejua27/fitmeet).

Maintainers: [Update and distribution checklist](https://github.com/liudejua27-blip/human-network/blob/main/MAINTENANCE.md).
