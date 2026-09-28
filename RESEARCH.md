# Research: Secure OpenClaw Remote Setup (Updated June 2026)

This document outlines the findings for setting up OpenClaw securely to bridge with Google's Antigravity (Project IDX) and Moltbook, accessible via mobile.

## 1. Security Analysis (The "Cleanse")
- **Flashing Window Source**: Identified as a scheduled task `\OpenClaw Gateway` executing `C:\Users\transmacsual\.openclaw\gateway.cmd` at logon.
- **Action Taken**: 
    - Deleted the scheduled task and terminated all `node.exe` processes.
    - Wiped all `.openclaw` and global NPM artifacts.

## 2. Updated Vulnerability Context
- **CVE-2026-33579 (Agentic Consent Bypass)**: High-severity flaw (CVSS 8.4) allowing attackers to bypass `exec.approvals` via privilege escalation in the pairing path.
- **Requirement**: Must use OpenClaw **v2026.4.2** or later.
- **Passkey Protection**: New `stepUpAuth` feature allows mapping sensitive tool calls to cryptographic passkeys (Yubikey/Biometrics).

## 3. Secure Setup Strategy (Zero Trust)
- **Isolation**: Deploy via Docker using **gVisor** (if supported by host) for stronger kernel isolation.
- **Networking (Tailscale)**: Set `gateway.tailscale.mode: "serve"`. This ensures the gateway is only visible to your private "Tailnet" devices.
- **Mobile Access**:
    - **OpenACP Bridge**: Integrates OpenClaw with Telegram/Discord for voice/chat control from mobile.
    - **IDX Manager View**: Use the `openclaw-antigravity-auth` mobile-optimized dashboard.

## 4. Integration Details
- **Antigravity (Project IDX)**: Keyless bridge via `openclaw-antigravity-auth` plugin.
- **Moltbook**: Use `moltbook-social` skill. Agents participate in "Submolt Games" to earn reputation/karma.

## 5. Security Checklist
- [ ] Verify OpenClaw version >= 2026.4.2.
- [ ] Configure `exec.approvals: true`.
- [ ] Implement `stepUpAuth` for passkey-required commands.
- [ ] Disable Bonjour/mDNS (`OPENCLAW_DISABLE_BONJOUR=1`) in Docker.
