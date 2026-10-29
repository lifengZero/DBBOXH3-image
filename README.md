# 当贝 H3 精简固件

**简体中文** | [English](README.en.md)

适用于 **当贝 H3 / RK3566 / Android 11 对应基础固件**，不适用于 H3S 或其他型号。

## 特点

- 精简原厂桌面、播放器、屏保、OTA、工厂测试、备份及部分预装应用。
- 默认使用 Aerial，取消桌面白名单，可自行更换其他兼容桌面。
- 自动授权 root，无须手动确认；底层保留 Magisk/Kitsune，管理器默认禁用。
- 无线 ADB 持续开启，端口 `5555`，无需认证。
- 框架和 Aerial 已预编译，替换静音开机动画，优化启动及 Home 键重复激活逻辑。
- 保留蓝牙遥控器配对、首次设置向导和系统 WebView。

预装应用：**Aerial、BV、当贝市场、LXTV（ARM64）、OK 影视、WebViewTV**。

## 下载与校验

固件体积较大，通过 [GitHub Releases](https://github.com/lifengZero/DBBOXH3-image/releases/tag/v1.0.0) 提供，不存放在 Git 仓库中。

1. 下载 Release 中的 `H3_RK3566_Android11_Aerial_AOT_AUTO_ROOT_ADB5555.img.gz`。
2. 使用 7-Zip 或其他支持 gzip 的工具解压，得到完整的 `.img` 文件；不要直接刷入 `.gz` 文件。
3. 使用仓库或 Release 中的同名 `.img.sha256` 文件核对解压后 IMG 的 SHA-256。Release 另提供 `.img.gz.sha256`，用于校验压缩包。

解压后 IMG 的 SHA-256：

```text
f996379a140d8a2b6e3c3b5e9b10bd80d1f18c7a9cf21dd3674470712f181f3e
```

## 刷机方法

使用完整固件：

```text
H3_RK3566_Android11_Aerial_AOT_AUTO_ROOT_ADB5555.img
```

1. 在 Windows 电脑上准备瑞芯微 USB 驱动和 RKDevTool。
2. 通过 USB 连接设备，按设备原有线刷方法进入 **Loader 模式**。
3. 确认工具识别到设备，在 **“升级固件”** 中加载上述 IMG，执行升级。
4. 等待升级成功后重启，刷写期间不要断电或拔线。
5. 首次开机完成蓝牙遥控器配对和网络设置，等待应用安装完成后进入 Aerial。

**这是完整升级包，不要当作 boot 分区镜像写入，也不需要额外刷入 boot 或手动授权 root。**

## 无线 ADB

将示例 IP 替换为设备实际 IP：

```bash
adb connect 192.168.1.100:5555
adb shell su -c id
```

root 正常时，输出包含 `uid=0(root)`。

## 注意事项

- **所有应用申请 root 都会自动允许，无线 ADB 也没有认证。仅在可信网络使用，不要开放到公网或安装不可信应用。**
- 首次启动仍需初始化和安装应用，部分应用可能需要编译，请耐心等待。
- Aerial 可用同包名、同签名且兼容 Android 11 的新版 APK 覆盖升级，无须重刷固件。
