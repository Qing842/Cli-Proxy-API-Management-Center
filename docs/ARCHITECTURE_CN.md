# 管理中心架构说明

## 总体结构

~~~
Browser
  |
  v
management.html
  |
  v
CLIProxyAPI /v8/management
  |
  +-- config
  +-- auth files
  +-- quotas
  +-- logs
  +-- plugins
~~~

管理中心只是前端，不是代理服务本身。

## 单文件发布

Vite 使用单文件构建，最终生成：

~~~
dist/index.html
~~~

Release workflow 将其重命名为：

~~~
management.html
~~~

后端的 Management Asset updater 下载这个文件并提供管理界面。

## Quota Drain 跨仓库契约

前端配置值：

~~~
quota-drain
~~~

必须与后端支持的 routing.strategy 完全一致。

管理中心负责配置和展示，不负责配额采集或账号选择。真正的 Quota Drain 计算位于后端 Qing842/CLIProxyAPI。

## 关键目录

~~~
src/features/
src/services/api/
src/stores/
src/types/
src/i18n/locales/
tests/
.github/workflows/qing-panel-release.yml
~~~

新增 provider 或修改配置契约时先核对后端实现，不能在 UI 中猜测字段。
