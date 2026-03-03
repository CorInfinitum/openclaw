# OpenClaw Studio — Assessment and CorCompass Integration Guide

**Document ID:** REF-STUDIO-INTEGRATION
**Version:** 1.3.0 — March 1, 2026
**Classification:** Internal — Operator Use Only
**Series:** CorCompass Protected Series, Cor Infinitum LLC

---

## What Is OpenClaw Studio?

OpenClaw Studio (`grp06/openclaw-studio`) is an open-source, self-hosted web dashboard for managing OpenClaw Gateway deployments. It provides a browser-based UI that connects to a running Gateway instance via WebSocket, allowing the user to chat with agents, manage workspace files, configure capabilities (exec, web, file tools), set up automations (cron schedules), and approve exec commands — all without touching the command line.

As of March 2026, the repository has **1.2k stars and 169 forks**, indicating strong community adoption. It is actively maintained with 671 commits and 49 branches, with the most recent commit dated February 27, 2026.

---

## Architecture Summary

Studio is a **Next.js App Router** application with a custom Node.js server that acts as a WebSocket proxy between the browser and the upstream OpenClaw Gateway. The two-hop architecture is important to understand:

```
Browser → Studio (port 3000) → Gateway (port 18789)
```

Studio does not store agent data, sessions, or workspace files. It is a pure UI layer. The Gateway remains the single source of truth for all agent state. This means Studio can be deployed, updated, or replaced without affecting the agents themselves.

| Component | Role |
|---|---|
| Browser | Renders the UI; connects to Studio via HTTP + WebSocket |
| Studio server | Proxies WebSocket frames; stores only UI settings (gateway URL, token) |
| Gateway | Runs agents, manages workspace files, enforces permissions |

---

## Feature Inventory

| Feature | What It Does | Client-Facing Value |
|---|---|---|
| **Agent fleet view** | Lists all agents with status badges (connected, heartbeat, idle) | Client sees their agents at a glance |
| **Chat interface** | Full conversation UI with tool call display and thinking traces | Primary interaction surface |
| **Personality editor** | Edit SOUL.md, AGENTS.md, USER.md, IDENTITY.md in-browser | Client can update their own USER.md |
| **Capabilities panel** | Toggle exec (off/ask/auto), web access, file tools | Client controls agent permissions |
| **Automations tab** | Create and manage cron schedules with template → task → schedule flow | Client sets up recurring tasks |
| **Exec approval cards** | In-chat cards for approving/denying pending exec commands | Client maintains oversight of agent actions |
| **Session management** | Start new sessions, view session history | Client resets context when needed |
| **Workspace viewer** | Open workspace folder, view and edit agent files | Advanced users can inspect agent memory |

---

## Recommendation: Yes — With a Specific Deployment Model

**OpenClaw Studio is recommended for CorCompass Harbor Build client deployments.** The rationale follows.

### What Studio Does Well

Studio solves the single biggest friction point in client handoffs: the command line. Without Studio, a client who wants to chat with their agent, update their USER.md, or add a cron schedule must either use a terminal or wait for the CorCompass operator to make changes. Studio eliminates that dependency entirely.

The chat interface is polished and production-quality. It displays tool calls and thinking traces in a way that builds client trust — they can see the agent reasoning, not just the output. The exec approval flow is particularly valuable: rather than giving clients unrestricted exec access, Studio surfaces pending commands as approval cards, keeping the client in control without requiring technical knowledge.

The workspace file editor (Personality tab) is directly aligned with the CorCompass workspace model. Clients can update their USER.md — the file that tells the agent who they are and what they are working on — without any operator involvement. This is the correct level of client autonomy: they own their context, but they cannot modify the agent's core identity or operating instructions.

### What Studio Does Not Do

Studio is explicitly **not designed for multi-user concurrency**. The ARCHITECTURE.md states this directly: "Non-goals: Multi-tenant or multi-user concurrency." This means Studio is appropriate as a single-user cockpit for each client's own agents — not as a shared dashboard where multiple clients log in to different accounts.

Studio also does not provide analytics, billing, or CRM features. Those remain in the CorCompass Operator HQ.

### The Correct Deployment Model for CorCompass

Each Harbor Build client receives their own Studio instance, deployed on their own VPS or the CorCompass-managed VPS, connected to their own Gateway. The recommended setup is **Scenario C** from the Studio README: Studio in the cloud, Gateway in the cloud, both on the same VPS, with Studio exposed over Tailscale HTTPS.

```
Client's VPS
├── OpenClaw Gateway (port 18789, localhost only)
└── OpenClaw Studio (port 3000, exposed via Tailscale)

Client access: https://[client-name].ts.net (Tailscale)
```

