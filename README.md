# LocalPTT V_0_1

LocalPTT is a native Android LAN push-to-talk radio. One Android device creates a local room and other Android devices on the same reachable Wi-Fi, hotspot, router, or private network discover and join it.

The app uses no cloud account, Firebase project, hosted WebSocket, Node server, or PC server. The host Android device coordinates room membership and forwards UDP Opus voice packets.

## Supported Android Versions

- Minimum SDK: Android 8.0 / API 26
- Target SDK: API 36 in this build environment
- Version: `0.1.0`, version code `1`

## Basic Use

1. Install `dist/LocalPTT_V_0_1.apk` on at least two Android devices.
2. Connect both devices to the same reachable LAN or Android hotspot.
3. Open LocalPTT and grant microphone, notification, and local network permissions when Android asks.
4. On one device, choose Create Room and share the displayed PIN.
5. On another device, choose Join Room, select the discovered room or enter the host IP manually, then enter the PIN.
6. Hold the PTT button to speak. Release to stop transmitting.

## Build

Run:

```powershell
.\build_apk.ps1
```

The script runs clean, unit tests, lint, debug APK assembly, signature verification, APK metadata inspection, and SHA-256 generation.

## Permissions

LocalPTT requests microphone access only for push-to-talk transmission, notification access for foreground Radio Mode status, LAN/network access for local sockets and NSD discovery, multicast control for mDNS reliability, wake lock for active sessions, and overlay permission only if the floating PTT control is enabled.

## Troubleshooting

If discovery fails, use manual host IP and control port. Some routers and hotspots isolate clients. Some Android manufacturers terminate background services aggressively; keep Radio Mode visible and review battery settings if sessions are killed.
