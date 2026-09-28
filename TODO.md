# TODO: Shared Responsibility Guide (OpenClaw Secure Recovery)

This guide tracks the recovery of your OpenClaw environment. 
- `[USER]` tasks require your physical interaction.
- `[AGENT]` tasks are automated steps I will perform.

## 1. The Shield: Environment Preparation [infrastructure]
| Task | Owner | How & Why |
| :--- | :--- | :--- |
| **Install Tailscale** | `[USER]` | **How**: Download from tailscale.com on PC and Phone. **Why**: Creates a private, invisible tunnel between your devices. |
| **Login to Tailnet** | `[USER]` | **How**: Sign in to the same account on both devices. **Why**: Authenticates your phone as a "trusted node." |
| **Verify Private Mesh** | `[AGENT]` | **How**: Run `tailscale status`. **Why**: Confirm the "Invisibility Cloak" is active. |
| **Install Docker Desktop** | `[USER]` | **How**: Download for Windows and ensure "WSL2 backend" is checked. **Why**: To sandbox the agent so it can't touch your host PC files. |
| **Enable gVisor Isolation** | `[AGENT]` | **How**: Configure Docker runtime. **Why**: Prevents "Vibe Coding" kernel-level escapes. |

## 2. The Phoenix: Secure Installation [backend] [security]
| Task | Owner | How & Why |
| :--- | :--- | :--- |
| **Hardened Deployment** | `[AGENT]` | **How**: Clone v2026.4.2+ and run `docker-setup.sh`. **Why**: Deploys the latest patched version in a sandbox. |
| **Zero Trust Binding** | `[AGENT]` | **How**: Edit `openclaw.json` to `loopback` + `tailscale: serve`. **Why**: Ensures NO ONE on the public internet can even see your gateway. |
| **Enable Safety Gate** | `[AGENT]` | **How**: Set `exec.approvals: true`. **Why**: The hard-coded human-in-the-loop requirement. |
| **Biometric Pairing** | `[USER]` | **How**: Open the Tailscale IP on your phone and scan the fingerprint prompt. **Why**: Binds high-risk commands to your physical presence. |
| **Configure Gemini API Key** | `[AGENT]` | **How**: Securely add the user's Gemini API key to the agent's configuration. **Why**: Allows the agent to use Gemini models. |

## 3. Trust, but Verify: The Stress Test [test]
| Task | Owner | How & Why |
| :--- | :--- | :--- |
| **Forbidden Access Test** | `[AGENT]` | **How**: I'll ask the agent to read `C:\Windows\System32\config\SAM`. **Why**: To prove it is blocked by the gate. |
| **Biometric Denial Test** | `[USER]` | **How**: Click "DENY" on your phone when the prompt appears. **Why**: To confirm the agent cannot bypass a "No." |

## 4. Multimodal Power: Discord & Antigravity [integration]
| Task | Owner | How & Why |
| :--- | :--- | :--- |
| **Antigravity OAuth** | `[USER]` | **How**: Click the Google login link I provide. **Why**: Keyless bridge to your IDX coding workspaces. |
| **Discord Voice/Text** | `[AGENT]` | **How**: Complete bot setup and enable `VoiceGateway`. **Why**: Allows you to talk/type to agents from any location. |
| **Moltbook Register** | `[AGENT]` | **How**: `POST` to moltbook.com API. **Why**: Give your agent a social identity to join "Submolt Games." |

## 5. Final Handover [test]
| Task | Owner | How & Why |
| :--- | :--- | :--- |
| **Voice-to-IDX Test** | `[USER]` | **How**: Join Discord Voice on phone and say "Agent, update the README." **Why**: Proof of full remote coding capability. |
| **Security Audit** | `[AGENT]` | **How**: Run `openclaw security audit`. **Why**: Final confirmation that we are 100% "Clean." |

**Current Status (2026-04-27):**
- Tailscale and Docker are verified.
- OpenClaw is running in Docker.
- Currently paused on securely configuring the Gemini API key and finding the correct path for `exec.approvals`.
