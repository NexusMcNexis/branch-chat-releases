# Branch Chat releases

**Branch Chat** is a small, private, end-to-end encrypted chat for families, friends and groups.
Messages, photos and files are encrypted on your device; the server only stores ciphertext.
Start at **https://branchchat.app**, or run your own server with the packages below.

This repository only hosts release downloads. Get the newest version at
**https://github.com/NexusMcNexis/branch-chat-releases/releases/latest**.

## Downloads (26.10.0)

| Platform | File | Notes |
|---|---|---|
| Linux x86_64 | `BranchChat-26.10.0-x86_64.AppImage` | Any distro: `chmod +x` and run (needs FUSE 2, or use `--appimage-extract-and-run`) |
| Linux arm64 | `BranchChat-26.10.0-arm64.AppImage` | Raspberry Pi 4/5 (64-bit OS) and other arm64 desktops |
| Debian / Ubuntu | `BranchChat-26.10.0-amd64.deb` | `sudo apt install ./BranchChat-26.10.0-amd64.deb` |
| Fedora / openSUSE | `BranchChat-26.10.0-x86_64.rpm` | `sudo dnf install ./BranchChat-26.10.0-x86_64.rpm` |
| Linux (portable) | `BranchChat-26.10.0-x64.tar.gz`, `BranchChat-26.10.0-arm64.tar.gz` | Extract anywhere and run `./branch-chat` |
| Server (native) | `branch-chat-server-26.10.0-install.tar.gz` | Debian, Ubuntu, Raspberry Pi OS (amd64 and arm64): `sudo ./server/install.sh` |
| Server (Docker) | `branch-chat-server-26.10.0-docker-compose.tar.gz` | Docker Compose, amd64 and arm64 |
| Android | coming soon | |
| iPhone / iPad | coming soon | |
| Windows / macOS | coming soon | Use https://branchchat.app in your browser for now |

Every release includes `SHA256SUMS-<version>.txt`. Check a download with `sha256sum -c SHA256SUMS-26.10.0.txt --ignore-missing`.

## Desktop app
Opens **branchchat.app** first. Choose *Use my own server* to connect to any Branch Chat server, and add or switch
servers later in *Branch Chat → Servers…* (Ctrl+Shift+S). Requirements: 64-bit Linux with a desktop environment
(GTK 3, NSS, libnotify are standard on most distributions).

## Run your own server
Requirements: a 64-bit Linux machine (Raspberry Pi 4/5 with 2 GB+, any small PC, VM or Proxmox guest), Python 3.9+ for
the native install or Docker, and a domain on Cloudflare (free plan) for access from anywhere, or a home network.

```bash
tar xzf branch-chat-server-26.10.0-install.tar.gz
cd branch-chat-server-26.10.0
sudo ./server/install.sh        # wizard: native or Docker, your group's name, admin account, access, email, backups
```

Docker Compose:
```bash
tar xzf branch-chat-server-26.10.0-docker-compose.tar.gz
cd branch-chat-server-26.10.0-docker/server
cp config.env.example config.env && chmod 600 config.env   # set BC_PUBLIC_URL, BC_INSTANCE_NAME, BC_OWNER, BC_MAIL_FROM
mkdir -p data && sudo chown 10001:10001 data && chmod 700 data
docker compose build && docker compose up -d
```
Full guide: `docs/self-hosting.md` inside the package, plus `docs/server/raspberry-pi.md` and `docs/server/proxmox.md`.

## Versions
One version number for everything: `YY.MM.PATCH` (26.10 = October 2026). Apps and servers work together when the
first two numbers match. Servers report theirs at `/api/version`.

## License
All rights reserved. A license has not been chosen yet. Until one is published here, you may download and run these
releases for your own use, but no other rights are granted.

© 2026 BranchChat. Branch Chat™ is a trademark of BranchChat.
