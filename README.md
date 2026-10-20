# PanSou - LazyCat App

[PanSou](https://github.com/fish2018/pansou)（高性能网盘资源搜索：TG 频道 + 70+ 插件并发搜索、智能排序、网盘类型分类）的懒猫微服（LazyCat）打包。

## 模式

- **镜像模式（mirror）**：`ghcr.io/fish2018/pansou-web`（前后端集成镜像）经 `ghcr.nju.edu.cn` 加速拉取，`require_digest_match: true` 校验镜像内容与上游一致。
- **自动跟随上游**：GHCR 无版本 tag（`latest` 可变），采用 digest 比对 + `bump: patch`——上游更新 `latest` 后自动 patch +1 发布。
- **喵喵商店发布**：仅私有商店（MiaoMiao private store），不发布官方商店。

## 说明

- 单容器（Go 后端 + nginx 前端一体，端口 80），数据卷 `/lzcapp/var/pansou:/app/data`（缓存/日志）
- 默认 TG 频道（100+）与推荐插件（70+）已内置于镜像，开箱即用
- **认证默认关闭**；设置向导可开启（JWT），账号格式 `user:pass,user2:pass2`
- 健康检查 `/api/health`（nginx 与后端双检）
- 仅供学习研究，请勿用于盈利目的（上游声明）

## 所需 Secrets

| Secret | 说明 |
| --- | --- |
| `APPSTORE_URL` / `APPSTORE_TOKEN` | 喵喵商店 API 地址与发布令牌 |
| `APP_ID` | 可选 |
| `PRIVATE_STORE_GROUP_CODES` | 可选，私有分组码 |

## 许可

MIT（上游）
