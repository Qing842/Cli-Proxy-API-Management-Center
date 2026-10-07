# 管理中心发布流程

## 自动发布

工作流：

~~~
.github/workflows/qing-panel-release.yml
~~~

触发：push 到 main。

流程：

1. Node.js 24。
2. Bun 1.3.14。
3. bun install --frozen-lockfile。
4. bun run build。
5. dist/index.html -> dist/management.html。
6. gh release create 发布 management.html。

## 当前版本格式

截至 2026-10-07，workflow 使用：

~~~
v1.25.4-qing.<github-run-number>
~~~

例如首个维护版 Release：

~~~
v1.25.4-qing.1
~~~

注意：v1.25.4 当前写在 workflow 中。以后同步到新的上游管理中心版本时，应主动评估并更新这个前缀，避免 Release 名称长期停留在旧基线。

## 发布验收

main 更新后确认：

- tests / lint / build 相关 CI 通过。
- qing-panel-release 通过。
- latest Release 对应本次 main 提交。
- Release 资产名称严格为 management.html。
- 后端可以下载并更新面板。
