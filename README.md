# AGR Pilot

Control your machine's Claude Code from your phone. The intelligence (Claude Code, MCP servers, skills, file access) runs on your always-on computer; your phone is just a screen. Nothing leaves your private network.

> This repository is the **distribution channel**: it only contains the installer (Releases) and this page. No source code. Development happens in a private repository.

## Download

Latest version: see the **[Releases](../../releases/latest)** tab.

| Platform | File | How |
|---|---|---|
| Windows | `AGR-Pilot-Manager.exe` | Download, double-click. Everything is inside; it installs and updates itself. |

One file: the server is embedded in the app. No need to install Git or Node.

## Requirements

1. **Tailscale** installed and connected to the same account on the host computer and on the phone (https://tailscale.com/download). MagicDNS and HTTPS Certificates enabled once in the Tailscale admin console.
2. **Claude Code** installed and connected on the host (a Claude subscription is required; OAuth sign-in, never an API key).

## How it works

- The host app starts a local server that drives Claude Code and exposes it to your phone over Tailscale, via HTTPS, **only inside your private network**.
- On the phone: open the address (or scan the QR code shown by the host, which contains the address and an access token) and add it to your home screen.
- Updates are automatic: the app downloads the new installer, **verifies its SHA-256 fingerprint and an ECDSA P-256 signature**, then replaces itself.

## Security

- Trust boundary: the **Tailscale** network. The server is never exposed to the public internet.
- **Access token required** by default: the address to scan contains the token; without it, the API refuses everything.
- The binary published here is verified by SHA-256 fingerprint and a signed `version.json` before being run.

## Support

Questions, issues, or security reports: **support@agrlabs.ca**.

## License

MIT. See [LICENSE](LICENSE).
