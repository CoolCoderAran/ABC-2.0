
# Security Policy

The ABC 2.0 Project takes the security and reliability of our compiler, standard library, and runtime environment seriously. This policy outlines our standards, how to safely report vulnerabilities, and our process for delivering timely security updates.

---

## Reporting Security Issues

If you discover a security vulnerability or potential threat within ABC 2.0, please report it privately. Do **not** open a public issue on GitHub.

* **Preferred Contact Method:** Email [aran.rath@outlook.com](mailto:aran.rath@outlook.com) with the subject line `[SECURITY VULNERABILITY] ABC 2.0`.
* **Required Information:** Include a description of the issue, step-by-step instructions to reproduce the vulnerability, and any relevant proof-of-concept code or environment details.
* **Expected Response Time:** You will receive an initial acknowledgment within **48 hours**. We aim to provide a full assessment and remediation plan within **7 days**.

---

## Security Requirements

To protect the integrity of the core compiler engine and downstream software built with ABC 2.0, contributors and users must adhere to the following rules:

* **No Unsolicited Telemetry:** All core tools and standard library implementations must run strictly locally without transmitting data, metrics, or source code over the network.
* **Dependency Auditing:** Dependencies used in the compiler build chain must be continuously updated and audited using `cargo audit` (or equivalent toolchain scanners).
* **Safe Memory Practices:** Core memory operations must adhere to modern safe-programming standards to prevent buffer overflows, double frees, or memory corruption.

---

## Vulnerability Handling Process

Once a security report is submitted:

1. **Triage:** Maintainers review the report to confirm the vulnerability and assess its severity.
2. **Patch Development:** Fixes are developed and tested privately in a restricted branch.
3. **Prioritization:** Critical vulnerabilities (e.g., arbitrary code execution in the parser) take top priority and trigger an emergency patch release.
4. **Disclosure Timeline:** Fixes are published along with a advisory notice within 30 days of the initial private report, allowing coordinated public disclosure.

---

## Supported Versions

Only the current major release version receives active security patches.

| Version | Supported |
| :--- | :--- |
| **2.x (Current)** | Yes |
| **1.x / Historic ABC** | No |

---

## Hardening Recommendations

When deploying or distributing ABC 2.0 binaries, we recommend the following configurations:

* **Build Flags:** Compile releases with standard stack hardening and optimization flags enabled (`cargo build --release`).
* **Source Verification:** Always build from tagged, signed git releases or verify release binary checksums prior to execution.
* **Environment Isolation:** Run untrusted ABC source scripts inside restricted execution environments or sandboxed containers when evaluating external submissions.

---

## Help & Integrity Verification

If you suspect a compromised binary or need to verify the integrity of your ABC 2.0 distribution:

* **Signature Verification:** Check the SHA-256 checksums provided on the official release page against your local binary:
  ```
  sha256sum abc2
Markdown
### Dependency Tree Check
Run automated dependency checks on your local build workspace:

```cargo audit```

## Authors

Security issues and vulnerability assessments are managed by:

* **Aran Rath** (Project Lead & Security Officer) – [aran.rath@outlook.com](mailto:aran.rath@outlook.com)

---

## Acknowledgments

Our security standards and disclosure practices are inspired by guidelines from:

* OWASP (Open Web Application Security Project)
* GitHub Security Advisory Standards
* Coordinated Vulnerability Disclosure (CVD) best practices
