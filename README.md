# Bastion Hardening Lab

An interactive cybersecurity game about hardening a Linux server. You review five findings on a simulated public-facing Ubuntu host, choose one hardening action for each, and run an audit. The audit scores your choices on two dimensions that pull against each other: **Security Level** and **Uptime/Usability**.

**[▶ Play it live](https://cjcodes11.github.io/Project-3-Hardening-Lab/)**

## What it covers

| Finding | Reference |
|---|---|
| SSH allows root login with passwords | CIS Ubuntu 5.2.10, CWE-250 |
| Unpatched Apache 2.4.49 path traversal / RCE | CVE-2021-41773, CVE-2021-42013 |
| PostgreSQL default credentials, listening publicly | CWE-1392, CWE-1188 |
| Host firewall off, 14 ports listening | CIS Ubuntu 3.5.1, NIST SP 800-41 |
| Web user with passwordless sudo | CWE-269 |
| `.git` exposed in the web root | CWE-538, OWASP WSTG-CONF-04 |
| Redis open to the internet with no auth | CWE-306 |
| TLS 1.0 and weak ciphers | PCI DSS 4.0 req. 4.2.1, CWE-327 |

Each round draws five of these. Every finding has four options: the correct control, a partial fix, a security-through-obscurity trap, and an overcorrection that "secures" the system by breaking it.

## Scoring

- **Security** is weighted by each finding's risk score. A full fix removes all of a finding's risk; a partial fix removes some.
- **Uptime** starts at 100 and drops with every control that blocks users, admins or deploys.
- **Posture grade** = 60% security + 40% uptime. If uptime falls below 60%, the grade is capped at D, because a server nobody can use isn't a win.

After each audit, every finding gets a verdict (Secured, Partial fix, Still exposed, Service broken) with an explanation of why the defense works or fails, plus the recommended control.

## Built with

- HTML5, Tailwind CSS (CDN), vanilla JavaScript; no build step
- Responsive layout with light and dark themes
- Data-driven: all vulnerabilities live in one `POOL` array, so new findings can be added without touching the rendering code

## Run locally

Open `index.html` in a browser.
