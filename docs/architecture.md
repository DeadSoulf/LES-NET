# LES-NET client architecture

```text
Windows (.10) / Android (.11)
         |
Internet -> HOME public IPv4 : UDP 51820
         |
  [Home router: optional UDP forwarding]
         |
  [Ubuntu VM inside Proxmox: WireGuard SERVER, 10.77.0.1]
         |
  [Home LAN 192.168.1.0/24: opt-in routing]
```

**No third-party VPS or external relay** in this deployment. The home VM is the VPN endpoint and future controller. The v0.1 prototype is routed IPv4 over standard WireGuard, not a ZeroTier-like L2 or automated P2P mesh. Full IPv4 exit through the **home internet** needs explicit server forwarding/NAT, and IPv6/DNS leak protection is not yet implemented.

Future clients: Windows .NET desktop UI + privileged service, Android Kotlin/VpnService, RouterOS 7 native WireGuard profiles and OpenWrt native WireGuard/UCI. Control API and strong device enrollment will be specified in server repo; no private client key upload.
