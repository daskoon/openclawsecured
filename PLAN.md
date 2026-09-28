# Plan: Secure OpenClaw Remote Installation (June 2026 Edition)

This plan details the steps to deploy OpenClaw in a hardened gVisor-backed Docker environment with Zero Trust networking and biometric protection.

## 1. Environment Preparation (The Foundation)
- [ ] **Tailscale Verification**:
    - Ensure Tailscale is installed on both PC and Phone.
    - Verify both devices are visible in the private Tailnet.
- [ ] **Docker & gVisor Setup**:
    - Re-install Docker Desktop if missing.
    - Enable gVisor runtime (if supported) to prevent "Vibe Coding" kernel escapes.

## 2. Hardened "Phoenix" Installation
- [ ] **Clean Deployment**: 
    - Clone OpenClaw v2026.4.2+ into a fresh directory.
    - Run `./scripts/docker/setup.sh` and select "Hardened Mode".
- [ ] **Zero Trust Configuration**:
    - Edit `openclaw.json` to bind to `loopback` only.
    - Set `gateway.tailscale.mode` to `"serve"` for private device-to-device access.
- [ ] **Safety Gates**:
    - Enable `exec.approvals: true`.
    - Configure `stepUpAuth` to require **Phone Biometrics (FaceID/Fingerprint)** for high-risk commands.

## 3. Trust, but Verify (The Stress Test)
- [ ] **Gate Check**: Ask the agent to read a sensitive file outside its workspace.
- [ ] **Passkey Challenge**: Verify that a cryptographic challenge appears on your phone browser before the agent can even *ask* for approval.
- [ ] **Denial Logic**: Deny the request and verify the agent is physically blocked from retrying autonomously.

## 4. Remote Capabilities & Social Identity
- [ ] **Antigravity Bridge**: 
    - Install `openclaw-antigravity-auth`.
    - Link Google Account to bridge Project IDX workspaces via the mobile "Manager View".
- [ ] **Discord Multimodal Bridge**:
    - Complete the existing **Discord setup** (halfway done).
    - Configure for both **Voice and Text** interaction (Voice channel presence + Chat commands).
- [ ] **Moltbook Citizenship**:
    - Register agent at `moltbook.com/api/v1`.
    - Apply the `moltbook-social` skill and join "Submolt Games" to build karma.

## 5. Mobile Handover & Final Audit
- [ ] **Private Link**: Connect phone to the PC via the Tailscale IP.
- [ ] **Live Test**: From your phone, use Discord (Voice or Text) to trigger a code change in Antigravity.
- [ ] **Security Audit**: Run `openclaw security audit` to confirm no new vulnerabilities were introduced.
