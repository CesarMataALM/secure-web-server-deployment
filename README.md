# Secure Web Server Deployment

**A hardened web server infrastructure project using Ubuntu Server, Docker, Nginx and TLS.**

## Project Overview

This project demonstrates the deployment and security hardening of a web server using Ubuntu Server, Docker and Nginx.

The objective is to deploy a functional web service while reducing its attack surface, securing remote administration and protecting HTTP communications.

Security testing is performed from a separate Kali Linux machine.

## Lab Architecture

The laboratory consists of two physical computers:

| Machine | Role | Environment |
|---|---|---|
| Laptop 1 | Target web server | Ubuntu Server |
| Laptop 2 | Security assessment | Kali Linux running in VirtualBox |

Both systems communicate over a local network.

## Technologies

- Ubuntu Server
- Docker Engine
- Nginx
- OpenSSH
- UFW
- OpenSSL
- Nmap
- Kali Linux
- VirtualBox

## Security Implementations

### SSH Hardening
- Root login disabled.
- Password authentication disabled.
- Public-key authentication enabled.
- Maximum authentication attempts limited.

### Docker Hardening
- Read-only root filesystem.
- Privileged mode disabled.
- Linux capabilities dropped and selectively restored.
- `no-new-privileges` enabled.
- Website and configuration files mounted read-only.

### HTTPS and TLS
- Self-signed RSA 2048-bit certificate.
- TLS 1.2 and TLS 1.3 enabled.
- TLS 1.2 cipher suites restricted to ECDHE with AES-GCM or ChaCha20-Poly1305.

### HTTP Security Headers
- Strict-Transport-Security
- X-Content-Type-Options
- X-Frame-Options
- Referrer-Policy

## Network Security Assessment

Testing was performed from Kali Linux using Nmap, OpenSSL and cURL.

### Exposed Services

| Port | Service | Purpose |
|---|---|---|
| 22 | SSH | Remote administration |
| 8080 | HTTP | Redirects to HTTPS |
| 8443 | HTTPS | Secure web access |

### Validation

- Nmap service detection.
- TLS cipher enumeration.
- HTTP response header inspection.
- Docker security configuration inspection.
- SSH configuration validation.

## Known Limitations

- The certificate is self-signed and intended for laboratory use.
- Nginx still identifies itself through the HTTP Server header, but its version is hidden.
- The environment is a local laboratory and is not production-certified.
- Docker-published ports require additional firewall considerations.

## Project Structure

```text
secure-web-server/
├── .gitignore
├── README.md
├── nginx/
│   └── default.conf
├── site/
│   └── index.html
├── docs/
└── screenshots/
```

## Learning Outcomes

- Linux server administration.
- Docker deployment and hardening.
- SSH security configuration.
- HTTPS and TLS configuration.
- Network reconnaissance.
- Security control validation.
- Infrastructure troubleshooting.

**Project status:** Core deployment and security hardening implemented and tested.
