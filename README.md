# Kubernetes Deep Dive

A hands-on repository for learning Kubernetes core concepts through YAML examples and guided TODO plans.

---

## Learning Roadmap

All estimates assume **1–2 hours per night**. Finish Phase 1 of each module in order; return to Phase 2/3 after completing the core path.

```
┌─────────────────────────────────────────────────────────────────────────────────────┐
│  PHASE A: Workloads (foundation)                                                    │
├─────────────────────────────────────────────────────────────────────────────────────┤
│  01-first-demo  →  02-pod  →  03-deployment  →  04-stateful-set  →  05-daemon-set   │
│  (quick start)     ~2–4w        ~1.5–2.5w        ~1.5–2.5w           ~1–1.5w        │
│                                                                                     │
│  Then: return to 02–05 for Phase 2 (intermediate) topics                            │
└─────────────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│  PHASE B: Networking & Exposure                                             │
├─────────────────────────────────────────────────────────────────────────────┤
│  06-service  →  07-ingress                                                  │
│  ~1–1.5w        ~1–1.5w                                                     │
│  (expose Pods)   (HTTP/HTTPS routing)                                       │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│  PHASE C: Batch, Storage, Security                                          │
├─────────────────────────────────────────────────────────────────────────────┤
│  08-job-cronjob  →  09-storage  →  10-namespace-rbac                        │
│  ~1w                 ~1.5–2w        ~1–1.5w                                 │
│  (batch/scheduled)   (PV/PVC)        (multi-tenant, RBAC)                   │
└─────────────────────────────────────────────────────────────────────────────┘
                                    │
                                    ▼
┌─────────────────────────────────────────────────────────────────────────────┐
│  PHASE D: Practical Skills (learn alongside)                                │
├─────────────────────────────────────────────────────────────────────────────┤
│  11-kubectl-debugging                                                       │
│  ~1w (Phase 1), then revisit as needed                                      │
└─────────────────────────────────────────────────────────────────────────────┘
```

### Summary Table

| # | Module | Focus | Prerequisite | Phase 1 Time |
|---|--------|-------|--------------|--------------|
| 01 | first-demo | Quick start | None | — |
| 02 | pod | Containers, volumes, CM/Secret, probes | None | ~2–4 weeks |
| 03 | deployment-and-replica-set | Stateless apps, rollout | Pod | ~1.5–2.5 weeks |
| 04 | stateful-set | Stateful apps, stable network/storage | Deployment | ~1.5–2.5 weeks |
| 05 | daemon-set | One Pod per node | StatefulSet | ~1–1.5 weeks |
| 06 | service | Expose Pods, ClusterIP/NodePort/LB | Deployment | ~1–1.5 weeks |
| 07 | ingress | HTTP/HTTPS routing | Service | ~1–1.5 weeks |
| 08 | job-cronjob | Batch & scheduled workloads | Pod | ~1 week |
| 09 | storage | PV, PVC, StorageClass | Pod volumes | ~1.5–2 weeks |
| 10 | namespace-rbac | Multi-tenancy, access control | Deployment, Service | ~1–1.5 weeks |
| 11 | kubectl-debugging | Commands, troubleshooting | — (start anytime) | ~1 week |

---

## Directory Structure

```
01-first-demo/           # Quick start, basic manifests
02-pod/                  # Pod lifecycle, volumes, CM/Secret, probes
03-deployment-and-replica-set/
04-stateful-set/
05-daemon-set/
06-service/              # Service types, DNS, exposure
07-ingress/              # Ingress Controller, TLS, routing
08-job-cronjob/          # Job, CronJob
09-storage/              # PV, PVC, StorageClass
10-namespace-rbac/       # Namespace, ResourceQuota, RBAC
11-kubectl-debugging/    # kubectl, debugging workflows
```

Each module has a **TODO.MD** with phased tasks (Phase 1: basics, Phase 2: intermediate, Phase 3: advanced).

---

## Quick Start

1. **Connect to a cluster:**
   ```bash
   kubectl cluster-info
   ```

2. **Apply manifests:**
   ```bash
   kubectl apply -f 01-first-demo/first-demo.yaml
   kubectl apply -f 02-pod/pods-volumn-config-demo.yaml
   # etc.
   ```

3. **Inspect resources:**
   ```bash
   kubectl get pods -A
   kubectl get svc
   ```

4. **Follow the TODO.MD** in each module for a structured learning path.
