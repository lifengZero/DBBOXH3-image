# Dangbei H3 Debloated Firmware

[简体中文](README.md) | **English**

For **Dangbei H3 / H3S boxes. Both models have been successfully flashed and verified; reported working normally.** This firmware is based on the corresponding H3 / RK3566 / Android 11 base firmware and is not intended for other models.

## Removed and Retained

- Removes the stock launcher, media player, screensaver, OTA updater, initial setup wizard, factory testing tools, backup tools, and selected Dangbei services.
- Removes HTML Viewer, Sound Picker, and the spare Pinyin keyboard. Retains Sogou IME, system WebView, Bluetooth, and remote pairing.
- Retains the stock file manager, Settings Intelligence, recent-tasks interface, and Rocky voice service.
- Boots into Aerial, uses a silent boot image, disables window animations, and defaults system backup to off on first startup.

## Preinstalled Apps

**Aerial, BV, Dangbei Market, LXTV (ARM64), Video 5.8.4 (ARM64), and WebViewTV.**

## Download and Flash

Download the firmware from [Releases v1.3.0](https://github.com/lifengZero/DBBOXH3-image/releases/tag/v1.3.0):

```text
H3_RK3566_Android11_Aerial_MAINTENANCE_MARKET_STOCK_BOOT_ADB5555.img.gz
```

1. Extract the `.gz` to obtain the complete `.img`. Use the included `.sha256` files to verify your download.
2. Install the Rockchip USB driver and prepare RKDevTool on a Windows PC.
3. Connect the box via USB and enter **Loader mode** using its usual USB flashing procedure.
4. Load the extracted IMG under **Upgrade Firmware** in RKDevTool and start the upgrade.
5. Reboot after the upgrade succeeds. Wait for first-boot app installation, then configure networking and pair the remote.

**Flashing erases user data and Bluetooth pairings. Back up your data and keep the original firmware for recovery. Do not flash the `.gz` directly or write this package to the boot partition. Do not disconnect power or USB during flashing.**

## Remote Pairing

**Hold Home and Settings simultaneously. Release both when you hear a beep, then wait for pairing to complete.**

If the remote is not yet usable, connect a USB mouse or keyboard to access Bluetooth settings.

## Note

Wireless ADB remains enabled on port `5555` without authentication. Use only on isolated, trusted networks. Do not expose it to the internet or install untrusted apps.
