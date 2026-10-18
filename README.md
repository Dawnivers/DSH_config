# DSH_config — DSH 迁移包的远程备份

由 `publish-dsh.ps1` 每周定时生成并覆盖推送，**这是备份仓库，不要手工改这里的内容**。

| 项 | 值 |
| --- | --- |
| 最新包 | [`dsh-20261018-2209.zip`](https://github.com/Dawnivers/DSH_config/blob/main/dsh-20261018-2209.zip) |
| 大小 | 72.56 MB |
| 生成时间 | 2026-10-18 22:13 (Asia/Shanghai) |
| SHA-256 | `1C2C3ECC1A635BFA07608473AF62F1434691AC93D57A4D392F56908C32F1B85D` |
| 保留份数 | 2（最新 + 上一份） |

## 里面有什么
`~/.dsh` 的会话历史、storages、skills、task-board、profile 配置，以及 `~/.mnemon` 的记忆本体
（`runtime/MEMORY.md`、`runtime/USER.md`、`runtime/memories.json`）和所有 `link:` 自研插件源码。
**不含** `node_modules`、缓存、浏览器登录态、`~/.dsh/.credentials.yaml`（如果要连 API 密钥一起备份，
需要单独处理，别把密钥推到公开仓库）。

## 怎么恢复
解压后看包里的 `RESTORE.md`：先装同版本 DSH Desktop → `restore-dsh.ps1` 归位 → 项目代码放回原路径 →
`pnpm install` 重装插件 → 改掉 `cordis.patch.yml` 里的绝对路径。

## 为什么历史只有一个提交
每周全量包 70 MB 左右，正常提交会让仓库一年涨到 3 GB 以上。
所以每次用 `--force` 推一个单提交，只留最近 2 份包 —— 仓库体积恒定，备份照常可用。
