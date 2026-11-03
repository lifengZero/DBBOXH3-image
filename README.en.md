# Dangbei H3 Debloated Firmware

[简体中文](README.md) | **English**

For the **Dangbei H3** box (RK3566 / Android 11). Not intended for other models.

## Preinstalled Apps

- CleanYourTV launcher (app library and system status enabled)
- Video 5.8.7 (ARM64)
- BV
- LXTV music (ARM64)
- WebViewTV
- LeanCast (starts on boot)
- TVFileBox (file manager, allowed to install packages)

## Removed Apps

- Dangbei Market
- Dangbei File Manager
- Rocky voice service
- Settings Intelligence
- Contacts Provider
- User Dictionary Provider
- VPN Dialogs
- SecureElement, CompanionDeviceManager, CaptivePortalLogin, PacProcessor, ProxyHandler, StatementService
- Uninstalled on first boot: launcher3.guide, andes, etna.sample, leradwatcher, ota3435, needle, projector.direction, zhushou.os, dbmusic.tab, dbdownloadrefs

## Download and Flash

Download the firmware from [Releases v1.6.0](https://github.com/lifengZero/DBBOXH3-image/releases/tag/v1.6.0):

```text
H3_RK3566_Android11_CleanYourTV_ADB5555.img.gz
```

1. Extract the `.gz` to obtain the complete `.img`. Use the included `.sha256` files to verify your download.
2. Install the Rockchip USB driver and prepare RKDevTool on your computer (`upgrade_tool` works on macOS).
3. Connect the box via USB and enter **Loader mode** using its usual USB flashing procedure.
4. Load the extracted IMG under **Upgrade Firmware** in RKDevTool and start the upgrade.
5. Reboot after the upgrade succeeds. Wait for first-boot app installation, then configure networking and pair the remote.

**Flashing automatically formats the data partition, erasing all user data and Bluetooth pairings; apps are preinstalled again on first boot. Back up your data and keep the original firmware for recovery. Do not flash the `.gz` directly or write this package to the boot partition. Do not disconnect power or USB during flashing.**

## Remote Pairing

**Hold Home and Settings simultaneously. Release both when you hear a beep, then wait for pairing to complete.**

If the remote is not yet usable, connect a USB mouse or keyboard to access Bluetooth settings.

## Note

Wireless ADB remains enabled on port `5555` without authentication. Use only on isolated, trusted networks. Do not expose it to the internet or install untrusted apps.
