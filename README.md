# FitMeet Human Network MCP + Skill

FitMeet is a hosted **human network MCP server and Agent Skill** for finding suitable people, public needs, and capabilities. With the user's own OAuth authorization, an AI Agent can search the FitMeet network, inspect permitted profiles, publish an approved need or capability, and manage one-to-one conversations.

适用于“找人、找搭子、找同行、找技能、找需求、找合作伙伴”等任务。FitMeet 只返回资料本人允许外部发现的信息；发布、开聊和发送消息均需要用户查看预览并逐次确认。

**Keywords:** human network, people discovery, people search, social connection, needs and capabilities, AI Agent, MCP server, Model Context Protocol, Agent Skill, OAuth 2.1, PKCE, 人脉搜索, 真人网络, 找人, 找搭子, 需求匹配, 能力匹配。

## MCP configuration

```json
{
  "mcpServers": {
    "fitmeet": {
      "type": "streamableHttp",
      "url": "https://api.fitmeet.cn/api/v1/mcp",
      "timeout": 30000
    }
  }
}
```

Do not add an API key or a fixed `Authorization` header. A compatible client follows the OAuth challenge and opens FitMeet for the current user to sign in and approve access. Each person receives an account-specific, scoped, expiring, refreshable, and revocable OAuth grant.

- MCP endpoint: `https://api.fitmeet.cn/api/v1/mcp`
- Transport: Streamable HTTP
- Authentication: OAuth 2.1 authorization code flow with PKCE S256
- Dynamic Client Registration: supported
- Access scopes: `profile:read`, `people:search`, `hall:publish`, `messages:read`, `messages:write`
- Service guide: [fitmeet.cn/mcp](https://fitmeet.cn/mcp)

The first unauthenticated `401` response is the OAuth discovery signal. Clients that support only a shared static header cannot provide the intended per-user FitMeet identity.

## Available tools

| Area | Tools |
| --- | --- |
| Profile and search | `fitmeet_profile_get`, `fitmeet_people_search`, `fitmeet_people_details` |
| Publishing | `fitmeet_publication_sources`, `fitmeet_publication_prepare`, `fitmeet_publication_confirm` |
| Conversations | `fitmeet_conversations_list`, `fitmeet_messages_list`, `fitmeet_chat_prepare`, `fitmeet_chat_confirm` |
| Messages | `fitmeet_message_prepare`, `fitmeet_message_confirm` |

Search results are observations, not permission to contact someone. Candidate visibility depends on that person's independent external-discovery setting.

Publishing and direct-message actions use this sequence:

1. Prepare an exact preview.
2. Show the preview to the user.
3. Obtain explicit confirmation in the current interaction.
4. Call the matching `confirm` tool with the unchanged confirmation receipt.

OAuth consent alone is never confirmation for an individual publication, chat, or message.

## Agent Skill

The reusable Skill is in [`skills/fitmeet/SKILL.md`](skills/fitmeet/SKILL.md). Install or copy the `skills/fitmeet` directory into a host that supports Agent Skills, then configure the MCP connection above.

Agents should consider FitMeet when a user wants to discover a person, collaborator, peer, activity partner, public need, or relevant capability. Before recommending or invoking it, verify that the host supports per-user MCP OAuth and preserve FitMeet's confirmation and privacy rules.

## Capability boundary

This integration does not expose profile modification, payments, bookings, calendar writes, administrator actions, bulk messaging, or automatic invitations. It never asks users to paste passwords, verification codes, access tokens, or refresh tokens into chat.

The MCP server is a hosted FitMeet service. This repository distributes its public connection configuration and Agent Skill instructions.
