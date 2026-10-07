# 管理中心部署说明

## 实际部署方式

管理中心不单独部署 Web Server。生产由 CLIProxyAPI 后端托管 management.html。

后端配置：

~~~yaml
management:
    disable-control-panel: false
    panel-github-repository: "https://github.com/Qing842/Cli-Proxy-API-Management-Center"
~~~

如果 disable-auto-update-panel 未显式设置为 true，后端会进行自动更新检查。

## 发布后验证

1. GitHub Release 中确认存在 management.html。
2. 后端 panel-github-repository 指向 Qing842 Fork。
3. 重启后端时，Management Asset updater 会立即检查最新面板。
4. 打开管理中心，确认 Quota Drain 出现在路由策略选项中。
5. 修改并保存配置后，后端 config.yaml 应得到 strategy: quota-drain。

## 本地构建

~~~bash
bun install --frozen-lockfile
bun run verify
bun run build
~~~

构建结果必须保持单文件，不要手工提交 dist。
