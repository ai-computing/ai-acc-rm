 AI Accelerator Resource Management System (Planning)

**Status:** _Planning / Pre‑Alpha_. This repository describes and prepares a **resource management system (RMS) for AI accelerators**. It is **not yet feature‑complete** and **not ready for production**.

This repo aggregates the following components as **Git submodules** (for future integration):

| Submodule | Description |
|-----------|-------------|
| [llm_inference](https://github.com/ai-computing/llm_inference) | LLM inference engine for AI accelerators |
| [furiosa-env-tools](https://github.com/ai-computing/furiosa-env-tools) | Environment and deployment tools |
| [netri-zero](https://github.com/ai-computing/netri-zero) | Network interface for zero-copy data transfer |
| [rm_abstract_layer](https://github.com/ai-computing/rm_abstract_layer) | Resource management abstraction layer |
| [rm_monitor](https://github.com/ai-computing/rm_monitor) | Resource monitoring and telemetry service |

> **Important:** The RMS layer that orchestrates scheduling, allocation, and monitoring is **under active design**. Interfaces, directory layout, and tooling **will change**.

---

## Goal

Provide a unified software layer to **plan, schedule, and monitor** accelerator resources for **LLM inference** and related workloads, targeting high utilization and predictable QoS on AI accelerator hardware.

---

## Current Status (What _is_ true today)

- Repository scaffold with submodules is set up.  
- Integration between submodules and the RMS layer is **not implemented** yet.  
- Public APIs, CLIs, and services are **unstable / subject to change**.  
- Example commands below are **illustrative** and **may not work** until milestones are completed.

---

## Planned Features (Subject to Change)

- **Resource‑aware scheduling** for accelerator tasks (job queueing, placement policies, preemption)
- **Dynamic allocation & isolation** across concurrent inference jobs
- **Telemetry, monitoring, and profiling** (utilization, latency, throughput)
- **Environment bootstrap utilities** leveraging `furiosa-env-tools`
- **Operator & developer workflows** (CLI + REST/gRPC, job templates, configs)
- **Multi‑tenant safety** (quotas, limits, fair sharing)

---

## Roadmap / Milestones

- [ ] Repository layout & dev environment bootstrap  
- [ ] Resource model & configuration schema (YAML/TOML)  
- [ ] Minimal job runner + accelerator device discovery  
- [ ] Basic scheduler (FIFO) and runtime hooks  
- [ ] Metrics pipeline (exporters/collectors) and dashboards  
- [ ] Policies: bin‑packing / priority / preemption (experimental)  
- [ ] CLI & REST/gRPC control plane (alpha)  
- [ ] Documentation & examples (alpha)  
- [ ] Stabilization, tests, and first tagged release (v0.1.0‑alpha)

This list is **aspirational** and may evolve as design progresses.

---

## Getting Started (For Contributors)

Clone the repo **with submodules**:
```bash
git clone --recursive https://github.com/<your-org>/<your-repo>.git
cd <your-repo>
# If you already cloned:
git submodule update --init --recursive
```

> Until the v0.1.0‑alpha milestone, the RMS code may be incomplete.
> For now, please refer to the submodule READMEs for their independent usage:
> - `llm_inference`: see its own README for build/run instructions.
> - `furiosa-env-tools`: see its own README for environment setup tips.
> - `netri-zero`: see its own README for network interface configuration.
> - `rm_abstract_layer`: see its own README for abstraction layer APIs.
> - `rm_monitor`: see its own README for monitoring setup.

---

## Planned Example (Not Implemented Yet)

> The following is **a plan** for how usage might look once core milestones land.  
> **Do not expect these commands to work yet.**

```bash
# hypothetical CLI (planned)
rmsctl cluster init --config configs/cluster.example.yaml
rmsctl device list
rmsctl job submit --model llama-3 --accel AICARD0 --replicas 2 --qos high
rmsctl job status <job-id>
```

---

## Repository Structure (Will Evolve)

```
.
├── llm_inference/           # Submodule — LLM inference engine
├── furiosa-env-tools/       # Submodule — Environment/deployment tools
├── netri-zero/              # Submodule — Network interface (zero-copy)
├── rm_abstract_layer/       # Submodule — Resource management abstraction
├── rm_monitor/              # Submodule — Monitoring and telemetry
├── configs/                 # (planned) RMS configs and policies
├── scripts/                 # (planned) Helper scripts / dev tooling
├── rms/                     # (planned) RMS core services & libs
└── README.md
```

---

## Contributing

Contributions are welcome, especially around **design discussions**, **RFCs**, and **early prototypes**. Please open an issue to propose changes, or draft a design doc before large PRs.

- Issues: planning items, RFCs, milestones
- PRs: small, reviewable steps preferred

---

## License

**TBD for this repository.** Submodules retain their **original licenses**.  
Final licensing for the RMS layer will be clarified before the first tagged release.

---

## Disclaimer

This project is **work in progress**. **Do not** deploy in production.  
APIs, behavior, and directory structure may change without notice during pre‑alpha.
