# MCP 与 Harness 分发验收 · 2026-10-17

本次完成现有渠道更新。MCP 2.3.0 提供 23 个工具、7 类权限；Skill 为 1.4.0；中英文 Harness 插件为 0.3.2。各组件独立版本管理。

| 渠道 | 本次结果 | 证据与边界 |
| --- | --- | --- |
| API / MCP | 通过；既有 2.3.0 保持运行 | 健康接口、OAuth discovery、401 challenge、DCR、PKCE S256 与七类权限通过。公开契约未改变，不重复部署后端 |
| 网站 | 已修复并部署 OAuth 授权兼容 | `20261017-mcp-consent-747b3e7031`；BUILD_ID `StWK3juoBCI-yyuqXgtNu`；current 与 PM2 实际目录/脚本一致，online，观测重启 0 |
| npm 英文 | 已公开发布，latest 0.3.2 | [fitmeet-dsh-plugin](https://www.npmjs.com/package/fitmeet-dsh-plugin/v/0.3.2)；registry integrity 与 GitHub 对应安装包相同 |
| npm 中文 | 已公开发布，latest 0.3.2 | [fitmeet-dsh-plugin-zh](https://www.npmjs.com/package/fitmeet-dsh-plugin-zh/v/0.3.2)；registry integrity 与 GitHub 对应安装包相同 |
| GitHub | 0.3.2 标签与双语资产保留；更新当前说明 | [Release](https://github.com/liudejua27-blip/fitmeet-dsh-plugin/releases/tag/v0.3.2)；不改写既有版本标签或资产 |
| skills.sh | 公开页可见，隔离安装比对通过 | [Skill](https://skills.sh/liudejua27-blip/human-network/fitmeet)；安装内容与当前 1.4.0 来源相同，不为未变内容提升版本 |
| Official MCP Registry | active / isLatest，2.3.0 | [Registry API](https://registry.modelcontextprotocol.io/v0.1/servers/io.github.liudejua27-blip%2Ffitmeet/versions/latest)；端点未变，不重复发布 |
| Smithery | SUCCESS；公开页 Tools 23 | [现有条目](https://smithery.ai/servers/liudejua27/fitmeet)；release `9e9af3ac-735b-4f3d-9361-bbdb17690276`，2026-10-17 13:18:40 +08；重新授权并恢复同一发布 |
| Glama | 公开页 23 tools，Healthy | [现有条目](https://glama.ai/mcp/connectors/io.github.liudejua27-blip/fitmeet)；2026-10-17 13:10:16 +08 主动连接测试 success，3801ms |
| Harness | web、headless 配置均安装 0.3.2 | 真实 web 宿主 0.2.0-rc.2 显示插件运行；重启无需再次登录；使用其保存授权经 MCP SDK 读回 23 个工具。headless 仅确认安装，未另做真实宿主验收 |
| iOS | 不适用 | 本轮为 MCP 分发与网站授权修复，没有新增 iOS 构建或上传 |

## 实际修复

网站未把 `social:write` 加入可识别权限，导致包含此权限的授权预览与连接管理无法安全读回。本次补齐名称和说明，拒绝非法/原型继承权限值，去除旧的“全部 17 个工具”文案，并使授权自动执行文案与实际权限一致。网站提交 `7ce8068` 已推送。

Harness 生产 OAuth 检查原先硬编码旧版本和权限；现改为从当前清单推导。检查脚本提交 `4ad3e1e` 已推送；脚本不在 npm 安装包内，0.3.2 原始标签与制品未改变。

本地验证：网站 MCP 相关测试 56 项通过、生产构建通过；Harness 类型检查、14 项测试、构建与公开契约检查通过。MCP 清单、双语 Skills、网站和包的 23/7 契约一致。

## 授权和验收范围

用户明确批准为现有 Glama、Smithery、Harness 测试连接补充 `social:write`。三者均重新取得七类权限；新增授权的“自动执行”保持关闭。测试只发现工具，没有调用创建/加入群组、发布或发消息工具。工具清单可见不代表所有业务流程已验收。

Glama 的历史质量评分仍可能引用旧工具数量；以本次公开 Available Tools 和连接检查时间为准。Smithery 扫描对未声明支持的 resources/prompts 返回 Method not found，但 tools 扫描及发布 SUCCESS；没有向用户提供这两类能力。

skills.sh 当前公开页面包含 10 月 10 日 Snyk W011 提示：工具会读取用户生成内容，存在间接提示注入暴露。Skill 已要求把返回文本视为数据、保留服务端授权与确认边界；本次不将该平台历史风险提示称为“已清除”。

## 制品与回退

- 英文包 SHA-256：`0e8f7e78c5a08b816f8f3cf98c145a5834cf6caffc462cb0fe6653f95edda934`。
- 中文包 SHA-256：`9256c81f5caf85a3b9250f6cbf747fb13f3df0b1578c0cc2d8d8b93d60eaf9d3`。
- 网站构建包 SHA-256：`747b3e70316e00bf2e3a679500cb3fc39b47a46d5e697e903e6b44490ad6d9f5`。
- 网站前版 `20261017-164626bb7e20` 保留；锁文件与依赖声明一致，本版引用其不可变 Linux 依赖，清理前需解除引用。
- 网站生产制品包含既有工作树产品更新，并非单独由授权修复提交构建；精确源码与构建快照、原始回执保存在私有 `distribution-20261017`，不公开账号、令牌或回调参数。

English summary: both npm editions are publicly available at 0.3.2. Smithery and Glama show 23 tools. Harness was upgraded and its saved seven-scope grant was verified after restarting the real web host. The website consent fix is deployed. No group creation, joining, publication or messaging actions were performed during this acceptance.
