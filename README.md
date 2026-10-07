# Qing842 CLI Proxy API Management Center 维护版

[中文](README.md) | [English](README_EN.md)

这是 Qing842 维护的 CLI Proxy API Management Center Fork。它与 Qing842 CLIProxyAPI 后端配套使用，目标是在持续同步上游 UI 的同时，稳定保留维护版功能、单文件发布流程和交接资料。

## 当前维护版差异

1. 支持 Quota Drain（额度消耗优先）路由策略。
2. main 更新后自动构建单文件管理中心。
3. dist/index.html 会重命名为 management.html。
4. management.html 自动发布到 GitHub Release。
5. 后端 production config 通过 management.panel-github-repository 指向本仓库。

后端仓库：
https://github.com/Qing842/CLIProxyAPI

## 文档入口

- 交接总览：docs/HANDOVER_CN.md
- 架构：docs/ARCHITECTURE_CN.md
- 部署：docs/DEPLOYMENT_CN.md
- 发布流程：docs/RELEASE_CN.md
- 同步上游：docs/UPSTREAM_SYNC_CN.md
- 故障排查：docs/TROUBLESHOOTING_CN.md

## 技术栈

- React 19
- TypeScript
- Vite 8
- Bun 1.3.14
- 后端 API：仅 v8 Management API
- 发布物：单文件 management.html

## 上游关系

维护版：
https://github.com/Qing842/Cli-Proxy-API-Management-Center

上游：
https://github.com/router-for-me/Cli-Proxy-API-Management-Center

同步上游必须走临时同步分支和 PR，不要用 reset --hard 或 force push 覆盖维护版 main。

## License

本项目沿用上游 MIT License。LICENSE 必须保留原版权声明和许可文本。
