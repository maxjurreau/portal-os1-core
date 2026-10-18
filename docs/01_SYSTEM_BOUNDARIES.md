# 01 // SYSTEM BOUNDARIES & ISOLATION RINGS

## 1. Zero-Cost Operational Guardrails ($0.00/mo)

To operate permanently without triggering Cloudflare billing thresholds, Portal-OS1 enforces strict daily resource caps:

| Component | Daily Free Threshold | Portal-OS1 Safety Allocation |
| :--- | :--- | :--- |
| **Worker Requests** | 100,000 / day | Max 80,000 / day (20% reserve) |
| **D1 Database Reads** | 5,000,000 / day | Max 4,000,000 / day |
| **D1 Database Writes** | 100,000 / day | Max 75,000 / day (Batched writes) |
| **Memory Limit** | 128 MB per worker | Max 2 MB heap cap per process |

---

## 2. Four-Tier Isolation Rings

```text
  [Ring 3: Web-Based UI & Client PWA]
      └── [Ring 2: Semantic Firewall & Intent Router]
              └── [Ring 1: Agent Scheduler & IPC Bus]
                      └── [Ring 0: Durable Object Microkernel & D1 Core]
