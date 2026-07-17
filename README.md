# LanChat

![License](https://img.shields.io/badge/license-MIT-blue.svg)
![Version](https://img.shields.io/badge/version-0.1.0-blue.svg)
![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20Linux-blue.svg)
![Rust](https://img.shields.io/badge/Rust-1.96-orange.svg)

> Zero-configuration LAN messenger · No internet required · No server required · No registration

LanChat is a **pure LAN instant messaging tool**. No internet, no server, no account needed. It automatically discovers all LanChat users on your local network and supports private chat, group chat, file transfer, and Pro-tier exclusive features.

---

## Features

- **Zero-config** — Launch and go. Auto-discovers all LanChat users on the LAN
- **P2P Encrypted Communication** — X25519 key exchange + AES-256-GCM encryption, messages never touch any server
- **File Transfer** — TCP direct connection, no size limit, any file type, supports batch folder transfer
- **Group Chat** — Create multiple group rooms, supports @mentions and message history
- **Pro Exclusive Features** — Watermark anti-photo, message recall, self-destructing messages, unlimited file size, audit logs, DLP rules, Webhook API
- **Shared Pro License** — One person purchases Pro, every client on the LAN automatically unlocks. No per-machine activation needed
- **Multi-language** — English / 简体中文
- **Zero Telemetry** — Collects no user data, runs fully offline

---

## Supported Platforms

| Platform | Status | Minimum Version |
|----------|--------|-----------------|
| Windows 10/11 (x64) | ✅ Released | Windows 10 1809+ |
| Linux (x64) | 🔜 Planned | kernel 5.4+ |
| macOS | 🔜 Planned | macOS 12+ |

---

## Downloads

Grab the latest release from [Releases](https://github.com/xxx/lanchat/releases).

| Platform | Package Types |
|----------|--------------|
| Windows | `.exe` portable / `.msi` installer (enterprise deployment) |
| Linux | `.tar.gz` portable |

---

## Quick Start

### Windows

```powershell
# Portable (recommended)
Extract lanchat-windows-x64.zip
Double-click lanchat-app.exe

# Enterprise silent install
.\install_windows.ps1 -Silent
```

### Linux

```bash
tar -xzf lanchat-linux-x64.tar.gz
./lanchat-app
```

### Firewall

LanChat uses the following ports. Please ensure your firewall allows them:

| Port | Protocol | Purpose |
|------|----------|---------|
| 2425 | UDP + TCP | User discovery, messaging, file transfer |
| 24251 | UDP | Pro license request / response |
| 9527 | TCP | Web UI (Pro, optional) |

On first launch, LanChat will automatically attempt to configure Windows Firewall or iptables.

---

## Free vs. Pro

| Feature | Free | Pro |
|---------|------|-----|
| Private messaging | ✅ | ✅ |
| Group chat (up to 20 members) | ✅ | ✅ |
| File transfer | ✅ (max 100MB) | ✅ (unlimited) |
| Auto user discovery | ✅ | ✅ |
| **Watermark overlay (anti-screenshot leak)** | ❌ | ✅ |
| **Message recall** | ❌ | ✅ |
| **Self-destructing messages** | ❌ | ✅ |
| **Audit logs** | ❌ | ✅ |
| **DLP rules** | ❌ | ✅ |
| **Webhook API** | ❌ | ✅ |
| **Web UI (browser access)** | ❌ | ✅ |
| **Priority support** | ❌ | ✅ |

### Pricing

| Plan | Price |
|------|-------|
| Free | Free |
| Pro (monthly) | $4.99 / month |
| Pro (annual) | $39.99 / year |
| Pro (lifetime) | $99.99 one-time (all future updates included) |
| Team (10 seats, annual) | $249.99 / year |

> One person purchases Pro, every client on the LAN auto-unlocks.

---

## Pro License Activation

```bash
# 1. Get machine code
Launch LanChat → File menu → 🔑 Activate Pro → Copy machine code

# 2. Provide the machine code to your vendor to get license.key

# 3. Activate
Method A: Place license.key in the same folder as lanchat-app.exe → Restart
Method B: LanChat → File menu → 🔑 Activate Pro → Paste license content → Activate
```

---

## FAQ

**Q: I can't see other users?**
> Make sure all devices are on the same LAN (first 3 octets of IP match). Check if your firewall blocks UDP/TCP port 2425. For VMs, use bridged networking mode.

**Q: Linux client can't get Pro license?**
> Make sure firewall allows UDP port 24251, or run: `sudo iptables -I INPUT -p udp --dport 24251 -j ACCEPT`

**Q: What are the file transfer speeds?**
> Limited by your LAN bandwidth. ~100 MB/s on Gigabit Ethernet, ~10 MB/s on 100Mbps.

**Q: Does it support offline messages?**
> Not in the current version. Messages are delivered in real-time when the recipient is online.

**Q: Where are message logs stored?**
> Local SQLite database at: `%APPDATA%/LanChat/` (Windows) or `~/.local/share/LanChat/` (Linux).

---

## Security

- Messages and files protected with **X25519 + AES-256-GCM** end-to-end encryption
- Licenses verified with **RSA-2048 + SHA-256** signatures
- License broadcast includes clock skew check + TTL expiration
- Pro license distribution uses **SHA-256** integrity verification
- **Zero telemetry, zero data upload**

---

## Enterprise Deployment

- **Air-gapped networks**: LanChat runs fully offline, no internet required
- **Silent install**: MSI supports `/quiet` flag for silent installation via Group Policy
- **IT management**: Auto-update can be disabled via config file
- **Audit logs**: Pro tier provides complete communication audit trail

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| Language | Rust 1.96 |
| GUI Framework | eframe 0.31 / egui 0.31 |
| Window Management | winit 0.30 |
| Serialization | serde + serde_json |
| Async Runtime | tokio |
| Storage | SQLite (bundled rusqlite) |
| Encryption | X25519, AES-256-GCM, RSA-2048 |
| Build | cargo |

---

## Project Structure

```
lanchat/
├── crates/
│   ├── lanchat-app/         # GUI application entry point
│   ├── lanchat-core/        # Core business logic
│   ├── lanchat-network/     # Network layer (UDP discovery / TCP transfer)
│   ├── lanchat-protocol/    # Message protocol definitions
│   ├── lanchat-storage/     # SQLite storage layer
│   └── license-cli/         # License CLI tool
├── README.md
├── LICENSE
├── README_BEFORE_INSTALL.md
├── README_AFTER_INSTALL.md
├── EULA.txt
├── commercial-features-roadmap.md
├── platform-audit.md
└── release-promotion-plan.md
```

---

## License

This project is open source under the [MIT License](LICENSE).

---

*Built with Rust · Zero telemetry · Zero registration*
