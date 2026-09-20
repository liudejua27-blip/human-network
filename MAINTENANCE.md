# Maintaining FitMeet integrations

[中文完整操作流程 / Canonical release runbook](https://github.com/liudejua27-blip/FitMeet-UI/blob/main/docs/MCP_DISTRIBUTION_RUNBOOK.md) · [Verified distribution status](DISTRIBUTION.md)

Review every channel after each public update. Record passed, failed, pending or not applicable with evidence; a GitHub push does not update running services or installed packages.

## Change checklist

1. Compare the current FitMeet runtime with `service.json`, `mcp.json`, both Skill languages and their references. Keep the public endpoint and real capability boundaries consistent.
2. Update the matching materials in FitMeet-UI, the website and Harness. Keep MCP, Skill and plugin versions independent. Rebuild WorkBuddy downloads when their contents change.
3. Run the cross-repository contract checks described in the canonical runbook. Deploy affected backend and website assets before advertising the new capability.
4. Push this repository; verify discovery and installation in an isolated directory with `npx skills add liudejua27-blip/human-network --skill fitmeet`. Compare installed content with the intended commit. GitHub changes do not update existing local installations automatically.
5. If Harness bundle content changes, publish both language packages using the [plugin release guide](https://github.com/liudejua27-blip/fitmeet-dsh-plugin/blob/main/RELEASING.md). Updating this repository does not update npm.
6. Update affected directory records below, then record public readback and pending reviews in `DISTRIBUTION.md` and the canonical release status. Preserve dated historical evidence.

## Directory updates

| Channel | Source and required action |
| --- | --- |
| skills.sh | GitHub `skills/fitmeet/`; verify CLI installation and [public page](https://skills.sh/liudejua27-blip/human-network/fitmeet). Indexing may lag. |
| Official MCP Registry | `server.json`; publish a new unique version only when the Registry record changes. Keep `io.github.liudejua27-blip/fitmeet` and the remote HTTPS transport. Read back active/latest status and endpoint. Versions cannot be overwritten. |
| Smithery | Update the existing [liudejua27/fitmeet](https://smithery.ai/servers/liudejua27/fitmeet) settings or release; rescan changed tools with OAuth, verify SUCCESS and the public page. |
| Glama | Check the existing hosted-endpoint submission first. Public listing/claim remains unverified as of 2026-09-20. Update the approved entry or its actual upstream metadata source; do not create duplicates. `glama.json` is repository maintainer metadata, not proof of a claimed hosted connector. |

Use official login flows and keep publisher credentials, OAuth parameters and user data outside Git. Do not remove authentication to pass a directory scan. Schema discovery is not authorization or successful execution of every tool.

Public contacts: WeChat **angji01**, email **15253005312@163.com**. Discord and X are not yet available. Do not advertise a generic `fitmeet` npm CLI or a Docker image unless those exact artifacts have been published and independently verified.
