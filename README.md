# 当贝 H3 精简固件

**简体中文** | [English](README.en.md)

适用于 **当贝 H3** 盒子（RK3566 / Android 11），不适用于其他型号。

## 预装应用

- CleanYourTV 桌面（已开启应用库和系统状态显示）
- 影视 5.8.7（ARM64）
- BV
- 洛雪音乐（LXTV，ARM64）
- WebViewTV
- LeanCast（开机自启）
- TVFileBox（文件管理，已授予安装应用权限）

## 已删除的应用

- 当贝市场
- 当贝文件管理器
- Rocky 语音服务
- 设置智能服务（SettingsIntelligence）
- 联系人存储（ContactsProvider）
- 用户词典存储（UserDictionaryProvider）
- VPN 对话框（VpnDialogs）
- SecureElement、CompanionDeviceManager、CaptivePortalLogin、PacProcessor、ProxyHandler、StatementService
- 首次启动时卸载：launcher3.guide、andes、etna.sample、leradwatcher、ota3435、needle、projector.direction、zhushou.os、dbmusic.tab、dbdownloadrefs

## 下载与刷机

从 [Releases v1.5.0](https://github.com/lifengZero/DBBOXH3-image/releases/tag/v1.5.0) 下载固件：

```text
H3_RK3566_Android11_CleanYourTV_CURRENT_NOWIPE_ADB5555.img.gz
```

1. 解压 `.gz` 得到完整 `.img`，可用随附的 `.sha256` 文件校验。
2. 在电脑安装瑞芯微 USB 驱动，准备 RKDevTool（macOS 可用 `upgrade_tool`）。
3. 通过 USB 连接盒子，按原有线刷方法进入 **Loader 模式**。
4. 在 RKDevTool 的 **“升级固件”** 中加载解压后的 IMG，执行升级。
5. 等待升级成功后重启，首次开机等待应用安装完成，再设置网络、配对遥控器。

**刷机会清除用户数据和蓝牙配对，请提前备份并保留原厂固件。不要直接刷入 `.gz`，不要当作 boot 分区镜像写入，刷写期间不要断电或拔线。**

## 遥控器配对

**同时按住遥控器的 Home 键和设置键，听到“滴”声后松手，等待配对完成。**

遥控器尚不可用时，可连接 USB 鼠标或键盘进入蓝牙设置。

## 注意

无线 ADB 持续开启，端口 `5555`，无需认证。仅在隔离可信网络使用，不要开放到公网或安装不可信应用。
