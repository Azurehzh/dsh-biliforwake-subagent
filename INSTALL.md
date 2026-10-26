# 刷B站（dsh-bili-subagent 0.8.6）安装说明

> dsh-bili-scroll 的改版：派子代理去刷、按设置评论/私信，带「互动根本原则」、发动态/图文/投稿。

## 安装

### 方式一：GitHub

把本目录（`package.json` 在根）推到仓库，然后：

```bash
dsh plugin --profile desktop add github:<用户名>/<仓库>
```

或 DSH **设置 → 插件 → 安装** 填 `github:<用户名>/<仓库>`，装完**重启 DSH**。

### 方式二：离线

1. 解压，把 `dsh-bili-subagent` 放到：
   ```
   %USERPROFILE%\.dsh\profiles\<profile>\node_modules\dsh-bili-subagent
   ```
2. 在 profile 的 `cordis.patch.yml` 加：
   ```yaml
   - insert:
       - id: bili-scroll
         name: dsh-bili-subagent
   ```
   （或把 `"dsh-bili-subagent"` 加进 `dsh.profile.bundles`）
3. **重启 DSH**。

> `id: bili-scroll` 与原版 dsh-bili-scroll 相同，两者只能启用一个。

## 首次使用

1. **设置 → 刷B站**；
2. 「装主依赖」（需要 Python 3.10+ 或 uv，插件可自下载 uv）；
3. 「扫码登录」，手机 B站 扫码并选「记住我」；
4. 要发动态/图文/投稿，分别打开对应开关；
5. 「测一下」自检登录 + 搜索。

## 与尾波配套

- 尾波空闲思考后可按概率把想法写进
  `%USERPROFILE%\.dsh\bili-duty\dynamic-queue\*.json`；
- 本插件每 **5 分钟**扫一次队列，发之前检查「允许发动态」和「互动根本原则」；
- 公开评论/动态/图文/投稿里出现手机号、身份证、邮箱等隐私会被直接拦下；
- 自动刷轮间隔固定 180 分钟（在设置里可改）。

运行数据：`%USERPROFILE%\.dsh\bili-duty\`（凭证、venv、日报、队列）。
