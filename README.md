# skill-safety-api
Safety scanner for Claude Code SKILL.md files,  scripts, templates, and references.

# Skill Safety

**Security scanner for Claude Code skills.** Scan any skill before you install it — get a structured safety report with MITRE ATT&CK-mapped findings, a clear verdict, and a plain-English summary.

> Claude Code skills are powerful — but installing one means running someone else's code on your machine. Skill Safety tells you what a skill does before you trust it.

---

## Why Skill Safety?

- **Fast** — 143 static rules run in milliseconds, no waiting
- **Comprehensive** — covers 106 MITRE ATT&CK techniques across 15 attack categories
- **Actionable** — every finding tells you what, where, how serious, and why
- **No setup** — one API call, structured JSON response, nothing to install or configure
- **Deep scan available** — optional LLM analysis catches subtle risks that regex can't (logic abuse, social engineering, data leakage)

---

## How It Works

```
You give us a skill URL
     |
     v
143 security rules scan the skill in milliseconds
     |
     v
You get: verdict + findings + summary
```

**One API call. Instant results. No code to deploy.**

---

## What It Detects

143 rules covering 106 MITRE ATT&CK technique IDs across 15 categories:

| Category | What it catches | Severity |
|---|---|---|
| Credential Access | SSH keys, AWS creds, passwords, browser tokens, keyloggers | HIGH |
| Exfiltration | `curl -d`, reverse shells, DNS tunneling, webhooks, cloud upload | HIGH |
| Command & Control | Beaconing, ngrok/chisel tunnels, proxychains, remote desktop | HIGH |
| Dangerous Execution | `eval`/`exec`, PowerShell, `docker exec`, trojan delivery | HIGH |
| Privilege Escalation | setuid, ptrace injection, CVE exploits, sudo abuse | HIGH |
| Defense Evasion | Base64 decode+exec, obfuscation, evidence deletion, Unicode smuggling | HIGH |
| Persistence | Cron jobs, systemd services, shell RC files, authorized_keys | HIGH |
| Collection | Screen capture, clipboard read, archive sensitive dirs | HIGH |
| Impact | `dd` wipe, ransomware, crypto mining, service stop, shutdown | HIGH |
| Lateral Movement | SSH with stolen keys, VNC, tool transfer | HIGH |
| Prompt Injection | Instruction override, persona hijack, delimiter injection | HIGH |
| Tool Poisoning | `allow_all_tools`, sandbox bypass | HIGH |
| Supply Chain | Unpinned `pip install git+`, `cargo install --git` | MEDIUM |
| Initial Access | Compromised registries, spearphishing links | MEDIUM |
| Discovery | `nmap`, network shares, system enumeration | LOW |

---

## Verdicts

| Risk | Verdict | Recommendation | Meaning |
|---|---|---|---|
| NONE | **safe** | INSTALL | No issues found |
| LOW/MEDIUM | **suspicious** | REVIEW / CAUTION | Minor or moderate risks detected |
| HIGH | **unsafe** | BLOCK | Serious security risks — do not install |
