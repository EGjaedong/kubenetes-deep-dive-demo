# Deployment & ReplicaSet Learning Plan

> Prerequisite: **Pod** basics (lifecycle, volumes, CM/Secret, probes)  
> Learning order: Pod → **Deployment & RS** → StatefulSet → DaemonSet

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1.5–2.5 weeks | Finish before StatefulSet              |
| Phase 2    | ~1.5–2.5 weeks | Return after DaemonSet basics           |
| Phase 3    | ~1–1.5 weeks | Optional, for production and interviews |

---

## Phase 1: Core Basics (Do First)

### ReplicaSet Basics
- [ ] ReplicaSet’s role: manage a set of Pod replicas, keep desired count
- [ ] Meaning of `selector` and `replicas`
- [ ] ReplicaSet vs Pod (you usually don’t manage RS directly)

### Deployment Basics
- [ ] Deployment manages ReplicaSet, ReplicaSet manages Pods
- [ ] Create Deployment: `spec.template` is the Pod template
- [ ] Scale: `kubectl scale` or change `replicas`

### Rollout & Rollback
- [ ] Change `image` or `template` to trigger rollout
- [ ] `kubectl rollout status`, `kubectl rollout history`
- [ ] `kubectl rollout undo` for rollback

### Relation to Service
- [ ] How Deployment Pods are selected by Service
- [ ] Connect Deployment and Service via labels

---

## Phase 2: Intermediate (Return After DaemonSet)

### Update Strategy Deep Dive
- [ ] `strategy.type`: `RollingUpdate` vs `Recreate`
- [ ] `maxSurge`, `maxUnavailable` and tuning
- [ ] Canary and blue-green deployment approaches

### Rollout & Observability
- [ ] `kubectl rollout pause` / `resume`
- [ ] Use with HPA (Horizontal Pod Autoscaler)
- [ ] Deployment events and troubleshooting

### Revisions & Rollback
- [ ] Rollback to a specific `revision`
- [ ] How old and new ReplicaSets hand off

---

## Phase 3: Advanced (Optional)

### Production Practices
- [ ] Deployment and ConfigMap/Secret change behavior
- [ ] Zero-downtime deployments with health checks
- [ ] Fit with GitOps / Argo CD

### Resources & Scheduling
- [ ] Resource limits in Deployment template and cluster scheduling
- [ ] PodDisruptionBudget with Deployment
