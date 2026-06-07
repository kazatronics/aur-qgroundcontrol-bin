# qgroundcontrol-bin

AUR package that installs [QGroundControl](https://qgroundcontrol.com/) from the
official upstream AppImage release, extracted into a normal system package.

## What's included

The full AppDir from `QGroundControl-x86_64.AppImage`, installed to
`/opt/qgroundcontrol/`:

- **Application:** the `QGroundControl` binary plus its bundled Qt 6 runtime,
  QML modules, and GStreamer plugins
- **Launcher:** `/usr/bin/qgroundcontrol` (symlink to the upstream `AppRun`,
  which sets up the bundled library paths)
- **Desktop integration:** `.desktop` entry, hicolor icons (16–256 px), and
  AppStream metadata installed to the usual `/usr/share` locations

Because the AppImage is extracted at build time, no FUSE/AppImage runtime is
needed and the app integrates like any other package.

## Install

```bash
yay -S qgroundcontrol-bin
```

Or manually:

```bash
git clone https://aur.archlinux.org/qgroundcontrol-bin.git
cd qgroundcontrol-bin
makepkg -si
```

## Serial port access

To talk to a flight controller over USB/serial, add yourself to the `uucp`
group:

```bash
sudo usermod -aG uucp $USER
```

If ModemManager is installed it can grab serial ports; consider removing it or
masking its service.

## Automatic updates

A GitHub Actions workflow checks daily for new QGroundControl releases and
pushes updates to the AUR automatically.

## License

The packaging files in this repository are provided under
[Apache-2.0](LICENSE.md). QGroundControl itself is dual-licensed under
Apache-2.0 and GPL-3.0 by the [upstream project](https://github.com/mavlink/qgroundcontrol).
