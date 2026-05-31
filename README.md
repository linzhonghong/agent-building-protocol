# Agent Building Protocol (ABP) Specification

[![Protocol Version](https://img.shields.io/badge/ABP_Spec-v1.0--alpha-orange.svg)](./SPECIFICATION.md)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

> **A neutral, open-source, language-agnostic specification for an "agent container runtime layer and digital employee instantiation protocol" (Agent Container Runtime Standard).**

---

## Why Does ABP Exist?

In the current large-model engineering ecosystem, serious non-standard barriers exist between upper-layer orchestration tools (IDEs, visual editors, Meta Agents) and lower-layer execution environments (fragmented Python, Go, and other scaffold frameworks).

ABP starts from one hard premise: **an agent artifact compiled by development tools should not be a patch of code executed by a specific framework. It should directly be an independent "digital employee process container" with a trusted digital identity, distributed-state handoff, and long-lived in-memory residency.**

ABP completely flattens differences between programming languages and underlying physical compute. It defines a unified topology abstract syntax tree (AST) and fine-grained component lifecycle, enabling: **"orchestrate once, run as a cross-language resident equivalent."**

---

## Repository Layout

This repository does not contain runtime implementation code for any specific language, such as Go, Python, or Rust. It is a purely neutral contract asset:

```text
abp-en/
|-- schema/
|   |-- abp-instance.schema.json  # Hard contract for infrastructure and operations identity
|   `-- graph.schema.json         # Hard contract for brain topology and component execution flow
|-- SPECIFICATION.md              # ABP v1.0 protocol semantics white paper
`-- README.md
```

## Ecosystem Compatibility Matrix

* **Upper control plane (Editor / Meta Agent)**: only needs to integrate with the `json-schema` rules in this repository, ensuring that generated artifact bundles conform to the topology specification without caring about the underlying runtime environment.
* **Downstream data plane (Harness / Runner)**: regardless of implementation language, if its kernel parser can understand the `graph.json` defined by this specification and satisfy the four mandatory execution phases, it can seamlessly take over an agent brain delivered by the upstream flow.

## Official Language Dialect Reference Implementations

* **Official minimal Golang microkernel reference implementation**: [infra-claw/abp-kernel-go](https://www.google.com/search?q=https://github.com/infra-claw/abp-kernel-go)
* **Python/LangGraph-compatible kernel reference implementation**: *[Coming Soon]*
