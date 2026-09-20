# FitMeet directory publication and verification

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
- Skill 1.3.2 and WorkBuddy packages build; the Skill installs using `npx skills add liudejua27-blip/human-network --skill fitmeet`.
- Initial requests without an Authorization header now return a 401 discovery challenge without incorrectly claiming that a token expired. Invalid presented credentials retain `invalid_token`; missing scopes remain separate. The fix was deployed and verified at the public endpoint.
- No publishing or messaging was performed to test directory submissions. Registry metadata does not contain user records or credentials.

## Distribution boundaries

The npm packages `fitmeet-dsh-plugin` and `fitmeet-dsh-plugin-zh` are DeepSeek Harness plugins, not generic stdio MCP servers. The Registry record uses `remotes` for the existing HTTPS MCP endpoint. Do not advertise `npm install -g fitmeet` or a public Docker image that has not been built and verified.

[server.json](server.json) follows the official MCP Registry schema. [glama.json](glama.json) declares the maintainer of these integration materials; it does not prove that the hosted connector is already claimed or indexed.

## Maintenance

Recheck the official rules before a new submission: [Registry remote servers](https://modelcontextprotocol.io/registry/remote-servers), [skills.sh](https://skills.sh/docs), [Smithery publishing](https://smithery.ai/docs/build/publish), [Glama FAQ](https://glama.ai/mcp/faq).

Smithery CLI 4.11.1 returned an auth URL that displayed 404; web publishing worked. The directory scan required OAuth. Publication success and advertised schemas do not establish that every downstream client has completed every business action.
