# AI Accelerator Resource Management System

AI 가속기를 위한 자원 관리 및 모니터링 시스템입니다.

---

## Submodules

| Submodule | Description |
|-----------|-------------|
| [rm_monitor](rm_monitor/) | LLM 추론 모니터링 스택 (vLLM + Prometheus + Grafana) |

---

## 주요 기능

### RM Monitor

- vLLM 메트릭 수집 (TTFT, TPOT, E2E, TPS)
- Prometheus + Grafana 대시보드
- DCGM Exporter를 통한 GPU 전력/사용률 모니터링
- Azure 트레이스 기반 트래픽 리플레이 도구

---

## Getting Started

```bash
# Clone with submodules
git clone --recursive https://github.com/ai-computing/ai-acc-rm.git
cd ai-acc-rm

# If already cloned
git submodule update --init --recursive
```

상세 사용법은 [rm_monitor/README.md](rm_monitor/README.md)를 참조하세요.

---

## Repository Structure

```
.
├── rm_monitor/    # LLM 추론 모니터링 스택
├── LICENSE
└── README.md
```

---

## License

This project is licensed under the BSD 3-Clause License - see the [LICENSE](LICENSE) file for details.
