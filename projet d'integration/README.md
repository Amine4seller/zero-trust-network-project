# Zero Trust Network Project

![Cloudflare](https://img.shields.io/badge/Cloudflare-Tunnel-orange)
![Tailscale](https://img.shields.io/badge/Tailscale-VPN-blue)
![Python](https://img.shields.io/badge/Python-3.x-green)

## Objective
This project shows two ways to access a local server securely without opening ports: **Cloudflare Tunnel** and **Tailscale**.

---

## Local Server
A simple server was created using Python on port 8000. It works only on localhost by default.
```bash
python3 -m http.server 8000
```

---

## Cloudflare Tunnel
Cloudflare was used to expose the local server to the internet. It generates a public URL that anyone can access. No port forwarding is required.
```bash
cloudflared tunnel --url http://localhost:8000
```

---

## Tailscale
Tailscale was used to create a private network. It gives the machine a private IP (100.x.x.x). Only devices connected to Tailscale can access the server.
```bash
tailscale up
# Access via: http://100.x.x.x:8000
```

---

## Comparison

| Feature         | Cloudflare Tunnel     | Tailscale            |
|-----------------|-----------------------|----------------------|
| Access Type     | Public                | Private              |
| URL             | Public HTTPS URL      | 100.x.x.x IP        |
| Auth Required   | No                    | Yes                  |
| Use Case        | Web apps, demos       | Internal networks    |
| Port Forwarding | Not needed            | Not needed           |
| Encryption      | TLS (HTTPS)           | WireGuard VPN        |

---

## Why Zero Trust?
Both tools follow the Zero Trust model — no open ports, access is verified, and only authorized users can reach the server.

---

## Screenshots
- Local server running
- Cloudflare tunnel command and URL
- Cloudflare URL opened in browser
- Tailscale IP access in browser

---
## Dev Environment
This project includes a `.devcontainer` configuration for VS Code.
It sets up the environment automatically with all required tools.

To use it:
1. Open the project in VS Code
2. Install the **Dev Containers** extension
3. Click **Reopen in Container** when prompted
---

## Conclusion
Cloudflare is useful for exposing services to the public securely. Tailscale is useful for private and secure communication between devices. Both avoid opening ports and improve security.

**Recommendation:** Use Cloudflare for public-facing demos and Tailscale for internal access. Together they demonstrate a complete Zero Trust remote access strategy.
