# StatefulSet Learning Plan

> Prerequisite: **Pod**, **Deployment & ReplicaSet** basics  
> Learning order: Pod → Deployment & RS → **StatefulSet** → DaemonSet

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1.5–2.5 weeks | Finish before DaemonSet                 |
| Phase 2    | ~1.5–2.5 weeks | Return after DaemonSet basics           |
| Phase 3    | ~1–1.5 weeks | Optional, for stateful apps in practice |

---

## Phase 1: Core Basics (Do First)

### StatefulSet vs Deployment
- [ ] Stateless vs stateful: can Pods be replaced freely?
- [ ] Stable network identity: `<pod-name>.<headless-service>.<ns>.svc.cluster.local`
- [ ] Ordered create, delete, scale

### Headless Service Basics
- [ ] Meaning of `clusterIP: None`
- [ ] Headless Service returns Pod IPs, not a single ClusterIP
- [ ] Link to StatefulSet via `serviceName`

### StatefulSet Basics
- [ ] Create StatefulSet, observe Pod names (`<name>-0`, `-1`, `-2`...)
- [ ] Scale: `kubectl scale statefulset <name> --replicas=N`
- [ ] Observe ordered startup and termination

### Stable Storage Overview
- [ ] Why stateful apps need fixed storage per Pod
- [ ] High-level idea of `volumeClaimTemplates` (details in Phase 2)

---

## Phase 2: Intermediate (Return After DaemonSet)

### VolumeClaimTemplates Deep Dive
- [ ] `volumeClaimTemplates` auto-creates PVC per Pod
- [ ] PVC naming: `<volumeClaimTemplateName>-<podName>`
- [ ] PVC creation and retention on scale up/down

### Typical Stateful Use Cases
- [ ] Databases: MySQL, PostgreSQL primary-replica
- [ ] Distributed systems: Redis Cluster, Kafka, Zookeeper
- [ ] Combining stable network + stable storage

### Update & Scale Strategies
- [ ] `updateStrategy`: `RollingUpdate`, `OnDelete`
- [ ] Scale order: expand then shrink, or vice versa
- [ ] Partitioned updates (`partition`)

### Headless Service Advanced
- [ ] Pod discovery and leader election
- [ ] Hands-on DNS resolution with StatefulSet

---

## Phase 3: Advanced (Optional)

### Production Practices
- [ ] Backup and restore for StatefulSet
- [ ] Failover and recovery for stateful apps
- [ ] Relation to Operators (e.g. MySQL Operator)

### Troubleshooting
- [ ] Common causes of `Creating` / `Pending`
- [ ] PVC binding failures, StorageClass issues
