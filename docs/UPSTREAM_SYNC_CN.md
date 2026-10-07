# 上游同步流程

## 上游

~~~
https://github.com/router-for-me/Cli-Proxy-API-Management-Center
~~~

## 安全同步

首次：

~~~bash
git remote add upstream https://github.com/router-for-me/Cli-Proxy-API-Management-Center.git
~~~

以后：

~~~bash
git fetch upstream
git checkout main
git pull origin main
git checkout -b sync/upstream-YYYYMMDD
git merge upstream/main
~~~

禁止：

~~~bash
git reset --hard upstream/main
git push --force
~~~

## 冲突重点

重点保护维护版内容：

- quota-drain RoutingStrategy。
- 路由策略解析和 YAML 写回。
- 路由策略 UI。
- 所有相关 i18n 文案。
- Quota Drain 测试。
- .github/workflows/qing-panel-release.yml。
- README 和 docs 维护版文档。

上游如果改变 routing config 契约，必须同时核对 Qing842/CLIProxyAPI 后端。

## 验证

~~~bash
bun install --frozen-lockfile
bun run verify
~~~

同步完成后通过 PR 合并回 main，再确认 qing-panel-release 成功生成新的 management.html。
