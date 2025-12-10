# SERVER-
Main website
# Secure WHM/WHMCS Handover - CloudLinux/LiteSpeed Setup

## Overview
- Server: Contabo VPS (IP: 147.93.154.62), CloudLinux 9
- Hostname: yourserver.yourdomain.com
- WHM: https://147.93.154.62:2087 (root / [new strong pw])
- cPanel Sample: https://147.93.154.62:2083
- WHMCS: https://billing.yourdomain.com (admin / [strong pw])
- Licenses: cPanel, LiteSpeed Enterprise [key], Imunify360 [key], WHMCS [key]—renew via portals.
- Cloudflare: Zone: yourdomain.com (Full SSL, WAF on); API Token: [stored securely].

## Components
- OS: CloudLinux 9 (LVE enabled)
- Web: LiteSpeed Enterprise (via EasyApache; LSAPI for PHP)
- Panel: WHM/cPanel v122+
- Billing: WHMCS v9+ (integrated; Cloudflare module)
- Security: Imunify360 (WAF/malware), Cloudflare (CDN/DDoS)
- NS: ns1/ns2.yourdomain.com (via CF)
- Package: "SecureStarter" (LVE-limited, auto-CF proxy)

## Security
- Firewall: Imunify360 + CloudLinux (CF IPs whitelisted; direct access blocked)
- SSH: Key-only, no root pw login
- SSL: AutoSSL + CF Full Strict
- Malware: Imunify daily scans/quarantine; 2FA on WHM
- Backups: Daily remote (WHM); Imunify snapshots
- Monitoring: Imunify Dashboard; CF Analytics

## Maintenance
- Updates: `yum update -y` (OS); WHM > Update Now (cPanel/LiteSpeed); WHMCS Dashboard
- Scaling: Upgrade VPS; add LVE limits in WHM > CloudLinux Manager
- Logs: /var/log/imunify360; WHM > Server Status; CF Dashboard
- Client Test: Signup > Provision > Site via CF (green lock, fast load)

For issues: CloudLinux support (support@cloudlinux.com), CF docs (developers.cloudflare.com). Custom: Imunify > Rules for tuning.
