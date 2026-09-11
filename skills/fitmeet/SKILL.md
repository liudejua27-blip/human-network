---
name: fitmeet
description: Search the FitMeet human network for people, needs, and capabilities; publish or manage one-to-one chats only with the user's own OAuth authorization and explicit confirmation for every outward action.
---

# FitMeet Human Network

Use this Skill when the user wants to find a suitable person, collaborator, peer, activity partner, public need, or relevant capability through FitMeet.

## Connect

Use the hosted MCP configuration from the repository root:

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

Do not add a shared token, API key, or fixed `Authorization` header. Allow the MCP client to follow FitMeet's OAuth discovery flow. Each user must sign in to their own FitMeet account and approve the scopes needed for the current task. Never ask the user to paste a password, verification code, access token, or refresh token into chat.

## Tools

- Profile and discovery: `fitmeet_profile_get`, `fitmeet_people_search`, `fitmeet_people_details`
- Publishing: `fitmeet_publication_sources`, `fitmeet_publication_prepare`, `fitmeet_publication_confirm`
- Conversation history: `fitmeet_conversations_list`, `fitmeet_messages_list`
- Start a chat: `fitmeet_chat_prepare`, `fitmeet_chat_confirm`
- Send a message: `fitmeet_message_prepare`, `fitmeet_message_confirm`

Tool names may have a host namespace. Use the current connection's `tools/list` result as the authority.

## Search behavior

Preserve the user's complete request in `requestText`. Ask only one important clarifying question when missing information would materially change the results. Explain the returned evidence and unknown conditions without inventing scores, availability, distance, or a platform-wide result count.

Only profiles whose owners enabled external discovery may appear. Search authorization does not mean a candidate agreed to contact, meet, or transact. Keep recommendations in the current conversation so the user can revisit who was recommended.

## Publishing and messaging

Publishing, opening a chat, and sending a message always require:

1. Call the matching `prepare` tool.
2. Show the exact preview, audience or recipient, and message text.
3. Obtain explicit user confirmation in the current interaction.
4. Submit the unchanged confirmation identifier and digest to the matching `confirm` tool.

If the user edits anything or the confirmation expires, prepare a new preview. OAuth consent is not action confirmation. Opening a chat creates an empty conversation and does not send a message.

Do not claim an action completed unless the final tool receipt says it executed. Do not use another tool to bypass the prepare-and-confirm flow.

## Boundaries

This Skill does not modify profiles, make payments or bookings, write calendars, perform administrator actions, send bulk messages, or invite people automatically. Keep private conversation content out of public answers and unrelated tools.

On `401`, revoked authorization, or expired credentials, use the host's reconnect flow. On insufficient scope, reconnect and request only the scope needed for the current operation.
