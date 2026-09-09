# PeerPath

Safe **video + text** random connections with real WebRTC, accounts, and matchmaking.

## IMPORTANT – How to run (required)

Camera, video, and matching **only work** when you start the server:

```bash
cd peerpath
node server.js
```

Then open in your browser:

**http://localhost:3000**

Do **not** open the HTML files directly (file://) — camera and WebSocket will fail.

## Features
- **Sign Up / Sign In** accounts (stored in your browser)
- Real WebRTC video + audio (STUN via Google)
- Text chat via DataChannel
- Random matchmaking (text or video queues)
- Friend list, report system, content filter
- 18+ confirmation on signup

## How to test video + chat

1. Run `node server.js`
2. Open http://localhost:3000 in **Tab 1**
3. Sign up as User A
4. Open http://localhost:3000 in **Tab 2** (or another browser)
5. Sign up as User B
6. Both click **Video + Text** (allow camera when asked)
7. You will be matched — local + remote video and chat work

## Troubleshooting camera

- Allow camera & microphone when the browser prompts
- Use Chrome or Edge on desktop for best results
- If camera is used by Zoom/Teams, close those apps first
- Must be on http://localhost:3000 (not file://)

## Architecture

```
Browser A  ←── WebSocket ──→  server.js  ←── WebSocket ──→  Browser B
     │                                                      │
     └──────────── RTCPeerConnection (media + chat) ────────┘
```
