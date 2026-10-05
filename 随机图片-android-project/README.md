# 随机图片

由 **HTML → APK 在线打包工具** 自动生成的 Android 工程。

## 应用信息

| 项目 | 值 |
| --- | --- |
| 应用名称 | 随机图片 |
| 包名 | com.example.webapp |
| 版本 | 5.2.1 (1314) |
| 内容来源 | 本地网页 assets/www/ios.html |
| 最低系统 | Android 5.0 (API 21) |

## 方式一：GitHub Actions 自动构建（推荐）

1. 把本目录所有文件上传到一个 GitHub 仓库（保持目录结构不变）
2. 打开仓库的 **Actions** 页面
3. 等待 **Build APK** 工作流执行完成
4. 在该次运行的页面底部 **Artifacts** 中下载 `app-debug`，解压得到 APK

> 首次运行会自动安装 Android SDK 组件，通常 2～5 分钟。

## 方式二：Android Studio 本地构建

1. `File → Open` 选择本目录
2. 等待 Gradle Sync 完成
3. `Build → Build Bundle(s) / APK(s) → Build APK(s)`
4. APK 输出路径：`app/build/outputs/apk/debug/app-debug.apk`

## 方式三：命令行

```bash
gradle assembleDebug
```

## 修改网页内容

直接编辑 `app/src/main/assets/www/` 下的文件即可，重新构建后生效。

## 关于签名

当前 release 构建复用了 debug 签名，仅供测试安装。
正式发布请自行生成 keystore：

```bash
keytool -genkey -v -keystore my-release.jks -keyalg RSA -keysize 2048 -validity 10000 -alias mykey
```

然后在 `app/build.gradle` 中配置 `signingConfigs.release`。
