# PeerPath

Safe **video + text** random connections across regions and generations — with real WebRTC.

## Features
- Real WebRTC peer-to-peer video & audio
- WebSocket signaling + matchmaking server (zero npm dependencies)
- Text chat via RTCDataChannel (with signaling fallback)
- Google STUN servers for NAT traversal
- Friend requests, report system, content filter, 18+ gate
- Professional responsive UI

## How to run

```bash
cd peerpath
node server.js
```

Then open **http://localhost:3000** in **two different browser tabs** (or two devices on the same network).

1. Confirm age (18+)
2. Click **Text Only** or **Video + Text**
3. Allow camera/mic when asked
4. When a second person also clicks Find, you get matched
5. Chat, video, mute, report, friend, or Next

## Architecture

```
Browser A  ←── WebSocket signaling ──→  Node server  ←── WebSocket ──→  Browser B
     │                                        │
     └──── RTCPeerConnection (media + data) ──┘
              (STUN: stun.l.google.com)
```

- **server.js** – pure Node.js HTTP static file server + minimal WebSocket matchmaking & SDP/ICE relay
- **js/chat.js** – full WebRTC client (offer/answer, ICE, DataChannel, getUserMedia)

## Production notes
For public internet use, add a TURN server (e.g. coturn) and host the signaling server with HTTPS/WSS.
