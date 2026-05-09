<p align="center">
  <img src="https://raw.githubusercontent.com/Nox-HQ/.github/main/profile/nox-logo.png" alt="NOX" width="280" />
</p>

<p align="center">
  <strong>The polyglot, agent-native security scanner with AI risks built in.</strong><br/>
  Find prompt-injection, RAG-boundary, MCP-misuse, and supply-chain risks alongside the SAST and SCA findings you already expect — without sending a single line of code to a vendor.
</p>

<p align="center">
  <a href="https://github.com/Nox-HQ/nox/releases"><img src="https://img.shields.io/github/v/release/Nox-HQ/nox?style=flat-square" alt="Latest release" /></a>
  <a href="https://github.com/Nox-HQ/nox"><img src="https://img.shields.io/github/stars/Nox-HQ/nox?style=flat-square&label=stars" alt="Stars" /></a>
  <a href="https://github.com/Nox-HQ/nox/blob/main/LICENSE"><img src="https://img.shields.io/badge/license-Apache--2.0-blue?style=flat-square" alt="License" /></a>
  <a href="https://github.com/Nox-HQ/nox"><img src="https://img.shields.io/badge/output-SARIF%20%7C%20SBOM%20%7C%20AI--BOM-blueviolet?style=flat-square" alt="Outputs" /></a>
  <a href="https://github.com/Nox-HQ/nox"><img src="https://img.shields.io/badge/agent--native-MCP-purple?style=flat-square" alt="MCP" /></a>
</p>

---

## The struggling moment

You shipped an LLM endpoint last quarter. Your SAST runs on every PR — and reports zero AI-related findings, because it has none. Security asks how you handle prompt injection, model provenance, and tool-permission scope; the honest answer is "we don't scan for it." Meanwhile your existing scanner is a SaaS, and legal won't let half the org use it because uploads breach data residency.

NOX exists to close that gap without trading away the controls you already have.

---

## 30-second quickstart

```sh
# Install (any one)
brew install nox-hq/tap/nox            # macOS / Linux
go install github.com/nox-hq/nox/cli@latest
docker run --rm -v "$PWD":/src ghcr.io/nox-hq/nox scan /src

# Scan
nox scan .

# Emit SARIF + SBOMs + AI-BOM
nox scan . --format all --output nox-out

# CI: GitHub Action
# - uses: nox-hq/nox@v1
```

[**Full quickstart →**](https://github.com/Nox-HQ/nox#quickstart)

---

## Who NOX is for

- **AppSec engineers at AI-native teams** who need first-class AI rules (prompt injection, embedding leakage, agent over-privilege) alongside their SAST without bolting on a second tool.
- **Platform & security teams in compliance-bound orgs** (financial services, healthcare, public sector) blocked from SaaS scanners by data residency. NOX runs offline; your code never leaves the runner.
- **OSS maintainers** who want one scanner that emits SARIF, CycloneDX, and SPDX from a single command — no signup, no telemetry.

---

## What NOX scans

Five lanes, one engine. 717 built-in rules across the lanes below; plugins layer in on top.

| Lane | Examples | Sample rules |
|------|----------|--------------|
| **AI security** | Prompt injection, RAG boundary, MCP tool misuse, model provenance, AI-BOM | `AI-001`, `AI-021`, `MCP-001..008` |
| **Code & secrets** | Hardcoded credentials, SQL injection, command injection, XSS, taint flows | `SEC-001..160`, `TAINT-001..007` |
| **Infrastructure as Code** | Terraform / Kubernetes / Ansible / Kustomize misconfigurations + cross-resource graph rules | `IAC-001..369` |
| **Dependencies & supply chain** | OSV vulnerabilities, dependency confusion, container CVEs, license posture | `VULN-001..003`, `CONT-001..002`, `LIC-001` |
| **Data sensitivity** | PII / PHI / PCI patterns and exposure risk | `DATA-001..012` |

---

## Plugin marketplace

NOX is a small core with a [signed plugin marketplace](https://github.com/Nox-HQ/nox#plugin-ecosystem). 32 plugins ship today; new ones are a `nox plugin install` away.

| Track | What it does |
|-------|--------------|
| **Core analysis** | Architecture lint, container scan, MCP server analysis, logic checks |
| **Dynamic runtime** | DAST, attack-surface mapping, K8s runtime + drift, red-team chains |
| **Supply chain** | Artifact integrity, dependency confusion, provenance verification |
| **Policy & governance** | Policy gates, risk register, GRC across SOC2 / ISO 27001 / FedRAMP / HIPAA / PCI-DSS / NIST 800-53 / CIS / CMMC |
| **Threat modeling** | LLM-assisted explanations and STRIDE threat modeling |
| **Intelligence** | Risk scoring, threat enrichment, business-context risk amplification |
| **Incident readiness** | Detection-readiness checks, response playbooks |
| **Developer experience** | LSP, multi-plugin orchestrator, report composer |
| **Agent assistance** | Case bundling, AI-assisted triage with history learning, validator |

Plugins run out-of-process in a sandbox with explicit safety envelopes (read-only by default, network allowlists, file-path scopes). Every plugin is cosign-signed and verifiable from the marketplace index.

[**Browse the marketplace →**](https://github.com/Nox-HQ)

---

## Coexists with what you already run

NOX emits SARIF 2.1.0, so you can publish its findings to the same GitHub Code Scanning tab as Semgrep, CodeQL, or Snyk. Run NOX for the AI + supply-chain + IaC + cross-resource gap; keep your existing SAST for whatever you already trust. No rip-and-replace required.

---

## Outputs

| File | Format |
|------|--------|
| `results.sarif` | SARIF 2.1.0 (GitHub Code Scanning compatible) |
| `findings.json` | Canonical findings schema (stable fingerprints) |
| `sbom.cdx.json` | CycloneDX SBOM |
| `sbom.spdx.json` | SPDX SBOM |
| `ai.inventory.json` | AI-BOM v2.0 — model provenance, prompt templates, tool matrix |
| `report.html` | Standalone HTML report with filtering and severity sort |

---

## Principles

NOX is a **security primitive**, not a platform.

| | Principle | What it means in practice |
|---|---|---|
| **1** | Deterministic | Same inputs, same outputs. Fingerprints are stable across runs. |
| **2** | Auditable | Every finding traces to a rule ID, engine version, and matched location. |
| **3** | Offline-first | Zero required external services. Code never leaves your environment. |
| **4** | Read-only by default | Never executes untrusted payloads. Never auto-applies fixes without an explicit opt-in. |
| **5** | Agent-native | MCP server + structured findings so AI agents can consume scan results without parsing logs. |

---

## Get involved

- Star [Nox-HQ/nox](https://github.com/Nox-HQ/nox) — the home of the engine, CLI, MCP server, and plugin SDK.
- [Discussions](https://github.com/Nox-HQ/nox/discussions) — RFCs, plugin proposals, and the community roadmap.
- Build a plugin — see the [plugin SDK](https://github.com/Nox-HQ/nox/tree/main/sdk) for the gRPC contract.
- Use the GitHub Action — [`nox-hq/nox`](https://github.com/marketplace/actions/nox-security-scanner) on the marketplace.
- Automate dependency upgrades — [`nox-hq/nox-remediate-action`](https://github.com/Nox-HQ/nox-remediate-action) opens remediation PRs from your scan results.

---

<p align="center">
  <sub>NOX focuses on determinism, auditability, and explicit security boundaries.</sub><br/>
  <sub>It is not a SaaS platform, exploit framework, or autonomous remediation system.</sub>
</p>
