# 随机文本定时写入

工作流：`.github/workflows/random-updata.yml`。

- 每小时第 3、13、23、33、43、53 分钟运行一次，也可在 Actions 页面手动运行。
- 每次向默认分支的 `updata/` 新增一个 UUID 随机名称的 `.txt` 文件，内容为 256 个随机字节的 Base64 文本，不覆盖已有文件。
- 在仓库 Settings → Secrets and variables → Actions 中设置 `UPDATA_GITHUB_TOKEN`，授予目标仓库内容写入权限。凭据只存储在 Actions secret，不写入源码。
- Actions 在 GitHub 云端创建提交。电脑上的同名文件夹需通过 `git pull` 同步。
- GitHub 定时调度可能延迟，不能保证精确十分钟。定时工作流需要存在于默认分支。
- 要停止生成，在 Actions 页面禁用 `Random updata every 10 minutes` 工作流。

文档：[GitHub 定时事件](https://docs.github.com/en/actions/reference/workflows-and-actions/events-that-trigger-workflows#schedule)、[仓库内容 API](https://docs.github.com/en/rest/repos/contents#create-or-update-file-contents)。
