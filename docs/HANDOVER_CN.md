# 管理中心交接总览

最后更新：2026-10-07

## 1. 仓库关系

维护版管理中心：
https://github.com/Qing842/Cli-Proxy-API-Management-Center

上游管理中心：
https://github.com/router-for-me/Cli-Proxy-API-Management-Center

维护版后端：
https://github.com/Qing842/CLIProxyAPI

生产后端的 management.panel-github-repository 必须指向维护版管理中心仓库，才能自动拉取本仓库 Release 中的 management.html。

## 2. 当前生产发布基线

截至 2026-10-07，已发布维护版 Release：

~~~
v1.25.4-qing.1
~~~

Release 必须包含：

~~~
management.html
~~~

后端不会使用本仓库源码直接渲染管理中心，而是通过 Release 下载单文件产物。

## 3. 自定义功能

### Quota Drain UI

管理中心增加了 Quota Drain 路由选项，并与后端配置值保持一致：

~~~
quota-drain
~~~

修改路由策略相关 UI 时，必须同步检查：

- RoutingStrategy 类型。
- 配置读写和兼容解析。
- Dashboard / Network 配置显示。
- 所有源语言文件。
- 相关 Bun 测试。

### 自定义 Release

工作流：

~~~
.github/workflows/qing-panel-release.yml
~~~

main 每次更新后自动：

1. 安装 Bun 依赖。
2. 构建单文件页面。
3. 将 dist/index.html 重命名为 dist/management.html。
4. 创建 GitHub Release。

## 4. 维护规则

- 后端 API 契约以 Qing842/CLIProxyAPI 为准。
- 不新增 v0 Management API 兼容层。
- 保持单文件发布，不能引入运行时必需的外部静态资源。
- 新增 UI 文案必须同步所有仓库要求的语言文件。
- 上游同步必须走临时同步分支和 PR。
- LICENSE 保留上游 MIT 许可。

## 5. 交接检查清单

接手者至少需要确认：

1. 能访问管理中心和后端两个 Qing842 Fork。
2. 能运行 bun install --frozen-lockfile 和 bun run verify。
3. 知道管理中心发布物必须叫 management.html。
4. 知道后端通过 panel-github-repository 获取 latest Release。
5. 知道 Quota Drain 是维护版跨仓库功能，前后端必须同时兼容。
6. 知道 qing-panel-release.yml 当前版本号前缀需要随维护基线主动更新。
