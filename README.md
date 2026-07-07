# 🦀 LanChat

**Secure. Fast. Pure Rust.**

[![Rust](https://img.shields.io/badge/rust-1.70%2B-orange.svg)](https://www.rust-lang.org/)
[![License](https://img.shields.io/badge/license-MIT%2FApache--2.0-blue.svg)](LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey.svg)]()

---

## 📖 Overview

**LanChat** is a free, open-source LAN messaging tool built entirely in **Rust** — delivering blazing performance and memory safety out of the box. No servers, no cloud, no compromises. Just pure peer-to-peer encrypted communication for your local network.

---

## ✨ Key Features

### 🔒 End-to-End Encryption
All messages and files are encrypted point‑to‑point using modern cryptography. Your data stays private — even on shared networks.

### 📁 File & Folder Sharing
Send files and entire folders instantly with no size limits (except your disk space). Drag, drop, and share.

### 😄 Rich Messaging
Express yourself with **emojis** and formatted text. Keep conversations clear and fun.

### 👥 Group Chats
Create temporary or permanent group conversations. No admin setup — just invite peers on your LAN and start talking.

### ⚡ Pure Rust Performance
Zero runtime overhead, low memory footprint, and full thread safety. Built with Rust's `tokio` and `async` stacks for smooth multitasking.

### 🚀 Zero Configuration
Discover other users automatically via mDNS / local broadcast. No IPs to type, no ports to forward.

---

## 📊 Comparison

| Feature | LanChat | Typical LAN Tools |
|---------|---------|-------------------|
| End-to-end encryption | ✅ | ❌ / Partial |
| Folder sharing | ✅ | ❌ |
| Group chats | ✅ | Limited |
| No server required | ✅ | ❌ |
| Rust‑powered safety | ✅ | ❌ |
| Free & open source | ✅ | ❌ |

---

## 🛠️ Technical Highlights

| Component | Technology |
|-----------|------------|
| **Language** | Rust (stable 1.70+) |
| **Networking** | WebRTC / QUIC over UDP (fallback TCP) |
| **Crypto** | `x25519` + `ChaCha20‑Poly1305` (authenticated encryption) |
| **Discovery** | mDNS (Apple Bonjour / Avahi compatible) |
| **GUI** | Native GUI using `egui` or `iced` — lightweight and responsive |
| **Cross‑platform** | Windows, macOS, Linux (same binary works everywhere) |

---

## 🚀 Getting Started

### Installation

#### Option 1: Download Pre-built Binary
Download the latest release for your OS from the [Releases](https://github.com/yourusername/lanchat/releases) page.

#### Option 2: Build from Source

```bash
# Clone the repository
git clone https://github.com/yourusername/lanchat.git
cd lanchat

# Build in release mode
cargo build --release

# The binary will be at target/release/lanchat