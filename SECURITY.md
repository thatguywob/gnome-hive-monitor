<!-- ste-disable-file: standard security policy boilerplate across org -->
# Security Policy

## Supported Versions

Hive Monitor is a GNOME Shell extension for GNOME Shell versions 45 through 50.
Only the latest release and the default development branch are actively supported.

| Version | Status |
|---|---|
| Latest release | ✅ Supported |
| `main` branch | ⚠️ Best effort (development) |
| Older releases | ❌ Unsupported — please upgrade to the latest version |

## Reporting a Vulnerability

**Please do not report security vulnerabilities through public GitHub issues.**

Instead, report them privately via GitHub Security Advisories:

1. Go to the [Security Advisories](https://github.com/tuna-os/gnome-hive-monitor/security/advisories/new) page
2. Click **Report a vulnerability**
3. Provide a detailed description of the issue, including steps to reproduce, impact, and affected versions

If you cannot use GitHub Security Advisories, contact the maintainers privately at `security@tunaos.org`.

You can expect:
- **Acknowledgment** within 48 hours
- **Status update** within 5 business days
- **Resolution timeline** based on severity

## Credential Safety & Security Model

Hive Monitor handles sensitive credentials configured by the user:
- **Hive token (`hive-token`)**: A secret token sent as the `X-Hive-Internal` header for read-only access to hive fleet metrics.
- **GitHub personal access token (`github-token`)**: Used to file idea issues on GitHub with `issues:write` scope.

Because this extension stores and transmits authentication tokens:
- **Strict HTTPS enforcement**: All communication with the configured hive URL must use HTTPS to prevent credential interception on the network.
- **Repository validation**: Target repository identifiers are strictly validated before making GitHub API requests.
- **Responsible disclosure**: Vulnerabilities involving credential exposure, server-side request forgery (SSRF), or insecure transport should be reported responsibly to prevent unauthorized access or token compromise.
- **No credential leaks**: Never commit credentials, tokens, or private endpoints in issues, pull requests, or log outputs.

## Scope

### In Scope
- Credential or token leakage in memory, network requests, logs, or user interface dialogs
- Insecure transport or bypass of HTTPS enforcement
- Path or URL injection that could route tokens to untrusted servers
- Code execution or sandbox escapes in the GNOME Shell extension runtime
- Cross-site or command injection vulnerabilities

### Out of Scope
- Bugs in upstream GNOME Shell, GJS, or Mutter (report to [GNOME GitLab](https://gitlab.gnome.org/GNOME))
- Vulnerabilities in upstream GitHub services or kubestellar/hive server software (report to respective upstreams)
- Attacks requiring existing root privileges or arbitrary code execution on the local host machine

## Disclosure Policy

We follow coordinated disclosure:
1. The reporter submits the vulnerability report privately.
2. Maintainers investigate the report and verify the issue.
3. A fix is developed and tested privately.
4. A security advisory is published along with the patched release.
