# Security Policy

## Supported Versions

This project is a Zabbix template, not a software library. Only the latest
release is maintained. There are no backport fixes to older versions.

| Version | Supported          |
| ------- | ------------------ |
| Latest (v1.x) | :white_check_mark: |
| Older releases | :x: |

If a security-relevant issue is found, a new release will be published and
older releases will be marked accordingly in the changelog.

## Scope

This project consists of a Zabbix 7.4 JSON template file. Security issues
in scope include:

- Credentials or sensitive values unintentionally hardcoded in the template
- Unsafe JavaScript preprocessing that could be exploited if the monitored
  device returns malicious data
- HTTP item configurations that unnecessarily expose credentials or widen
  the attack surface on the Zabbix server or proxy
- Trigger or item logic that could suppress security-relevant alerts (e.g.
  silently ignoring a disabled-auth state on the device)

Out of scope:

- Vulnerabilities in Zabbix itself — report those to the
  [Zabbix security team](https://www.zabbix.com/security)
- Vulnerabilities in Shelly device firmware — report those to
  [Shelly support](https://www.shelly.com/en/support)
- Security issues arising from misconfiguration of the user's own Zabbix
  instance or network (e.g. exposing Zabbix to the internet, using weak
  passwords)

## Reporting a Vulnerability

Please **do not** open a public GitHub issue for security vulnerabilities.

Report privately via GitHub's built-in private vulnerability reporting:
**Security → Report a vulnerability** on this repository.

Alternatively, you can reach the maintainer directly via the email address
on the GitHub profile.

Include in your report:
- A description of the issue and its potential impact
- The affected template version (check the `version` field in the JSON or
  the latest release tag)
- Steps to reproduce or a proof-of-concept where applicable

### What to expect

| Timeframe | Action |
| --------- | ------ |
| Within 7 business days | Acknowledgement of the report |
| Within 30 days | Assessment and, if confirmed, a fix or mitigation |
| Upon release | Credit in the changelog unless you prefer to remain anonymous |

If the vulnerability is declined, you will receive an explanation of why it
was considered out of scope or not reproducible.

## Security Considerations for Users

This template polls Shelly devices over plain HTTP by default. Before
deploying in a sensitive environment:

- Enable HTTP authentication on every Shelly device (`{$SHELLY_PASS}`)
- Place Shelly devices on a dedicated IoT VLAN isolated from untrusted hosts
- Monitor the **Device: Authentication enabled** item — if it reads `No`,
  your device is unprotected on the network
- Consider overriding the URL scheme to `https` if your Shelly firmware and
  Zabbix version support it
