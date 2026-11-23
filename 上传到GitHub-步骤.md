# 把工程上传到 GitHub（拿到 iPhone 安装包的必经步骤）

> 目标：让 GitHub 的 macOS 云机器帮我们打包出 `TimeCapsule-unsigned.ipa`。
> 全程只需要 GitHub 账号，不需要 Mac、不需要命令行。

## 第 1 步：新建仓库

1. 电脑浏览器打开 https://github.com/new
2. **Repository name** 填：`timecapsule-ios`
3. 可见性选 **Public**（公开仓库的 Actions 分钟数完全免费；Private 也可以，每月 2000 分钟够用）
4. 不要勾选 "Add a README file"（留空即可）
5. 点绿色 **Create repository**

## 第 2 步：上传工程文件

1. 新仓库页面点 **uploading an existing file**（或 Add file → Upload files）
2. 打开桌面上的 `时间胶囊-iOS工程` 文件夹
3. **Ctrl+A 全选**里面的所有内容（`.github`、`ios`、`www`、package.json 等）
4. 拖进网页的上传区域，等文件列表加载完
5. 下方点绿色 **Commit changes**

> 如果拖拽上传失败，可以改用 GitHub Desktop：
> 安装后 Add local repository → 选 `桌面\时间胶囊-iOS工程` → Publish repository，效果一样。

## 第 3 步：运行自动打包

1. 点仓库顶部 **Actions** 标签
2. 第一次会看到提示，点 **I understand my workflows, go ahead and enable them**
3. 左侧选 **Build iOS IPA (unsigned)** → 右侧 **Run workflow** → 绿色按钮
4. 等 10–15 分钟，状态变成绿色 ✔
5. 点进那次运行，页面底部 **Artifacts** 下载 `timecapsule-ios-ipa`
6. 解压得到 **`TimeCapsule-unsigned.ipa`**

## 第 4 步：装进 iPhone（Windows 上完成）

1. 电脑下载安装 [Sideloadly](https://sideloadly.io/)
2. iPhone 数据线连电脑
3. Sideloadly 里选择 `TimeCapsule-unsigned.ipa`
4. **Apple ID** 填你自己的免费 Apple ID（只用于签名，不收集密码）
5. 点 **Start**，等进度条完成
6. iPhone：设置 → 通用 → **VPN与设备管理** → 点你的开发者证书 → **信任**
7. 回桌面点胶囊宝宝图标，就是实体 App 了

> 免费签名 7 天有效，到期用 Sideloadly 再点一次 Start 即可，App 内数据保留。

## 常见问题

| 问题 | 处理 |
| --- | --- |
| Actions 报错红色 ❌ | 把日志里第一条红色错误截图发我，我改工程 |
| 第一次打开提示"未受信任的开发者" | 去设置 → 通用 → VPN与设备管理 → 信任 |
| 7 天后打不开 | 重新用 Sideloadly 签一次 |
| 想上架 App Store / TestFlight | 需要 Apple Developer Program（$99/年），有账号后找我配签名 |
