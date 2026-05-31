# Agent Building Protocol (ABP) Specification

[![Protocol Version](https://img.shields.io/badge/ABP_Spec-v1.0-blue.svg)](./SPECIFICATION.md)
[![License](https://img.shields.io/badge/License-Apache%202.0-blue.svg)](https://opensource.org/licenses/Apache-2.0)

> **A neutral, open-source, language-agnostic specification for an "agent container runtime layer and digital employee instantiation protocol" (Agent Container Runtime Standard).**

---

## Status

Current specification version: **ABP v1.0**.

## Why Does ABP Exist?

In the current large-model engineering ecosystem, serious non-standard barriers exist between upper-layer orchestration tools (IDEs, visual editors, Meta Agents) and lower-layer execution environments (fragmented Python, Go, and other scaffold frameworks).

ABP starts from a core design premise: **an agent artifact compiled by development tools should not be a patch of code executed by a specific framework. It should directly become an independent "digital employee process container" with a trusted digital identity, distributed-state handoff, and long-lived in-memory residency.**

ABP flattens differences between programming languages and underlying physical compute. It defines a unified topology abstract syntax tree (AST) and fine-grained component lifecycle, enabling: **"orchestrate once, run as a cross-language resident workload."**

---

## Repository Layout

This repository does not contain runtime implementation code for any specific language, such as Go, Python, or Rust. It is a purely neutral contract asset:

```text
agent-building-protocol/
+-- schema/
|   +-- abp-instance.schema.json  # Hard contract for infrastructure and operations identity
|   +-- graph.schema.json         # Hard contract for brain topology and component execution flow
+-- SPECIFICATION.md              # ABP v1.0 protocol semantics white paper
+-- README.md
```

## Minimal Artifact Bundle

Every ABP v1.0-compatible agent deliverable must expose at least the following core descriptor structure after extraction:

```text
artifact/
+-- abp-instance.yaml
+-- graph.json
```

## What This Repository Defines

* The physical delivery structure of agent artifact bundles.
* The protocol boundary of `abp-instance.yaml` and `graph.json`.
* The three-layer state space, four-phase component lifecycle, component URN, and SPI constraints.
* The contract interface between the control plane (Editor / Meta Agent) and the data plane (Harness / Runner).

## What This Repository Does Not Define

* It does not provide runtime implementations in Go, Python, Rust, or any other language.
* It does not bind to any specific LLM provider, vector database, graph database, or cloud vendor.
* It does not prescribe the downstream Harness internal engineering architecture; it only defines the protocol behavior that the Harness must satisfy.

## Ecosystem Compatibility Matrix

* **Upper control plane (Editor / Meta Agent)**: only needs to integrate with the `json-schema` rules in this repository, ensuring that generated artifact bundles conform to the topology specification without caring about the underlying runtime environment.
* **Downstream data plane (Harness / Runner)**: regardless of implementation language, if its kernel parser can understand the `graph.json` defined by this specification and satisfy the four mandatory execution phases, it can take over an agent brain delivered by the upstream flow.
