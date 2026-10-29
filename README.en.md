# Dangbei H3 Debloated Firmware (Stock Boot)

[简体中文](README.md) | **English**

For **Dangbei H3 / RK3566 / the corresponding Android 11 base firmware** only. Not compatible with H3S or other models.

## Features

- Removes the stock launcher, media player, screensaver, OTA updater, factory testing tools, backup tools, and selected preinstalled apps.
- Uses Aerial as the default launcher and removes the launcher allowlist, allowing other compatible launchers.
- Uses the unmodified stock boot image.
- Keeps wireless ADB enabled on port `5555`, without authentication.
- Uses a static, silent boot image, disables window animations, and retains protection against redundant Home button activation.
- Removes the initial setup wizard and enters Aerial after initialization. Configure networking and pair the remote manually.
- Removes HTML Viewer, Sound Picker, and the spare Pinyin keyboard. Sogou IME and system WebView are retained.
- Disables system backup on the first successful startup, retrying failures without overriding later user changes.
- Fixes the Home-triggered system crash caused by the removed OEM policy provider: skips background cleanup when either required list is unavailable, while keeping `DBdownloadrefs` removed.
- Fixes the reproduced Bluetooth playback-queue null crash by returning an empty list only to the Bluetooth process. The original signed Bluetooth APK and HID/audio profiles are retained.

Retained as requested: **the stock file manager, Settings Intelligence, the recent-tasks interface, and the Rocky voice service**.

Preinstalled apps: **Aerial, BV, Dangbei Market, LXTV (ARM64), Video 5.8.4 (ARM64, `leanback-arm64_v8a.apk`), and WebViewTV**. The new Video APK replaces OK Video 5.1.6.

## Download and Verification

The firmware is available from [GitHub Releases v1.2.0](https://github.com/lifengZero/DBBOXH3-image/releases/tag/v1.2.0). Large firmware images are not stored in Git history. Version v1.1.0 has a known Home-triggered crash and should no longer be used.

1. Download `H3_RK3566_Android11_Aerial_HOME_BT_FIX_STOCK_BOOT_ADB5555.img.gz`.
2. Extract it with 7-Zip or another gzip-compatible tool to obtain the complete `.img` below. Do not flash the `.gz` directly.
3. Verify the extracted IMG against the matching `.img.sha256` file. A separate `.img.gz.sha256` verifies the compressed archive.

Extracted firmware file:

```text
H3_RK3566_Android11_Aerial_HOME_BT_FIX_STOCK_BOOT_ADB5555.img
```

IMG SHA-256:

```text
f11b3191ccbd2738f64f96209750fd777be4694a072aef545ea76bdbba9183f0
```

## Flashing Instructions

Use the complete firmware image:

```text
H3_RK3566_Android11_Aerial_HOME_BT_FIX_STOCK_BOOT_ADB5555.img
```

1. Prepare the Rockchip USB driver and RKDevTool on a Windows PC.
2. Connect the device via USB and enter **Loader mode** using the device's usual USB flashing procedure.
3. Confirm that RKDevTool detects the device, load the IMG above under **Upgrade Firmware**, and start the upgrade.
4. Wait for the upgrade to succeed, then reboot. Do not disconnect power or USB during flashing.
5. On first boot, wait for initialization and app installation to finish. The device enters Aerial directly; configure networking and pair the remote afterward.

**This is a complete firmware upgrade package. Do not flash it as a boot partition image or flash a separate boot image. Flashing erases user data and Bluetooth pairings. Back up your data and keep the original firmware for recovery.**

## Remote Pairing

**Hold the remote's Home and Settings buttons simultaneously. Release both when you hear a beep, then wait for pairing to complete.**

There is no initial setup wizard. If the remote is not yet usable, connect a USB mouse or keyboard to access Bluetooth settings.

## Wireless ADB

Replace the example IP address with your device's actual IP address:

```bash
adb connect 192.168.1.100:5555
adb shell bmgr enabled
```

After initial setup, backup should report `Backup Manager currently disabled`.

## Important Notes

- **Wireless ADB has no authentication. Use only on isolated, trusted networks. Do not expose it to the internet or install untrusted apps.**
- Removed OEM services may affect projector settings, hardware integrations, and remote firmware updates. Retaining related apps does not guarantee every OEM feature works.
- Initial setup and app installation are still required on first boot. Some apps may need compilation; please be patient.
- This version passed 25 regression tests plus filesystem and firmware integrity checks. The original Bluetooth APK and all 43 system APKs are byte-identical to the preceding internal HOMEFIX build; the fixes are implemented in the system framework.
- The same stock-boot base previously completed a software reboot in about 17.2 seconds. **This combined Home/Bluetooth-fix image has not been flashed and tested; long-term remote stability remains unverified.** First-boot and cold-start times are not guaranteed.
- Aerial can be updated by installing a newer APK with the same package name and signing certificate that is compatible with Android 11. Reflashing is not required.
