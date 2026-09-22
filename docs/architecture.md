# LES-NET client architecture

## 0.1 prototype

```text
Windows (.10) ----\
Android (.11) -----+--> public WireGuard relay (.1) <-- outbound WG -- Ubuntu VM (.2) -- home LAN (later)
```

All peers use unique key pairs. The relay routes peer traffic; no direct peer-to-peer transport in v0.1. Windows/Android use official WireGuard clients until our managed applications exist.

## Future client components

- Shared control protocol: versioned HTTPS API, identity, enrollment approval, network membership, ACL snapshots, key rotation and revocation. No private key upload.
- Windows: .NET desktop UI + privileged, narrowly scoped service for tunnel lifecycle.
- Android: Kotlin application using Android VpnService/WireGuard library; no hidden VPN activation.
- RouterOS 7: native WireGuard and generated configurations first; support limited by device/platform facilities.
- OpenWrt: native WireGuard and UCI first; optional management agent later.

Keep data plane (WireGuard traffic) separate from control plane (LES-NET Controller). A relay is a trusted routing point in the prototype, not end-to-end encrypted between clients beyond each peer-to-relay tunnel.
