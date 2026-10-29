# Dangbei H3 Debloated Firmware

[简体中文](README.md) | **English**

For **Dangbei H3 / RK3566 / the corresponding Android 11 base firmware** only. Not compatible with H3S or other models.

## Features

- Removes the stock launcher, media player, screensaver, OTA updater, factory testing tools, backup tools, and selected preinstalled apps.
- Uses Aerial as the default launcher and removes the launcher allowlist, allowing other compatible launchers.
- Automatically grants root access without confirmation. Magisk/Kitsune is retained, with its manager disabled by default.
- Keeps wireless ADB enabled on port `5555`, without authentication.
- Precompiles the framework and Aerial, replaces the boot animation with a silent one, and optimizes startup and repeated Home button activation.
- Retains Bluetooth remote pairing, the initial setup wizard, and system WebView.

Preinstalled apps: **Aerial, BV, Dangbei Market, LXTV (ARM64), OK Video (OK 影视), and WebViewTV**.

## Download and Verification

The firmware is distributed through [GitHub Releases](https://github.com/lifengZero/DBBOXH3-image/releases/tag/v1.0.0) because of its size. It is not stored in the Git repository.

1. Download `H3_RK3566_Android11_Aerial_AOT_AUTO_ROOT_ADB5555.img.gz` from the release.
2. Extract it using 7-Zip or another gzip-compatible tool to obtain the complete `.img` file. Do not flash the `.gz` file directly.
3. Verify the SHA-256 of the extracted IMG against the matching `.img.sha256` file in the repository or release. The release also includes an `.img.gz.sha256` file for verifying the compressed archive.

SHA-256 of the extracted IMG:

```text
f996379a140d8a2b6e3c3b5e9b10bd80d1f18c7a9cf21dd3674470712f181f3e
```

## Flashing Instructions

Use the complete firmware image:

```text
H3_RK3566_Android11_Aerial_AOT_AUTO_ROOT_ADB5555.img
```

1. Prepare the Rockchip USB driver and RKDevTool on a Windows PC.
2. Connect the device via USB and enter **Loader mode** using the device's usual USB flashing procedure.
3. Confirm that RKDevTool detects the device, load the IMG above under **Upgrade Firmware**, and start the upgrade.
4. Wait for the upgrade to succeed, then reboot. Do not disconnect power or USB during flashing.
5. On first boot, complete Bluetooth remote pairing and network setup, then wait for app installation to finish before entering Aerial.

**This is a complete firmware upgrade package. Do not flash it as a boot partition image. No separate boot image or manual root authorization is required.**

## Wireless ADB

Replace the example IP address with your device's actual IP address:

```bash
adb connect 192.168.1.100:5555
adb shell su -c id
```

If root is working, the output includes `uid=0(root)`.

## Important Notes

- **All apps requesting root access are automatically approved, and wireless ADB has no authentication. Use only on trusted networks. Do not expose the device to the public internet or install untrusted apps.**
- Initial setup and app installation are still required on first boot. Some apps may need compilation; please be patient.
- Aerial can be updated by installing a newer APK with the same package name and signing certificate that is compatible with Android 11. Reflashing is not required.
