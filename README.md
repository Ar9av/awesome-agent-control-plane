# Awesome Agent Control Plane [![Awesome](https://awesome.re/badge.svg)](https://awesome.re)

[![License: CC0-1.0](https://img.shields.io/badge/License-CC0_1.0-lightgrey.svg)](https://creativecommons.org/publicdomain/zero/1.0/)
[![PRs Welcome](https://img.shields.io/badge/PRs-welcome-brightgreen.svg)](CONTRIBUTING.md)

> A curated list of tools, frameworks, and resources for building and securing the **AI agent control plane** — the layer that decides what an autonomous agent is allowed to do, before it does it.

AI agents don't just generate text anymore — they call tools, run shell commands, hit APIs, read and write files, and talk to other agents. The control plane is everything that governs that behavior: identity for agents, policy enforcement at the point of action, gateways that mediate traffic, sandboxes that contain the blast radius, and the audit trail that proves what happened.

This list is organized around that lifecycle rather than around any single vendor or protocol.

## Contents

- [🆔 Identity & Non-Human Access](#-identity--non-human-access)
- [🚧 Policy Enforcement & Runtime Control](#-policy-enforcement--runtime-control)
- [🌐 Gateways & Proxies](#-gateways--proxies)
- [📦 Sandboxing & Isolation](#-sandboxing--isolation)
- [⚔️ Red Teaming & Vulnerability Scanners](#️-red-teaming--vulnerability-scanners)
- [🔍 Static Analysis & Linters](#-static-analysis--linters)
- [📊 Evaluation & Benchmarks](#-evaluation--benchmarks)
- [🧩 Agent Frameworks (control-plane-adjacent)](#-agent-frameworks-control-plane-adjacent)
- [Contributing](#contributing)
- [License](#license)

---

## 🆔 Identity & Non-Human Access
*Treating agents as first-class identities that can be authenticated, scoped, and revoked.*

- **[SPIFFE/SPIRE](https://github.com/spiffe/spire)** - A CNCF-graduated workload identity framework issuing cryptographic identity to services and, increasingly, to autonomous agents and their workloads.
- **[WSO2](https://github.com/wso2)** - Identity and access management tooling that treats AI agents as first-class identities, enabling authentication and authorization for agent actions.

## 🚧 Policy Enforcement & Runtime Control
*The core control-plane layer: evaluating and blocking agent tool calls against policy before they execute.*

- **[Prismor](https://github.com/PrismorSec/prismor)** - Self-hosted runtime control plane for AI coding agents. Hooks into Claude Code, Codex, and other agent SDKs to block dangerous commands, secret leaks, and prompt injection before they execute.
- **[NeMo Guardrails](https://github.com/NVIDIA/NeMo-Guardrails)** - NVIDIA's toolkit for adding programmable rails to LLM-based apps, keeping agents on topic and enforcing safety policies.
- **[Guardrails](https://github.com/guardrails-ai/guardrails)** - A Python framework for validating LLM inputs/outputs against structural and semantic rules.
- **[Invariant](https://github.com/invariantlabs-ai/invariant)** - Guardrails for secure and robust agent development, enforcing runtime policies over agent traces and tool calls.
- **[LLM Guard](https://github.com/protectai/llm-guard)** *(archived)* - A security toolkit for LLM interactions, scanning prompts and outputs for prompt injection, PII, and toxic content. Archived by Protect AI in 2026 and no longer maintained; listed for reference only.
- **[OWASP Agent Memory Guard](https://github.com/OWASP/www-project-agent-memory-guard)** - An official OWASP project detecting and blocking AI agent memory poisoning (OWASP ASI06), with drop-in middleware for LangChain, AutoGen, and CrewAI.

## 🌐 Gateways & Proxies
*Mediating traffic between agents, tools, and models — the network layer of the control plane.*

- **[AgentGateway](https://github.com/agentgateway/agentgateway)** - A Linux Foundation project providing an AI-native proxy for secure connectivity (A2A & MCP protocols), adding RBAC, observability, and policy enforcement.
- **[Envoy AI Gateway](https://gateway.envoyproxy.io/)** - An Envoy-based gateway managing request traffic to GenAI services, providing a control point for rate limiting and policy enforcement.
- **[Portkey AI Gateway](https://github.com/portkey-ai/gateway)** - An AI gateway with integrated guardrails, routing across 1,600+ LLMs behind a single API.
- **[Kong](https://github.com/Kong/kong)** - The API gateway's AI Gateway plugin extends Kong's existing traffic-control and auth model to LLM and agent traffic.
- **[Cloudflare AI Gateway](https://developers.cloudflare.com/ai-gateway/)** - A managed gateway in front of any LLM provider, adding caching, rate limiting, and logging for agent/LLM traffic.

## 📦 Sandboxing & Isolation
*Secure runtimes that contain what an agent can touch on the host system.*

- **[E2B](https://github.com/e2b-dev/e2b)** - Open-source infrastructure for running AI-generated code in secure, isolated cloud sandboxes.
- **[SandboxAI](https://github.com/substratusai/sandboxai)** - An open-source runtime for executing AI-generated code (Python/Shell) in isolated containers with granular permission controls.
- **[Kubernetes Agent Sandbox](https://github.com/kubernetes-sigs/agent-sandbox)** - A Kubernetes-native Sandbox Custom Resource Definition (CRD) for managing isolated, stateful agent workloads.
- **[Agent-Infra Sandbox](https://github.com/agent-infra/sandbox)** - An all-in-one sandbox combining browser, shell, VSCode, and file-system access in a single Docker container for agentic tasks.
- **[OpenHands](https://github.com/All-Hands-AI/OpenHands)** - Formerly OpenDevin; includes a secure runtime environment for autonomous coding agents to operate without touching the host machine's sensitive files.

## ⚔️ Red Teaming & Vulnerability Scanners
*Offensive tools that test agents for security flaws, unauthorized actions, and injection susceptibility.*

- **[PyRIT](https://github.com/Azure/PyRIT)** - Microsoft's open-source red teaming framework for generative AI, automating multi-turn adversarial attacks against agents.
- **[Garak](https://github.com/leondz/garak)** - A vulnerability scanner that probes models for hallucination, data leakage, and prompt injection susceptibility.
- **[Agentic Security](https://github.com/msoedov/agentic_security)** - A vulnerability scanner for agent workflows and LLMs, running multi-step jailbreaks and fuzzing attacks against agent logic.
- **[A2A Scanner](https://github.com/cisco-ai-defense/a2a-scanner)** - A Cisco scanner inspecting Agent-to-Agent communication protocols, validating agent identities and communication-spec compliance.
- **[Cybersecurity AI (CAI)](https://github.com/aliasrobotics/cai)** - A framework for building specialized offensive and defensive security agents, often used in CTF scenarios.
- **[ATR (Agent Threat Rules)](https://github.com/Agent-Threat-Rule/agent-threat-rules)** - Open-source regex detection rules for AI agent threats: prompt injection, tool poisoning, credential exfiltration, skill compromise.

## 🔍 Static Analysis & Linters
*Analyzing agent configuration and orchestration logic before deployment.*

- **[Aguara](https://github.com/garagon/aguara)** - A static security scanner for AI agent skills and MCP server configurations, detecting prompt injection, credential leaks, and supply-chain attacks.
- **[Agentic Radar](https://github.com/splx-ai/agentic-radar)** - Visualizes agent workflows (LangGraph, CrewAI, AutoGen), detecting risky tool usage and permission loops.
- **[Agent Bound](https://github.com/ElPaisano/agent-bound)** - Design-time analysis calculating "Agentic Entropy" to quantify unpredictability and loop/action risk in agent architectures.
- **[Checkov](https://github.com/bridgecrewio/checkov)** - Primarily an IaC scanner; includes policies for AI infrastructure and deployment configuration.

## 📊 Evaluation & Benchmarks
*Measuring agent and guardrail security performance.*

- **[CVE Bench](https://github.com/uiuc-kang-lab/cve-bench)** - A benchmark evaluating an AI agent's ability to exploit real-world web application vulnerabilities.
- **[DeepEval](https://github.com/confident-ai/deepeval)** - An LLM evaluation framework with test cases for hallucination, bias, and security-relevant failure modes.
- **[PINT Benchmark](https://github.com/lakeraai/pint-benchmark)** - A benchmark for evaluating prompt injection detection systems.

## 🧩 Agent Frameworks (control-plane-adjacent)
*Frameworks for building agents that the tools above are typically layered onto.*

- **[Microsoft Agent Framework](https://github.com/microsoft/agent-framework)** - A framework for building, orchestrating, and deploying AI agents and multi-agent workflows (Python and .NET).

---

## Contributing

Contributions are welcome — see [CONTRIBUTING.md](CONTRIBUTING.md).

1. Fork the project.
2. Add your entry in the relevant section, alphabetized within it.
3. Follow the existing format: `- **[Name](URL)** - One factual sentence, ending with a period.`
4. Open a pull request.

Tools should be actively maintained (a commit within the last 12 months) and directly relevant to securing or governing autonomous AI agents.

## License

[CC0](LICENSE) - This work is in the public domain, following the [awesome list](https://github.com/sindresorhus/awesome) convention.
## Hosted AI Gateways

- **[APIClaw](https://apiclaw.biz)** - A hosted flat-rate OpenAI-compatible AI API gateway for Claude, GPT, Kimi, Qwen, DeepSeek, and GLM, with plans from $19/month and a 50-request free trial.
