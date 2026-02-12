# Pod Learning Plan

> Learning order: **Pod** → Deployment & RS → StatefulSet → DaemonSet  
> After finishing basics of all four, come back for intermediate/advanced phases.

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~2–4 weeks | Finish before moving to Deployment & RS      |
| Phase 2    | ~1.5–2.5 weeks | Return after DaemonSet basics            |
| Phase 3    | ~1–1.5 weeks | Optional, for practice and interviews    |

---

## Phase 1: Core Basics (Do First)

Master these before Deployment; otherwise it will feel like using things without understanding them.

### Pod Basics
- [ ] Create, inspect, delete Pods; basic lifecycle
- [ ] `kubectl run` vs `kubectl apply -f`
- [ ] Pod states: `Pending`, `Running`, `Succeeded`, `Failed`

### Container Config
- [ ] `image`, `command`, `args`
- [ ] `env` / `envFrom` for environment variables
- [ ] `resources`: `requests` / `limits` basics

### ConfigMap & Secret Basics
- [ ] Create ConfigMap and use it in Pods (`volume` or `env`)
- [ ] Create Secret and use it in Pods
- [ ] Why configuration and secrets are kept separate

### Volume Basics (Common Types)
- [ ] `emptyDir`: ephemeral storage, shared between containers
- [ ] `configMap`: mount ConfigMap as dir/file
- [ ] `secret`: mount Secret as dir/file

### Health Check Probes
- [ ] Liveness Probe: restart container on failure
- [ ] Readiness Probe: skip traffic until ready

---

## Phase 2: Intermediate (Return After DaemonSet)

Deeper Pod topics; easier to grasp after seeing the full workload picture.

### Volumes Deep Dive
- [ ] `hostPath`: mount host path (use with caution)
- [ ] PersistentVolumeClaim (PVC): persistent storage claims
- [ ] Other types: `nfs`, `projected`, etc.

### Pod Namespace Sharing
- [ ] PID namespace sharing (`shareProcessNamespace: true`)
- [ ] IPC namespace sharing
- [ ] Network namespace sharing (multiple containers, shared network)

### Init Container & Sidecar
- [ ] Init Container: runs before main container(s)
- [ ] Sidecar pattern: helper container alongside main container

### Scheduling & Resources
- [ ] `nodeSelector`: node selection
- [ ] `hostAliases`: custom `/etc/hosts`
- [ ] Resource limits and reservations

---

## Phase 3: Advanced (Optional)

For production use and interview prep.

### Security & Constraints
- [ ] Pod `securityContext`
- [ ] Pod anti-affinity / `topologySpreadConstraints`
- [ ] Pod Disruption Budget (PDB)

### Multi-Container Patterns
- [ ] Design patterns for multi-container Pods
- [ ] Inter-container communication (localhost, shared volumes)
