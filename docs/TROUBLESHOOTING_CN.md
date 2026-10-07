# 故障排查

## 页面没有 Quota Drain 选项

先确认打开的是 Qing842 Release 的 management.html，而不是上游面板缓存。

同时确认当前前端源码包含 quota-drain RoutingStrategy 和对应本地化文案。

## 保存 Quota Drain 后又变回其他策略

确认后端已经升级到支持 quota-drain 的 Qing842/CLIProxyAPI。前端只负责提交配置，后端契约不支持时不能靠 UI 修复。

## 后端没有下载新面板

检查后端：

~~~yaml
management:
    panel-github-repository: "https://github.com/Qing842/Cli-Proxy-API-Management-Center"
~~~

并确认最新 Release 存在 management.html。

## Release workflow 失败

按顺序检查：

1. bun install --frozen-lockfile。
2. bun run build。
3. dist/index.html 是否生成。
4. GITHUB_TOKEN 是否具有 contents: write。
5. 同名 Release tag 是否已存在。

## 页面构建后依赖外部静态文件

这是不允许的。生产约束是单文件 management.html。检查 Vite 配置、动态 import、资源加载和 vite-plugin-singlefile 行为。
