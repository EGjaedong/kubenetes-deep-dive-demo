# DaemonSet Learning Plan

> Prerequisite: **Pod**, **Deployment & RS**, **StatefulSet** basics  
> Learning order: Pod → Deployment & RS → StatefulSet → **DaemonSet**

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1–1.5 weeks | Completes the four workload basics      |
| Phase 2    | ~1–1.5 weeks | Then return to Pod / Deployment etc.   |
| Phase 3    | ~1 week   | Optional, for production Agent deployment   |

---

## Phase 1: Core Basics (Do First)

### DaemonSet Concept & Use Cases
- [ ] One Pod per node (or per node matching `nodeSelector`)
- [ ] Typical cases: log collection, monitoring Agent, network plugin, storage driver
- [ ] vs Deployment: not “N replicas”, but “one per node”

### Create & Basic Ops
- [ ] Create DaemonSet: YAML structure (like Deployment, no `replicas`)
- [ ] `kubectl get daemonset`, `kubectl describe daemonset`
- [ ] New nodes: DaemonSet automatically adds Pods

### Relation to Nodes
- [ ] DaemonSet and node lifecycle (node add/remove)
- [ ] `nodeSelector`: run only on selected nodes

---

## Phase 2: Intermediate (After Four Basics)

### Node Selection & Taint Toleration
- [ ] `nodeSelector`: select by node labels
- [ ] `tolerations`: tolerate taints (e.g. `NoSchedule` on Master)
- [ ] Common config to run DaemonSet on Master

### Update Strategy
- [ ] `updateStrategy.type`: `RollingUpdate` / `OnDelete`
- [ ] Batching with `maxUnavailable` during rollout

### Typical Use Cases in Practice
- [ ] Deploy log collectors (Filebeat, Fluentd)
- [ ] Deploy monitoring agents (Node Exporter)
- [ ] DaemonSet access to host resources (`hostPath`, `hostNetwork`, etc.)

---

## Phase 3: Advanced (Optional)

### Production Practices
- [ ] DaemonSet resource limits and node planning
- [ ] Multiple DaemonSets and resource contention
- [ ] DaemonSet and Pod security policies

### Troubleshooting & Optimization
- [ ] Common reasons DaemonSet Pods can’t schedule
- [ ] Working with `CriticalAddonsOnly` taint
