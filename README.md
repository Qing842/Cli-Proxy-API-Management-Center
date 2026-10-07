# Qing842 CLI Proxy API Management Center

This repository is the maintained Qing842 fork of CLI Proxy API Management Center.

It tracks the upstream management UI while preserving Qing842-specific production integration, especially Quota Drain routing support and the custom management.html release pipeline.

## Fork-specific responsibilities

- Expose Quota Drain in the routing strategy UI.
- Keep the backend v8 configuration contract in sync with the Qing842 CLIProxyAPI fork.
- Build a single-file management.html artifact.
- Publish a GitHub Release automatically from main.
- Provide handover, release, deployment, and upstream-sync documentation.

## Documentation

- Chinese overview: README_CN.md
- Handover: docs/HANDOVER_CN.md
- Architecture: docs/ARCHITECTURE_CN.md
- Deployment: docs/DEPLOYMENT_CN.md
- Release process: docs/RELEASE_CN.md
- Upstream synchronization: docs/UPSTREAM_SYNC_CN.md
- Troubleshooting: docs/TROUBLESHOOTING_CN.md

## Repositories

Maintained fork:
https://github.com/Qing842/Cli-Proxy-API-Management-Center

Upstream:
https://github.com/router-for-me/Cli-Proxy-API-Management-Center

Backend fork:
https://github.com/Qing842/CLIProxyAPI

## License and attribution

This project remains under the upstream MIT license. Keep LICENSE and its copyright notices intact.