This architecture means:
- The client's Gateway is never exposed to the public internet
- Studio is accessible from any device the client has added to their Tailscale network
- The CorCompass operator can also access the same Studio instance for maintenance
- `STUDIO_ACCESS_TOKEN` is required since Studio is bound to a non-loopback address

---

## Integration Into the CorCompass Build-and-Ship Process

Studio is added to the SOP as **Phase 6 — Client Handoff**, which runs after the five-phase build protocol.

### Phase 6 — Client Handoff (30–45 min)

**Step 1 — Install Studio on the client's VPS**

```bash
npx -y openclaw-studio@latest
cd openclaw-studio
npm run dev
```

**Step 2 — Configure Tailscale access**

On the VPS:
```bash
tailscale serve --yes --bg --https 443 http://127.0.0.1:3000
```

**Step 3 — Set the Studio access token**

```bash
export STUDIO_ACCESS_TOKEN=[generate a strong random token]
```

Store this token in the client's Harbor Build handoff document.

**Step 4 — Connect Studio to Gateway**

In Studio settings:
- Upstream URL: `ws://localhost:18789`
- Upstream Token: `openclaw config get gateway.auth.token`

**Step 5 — Configure client-visible agents**

For each agent the client will interact with:
- Verify capabilities are set correctly (exec: Ask, not Auto, for client-facing agents)
- Confirm USER.md is populated with the client's profile
- Run one test conversation in Studio to confirm the agent responds correctly

**Step 6 — Client onboarding**

Deliver the client:
1. Their Tailscale invite link
2. Their Studio URL (`https://[client-name].ts.net`)
3. Their Studio access token (first login only)
4. The Studio Quick Start guide (see below)

---

## Studio Quick Start Guide for Clients

*This section is written for the client, not the operator. Copy and send as part of the Harbor Build handoff package.*

### Accessing Your Agents

1. Accept the Tailscale invite and install Tailscale on your device.
2. Navigate to `https://[your-studio-url].ts.net` in your browser.
3. Enter your access token when prompted. You will only need to do this once per device.
4. Your agents appear in the left sidebar. Click any agent to open the chat.

### Chatting With Your Agent

Select an agent and type in the message box. Your agent will respond with reasoning visible in the thinking trace above the reply. If your agent needs to run a command, an approval card will appear — review it and click Approve or Deny.

To start a fresh conversation, click **New Session** in the chat header. This clears the visible transcript but does not delete your agent's long-term memory.

### Updating Your Profile (USER.md)

Click the settings cog on any agent → **Personality** tab → **About You**. This is your profile file. Update it whenever your focus, priorities, or context changes. Your agent reads this file before every response.

### Setting Up Automations

Click the settings cog → **Automations** tab → **New Schedule**. Choose a template (daily report, weekly summary, etc.), describe the task, set the schedule, and review. Your agent will run this task automatically at the scheduled time and send you the result.

### What Your Agent Can and Cannot Do

Your agent's capabilities are shown in the **Capabilities** tab:
- **Run commands**: Set to Ask — your agent will request approval before running any command.
- **Web access**: On — your agent can browse the web.
- **File tools**: On — your agent can read and write files in its workspace.

Do not change these settings without consulting your CorCompass operator.

---

## Security Notes for Operators

| Risk | Mitigation |
|---|---|
| Studio exposed to public internet | Use Tailscale or SSH tunnel; never bind to `0.0.0.0` without `STUDIO_ACCESS_TOKEN` |
| Client modifies agent operating instructions | AGENTS.md is not exposed in the Personality tab by default; confirm this in the Studio UI before handoff |
| Client sets exec mode to Auto | Review capabilities settings during onboarding; set to Ask for all client-facing agents |
| Multiple clients on one Studio instance | Do not do this. Studio is single-user. Each client gets their own instance. |

---

## Comparison: Studio vs. CorCompass Operator HQ

These two systems serve different audiences and should not be confused.

| Dimension | OpenClaw Studio | CorCompass Operator HQ |
|---|---|---|
| **Primary user** | The client | The CorCompass operator |
| **Purpose** | Chat with and control deployed agents | Build, train, and manage the agent system |
| **Deployment** | Client's VPS | Manus-hosted (or self-hosted) |
| **Agent access** | Client's agents only | All agents across all clients |
| **Training files** | Not visible | Full library with viewer |
| **CRM** | Not present | Full CRM with pipeline |
| **SOP** | Not present | Full SOP with curriculum |
| **Multi-client** | No | Yes |

---

## Keywords

`openclaw-studio` `client-handoff` `harbor-build` `systems-cockpit` `gateway-dashboard` `tailscale` `studio-access-token` `user-md` `exec-approval` `automations` `cron` `personality-editor` `workspace-viewer` `vps-deployment` `client-onboarding` `single-user` `websocket-proxy` `next-js` `phase-6`
