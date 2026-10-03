# 引力AI · Yinli AI distribution status

## Current release — 2026-10-03

The public definition is now unified as: “Yinli AI (引力AI, formerly FitMeet) is building the SI (Social Intelligence)-native human connection and instant-messaging network. People come first; Agents apply social intelligence to understand intent, trust, context and boundaries, then connect people who would otherwise never meet.” MCP metadata version 2.2.3 is published and active in the Official Registry with the same HTTPS endpoint and 17-tool contract; the registry readback reports `isLatest: true` at 2026-10-03T14:10:06Z.

The Harness bilingual npm release 0.2.6 is published and public latest for both packages. Local distribution builds pass with typecheck, 14 tests, build and public-contract verification; the public tarballs match the recorded integrity values. Smithery's existing entry now shows the SI (Social Intelligence)-native bilingual human connection network description, and its public page reports 17 tools. Glama's existing entry now shows the same human-centered SI description; its public page reports Healthy, OAuth working and 17 tools.

## Current directory verification — 2026-10-03

| Directory | Verified result |
| --- | --- |
| [skills.sh](https://skills.sh/liudejua27-blip/human-network/fitmeet) | CLI installation source and public page return HTTP 200 with the SI-native 引力AI human connection network description and version 1.3.3. |
| [Official MCP Registry](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.liudejua27-blip%2Ffitmeet/versions/2.2.3) | 2.2.3 active/latest; SI Social Intelligence network description, title 引力AI · Yinli AI and HTTPS endpoint verified. |
| [Smithery](https://smithery.ai/servers/liudejua27/fitmeet) | Current brand visible; release ebd4d5fe-4ca8-4295-ad38-aa4da1ad8894 SUCCESS, MCP 2.2.1 and 17 tools discovered after OAuth. |
| [Glama](https://glama.ai/mcp/connectors/io.github.liudejua27-blip/fitmeet) | Ownership verified, OAuth works, public Healthy and 17 tools; page metadata and description now read the SI-native human connection network definition; last test shown by the signed-in page: 2026-10-02 22:37 China Standard Time. |

Glama currently requests all six scopes, including private-message access and write operations, without a scope editor in the test profile. The first unapproved request was declined; the user subsequently completed authorization and reported successful testing. The authenticated test-profile result was independently read back. Future authorization changes still require a dedicated test account or explicit permission for the requested access. Do not remove authentication to pass a scan.

MCP 2.2.1, Skill/WorkBuddy 1.3.3 and bilingual Harness npm 0.2.3 were distributed in the 2026-09-29 historical verification. Harness profile reading and restart recovery were verified; tool discovery does not prove every business action. See the [complete release evidence](https://github.com/liudejua27-blip/FitMeet-UI/blob/main/docs/deployments/2026-09-29-mcp-distribution.md).

## Historical verification — 2026-09-20

Verified on 2026-09-20. Directory listings are distinct from end-to-end client acceptance, search rankings and platform endorsement.

| Directory | Status | Entry |
| --- | --- | --- |
| skills.sh | Public Skill page exists; official CLI discovery and installation passed in an isolated directory | [FitMeet Skill](https://skills.sh/liudejua27-blip/human-network/fitmeet) |
| Official MCP Registry | Published; API reports active, latest version 2.2.0 | [Registry record](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.liudejua27-blip%2Ffitmeet/versions/2.2.0) |
| Smithery | Release reports SUCCESS; public server information exposes 17 tools | [FitMeet](https://smithery.ai/servers/liudejua27/fitmeet) |
| Glama | Hosted-endpoint submission sent through the signed-in form; public indexing not yet verified | [Connector directory](https://glama.ai/mcp/connectors) |

## What was checked

- Harness 0.2.2: 14 tests, typecheck, build and live public-manifest consistency passed. Production dependency audit: no known advisories returned (96 dependencies). This is not a guarantee against unknown vulnerabilities.
- MCP: 37 server/output tests and typecheck passed. The runtime, public manifest, Skill and plugin agree on 17 tools and six scopes.
- Skill 1.3.3 and WorkBuddy packages build; the Skill installs using `npx skills add liudejua27-blip/human-network --skill fitmeet`.
- Initial requests without an Authorization header now return a 401 discovery challenge without incorrectly claiming that a token expired. Invalid presented credentials retain `invalid_token`; missing scopes remain separate. The fix was deployed and verified at the public endpoint.
- No publishing or messaging was performed to test directory submissions. Registry metadata does not contain user records or credentials.

## Distribution boundaries

The npm packages `fitmeet-dsh-plugin` and `fitmeet-dsh-plugin-zh` are DeepSeek Harness plugins, not generic stdio MCP servers. The Registry record uses `remotes` for the existing HTTPS MCP endpoint. Do not advertise `npm install -g fitmeet` or a public Docker image that has not been built and verified.

[server.json](server.json) follows the official MCP Registry schema. [glama.json](glama.json) declares the maintainer of these integration materials; the Glama page and health result are recorded separately above.

## Maintenance

Recheck the official rules before a new submission: [Registry remote servers](https://modelcontextprotocol.io/registry/remote-servers), [skills.sh](https://skills.sh/docs), [Smithery publishing](https://smithery.ai/docs/build/publish), [Glama FAQ](https://glama.ai/mcp/faq).

Smithery CLI 4.11.1 returned an auth URL that displayed 404; web publishing worked. The directory scan required OAuth. Publication success and advertised schemas do not establish that every downstream client has completed every business action.

For future changes, follow [MAINTENANCE.md](MAINTENANCE.md) and the linked canonical release runbook. Keep submitted, publicly listed and real-client verified stages separate.
