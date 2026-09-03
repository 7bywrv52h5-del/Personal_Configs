# sing-box filter converter

把 AdGuard 域名过滤列表转成 sing-box 的 `.srs` 规则集，并用 GitHub Actions 每日自动更新。转换完全在 GitHub 云端完成，本地不需要安装任何东西、也不需要跑脚本。

## 怎么用

GitHub Actions 会在每天凌晨（UTC 04:00）自动下载 `filter_1.txt`、转换成 `filter_1.srs` 并提交回仓库。直接引用它：

```text
https://raw.githubusercontent.com/7bywrv52h5-del/Personal_Sing-box_and_Surge_Configs/main/filter_1.srs
```

在 sing-box 配置里这样引用：

```json
{
  "type": "remote",
  "tag": "adblock",
  "url": "https://raw.githubusercontent.com/7bywrv52h5-del/Personal_Sing-box_and_Surge_Configs/main/filter_1.srs",
  "update_interval": "24h"
}
```

## 添加更多过滤列表

编辑 [.github/workflows/update.yml](.github/workflows/update.yml)，把 `FILTER_URL` 换成别的列表，或按同样格式多复制一段 `Download and convert filter` 步骤即可。
