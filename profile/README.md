<p align="center">
  <img src="https://raw.githubusercontent.com/Nox-HQ/.github/main/profile/nox-logo.png" alt="NOX" width="280" />
</p>

<h1 align="center">NOX</h1>

<p align="center">
  <strong>Surface what hides in the dark.</strong><br/>
  Open-source, language-agnostic security engine for codebases, supply chains, runtime systems, and AI applications.
</p>

<p align="center">
  <a href="https://github.com/Nox-HQ"><img src="https://img.shields.io/badge/license-open--source-blue?style=flat-square" alt="License" /></a>
  <a href="https://github.com/Nox-HQ"><img src="https://img.shields.io/badge/output-SARIF%20%7C%20SBOM-blueviolet?style=flat-square" alt="Output Formats" /></a>
  <a href="https://github.com/Nox-HQ"><img src="https://img.shields.io/badge/agent--native-MCP-purple?style=flat-square" alt="MCP" /></a>
</p>

---

## Why NOX

Most security tools are opaque, SaaS-locked, and hard to compose.

NOX is a **security primitive** — deterministic, auditable, and designed to be inspected and extended, not a black-box platform.

## Core Principles

| | Principle | Description |
|---|---|---|
| **1** | Deterministic | Same inputs, same outputs. No hidden state. |
| **2** | Auditable | Every finding is explainable from inputs, rules, and engine version. |
| **3** | Language-Agnostic | Analyzes artifacts — source files, config, dependencies, containers, AI components. |
| **4** | Safe by Default | Never uploads code or executes untrusted payloads. Safe for CI and dev machines. |
| **5** | Agent-Native | Read-only, sandboxed MCP capabilities for AI agent workflows. |

## Features

- **Static Analysis** — Language-agnostic scanning across codebases
- **SBOM Generation** — CycloneDX and SPDX support
- **SARIF Output** — GitHub Code Scanning compatible
- **AI Security** — Analysis of prompts, tools, and RAG systems
- **Plugin System** — Strict, gRPC-based out-of-process plugins
- **MCP Integration** — Agent-native security workflows

## Quick Start

```sh
# Scan a repository
nox scan .

# Generate SARIF and SBOM
nox scan . --format sarif,sbom

# List installed plugins
nox plugin list
```

## Plugin Ecosystem

NOX is extensible by design. Plugins run out-of-process within explicit safety envelopes:

> DAST | Threat Modeling | Vulnerability Intelligence | Supply-Chain Checks | AI Runtime Security | Policy Enforcement | Incident Readiness

---

<p align="center">
  <sub>NOX focuses on determinism, auditability, and explicit security boundaries.</sub><br/>
  <sub>It is not a SaaS platform, exploit framework, or autonomous remediation system.</sub>
</p>
