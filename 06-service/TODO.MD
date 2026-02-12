# Service Learning Plan

> Prerequisite: **Pod**, **Deployment & ReplicaSet** basics  
> Service exposes Pods to other Pods or to the outside world. Learn after your first Deployment.

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1–1.5 weeks | Core Service types, label selection     |
| Phase 2    | ~1 week   | Deep dive, headless, session affinity        |
| Phase 3    | ~1 week   | Optional, production patterns               |

---

## Phase 1: Core Basics (Do First)

### Service Concept
- [ ] Why Service: Pods are ephemeral, IPs change; Service provides stable access
- [ ] Label selector: how Service finds Pods
- [ ] Endpoints: the bridge between Service and Pod IPs

### Service Types
- [ ] **ClusterIP** (default): internal-only, cluster DNS name
- [ ] **NodePort**: expose on each node's port (for dev / simple access)
- [ ] **LoadBalancer**: cloud provider LB (when supported)

### Basic Usage
- [ ] Create Service targeting Deployment Pods via labels
- [ ] DNS: `<service>.<namespace>.svc.cluster.local`
- [ ] `kubectl get svc`, `kubectl describe svc`, `kubectl get endpoints`

---

## Phase 2: Intermediate (Return After Core Path)

### Headless Service
- [ ] `clusterIP: None` for direct Pod DNS
- [ ] Use with StatefulSet (already seen in 04-stateful-set)
- [ ] When to use headless vs normal Service

### Advanced Selection & Traffic
- [ ] `sessionAffinity`: sticky sessions
- [ ] Multiple ports in one Service
- [ ] `externalTrafficPolicy`: Local vs Cluster

### Debugging Services
- [ ] Pod not receiving traffic: check labels, Endpoints, readiness
- [ ] `kubectl port-forward` for local testing
- [ ] `kubectl run` debug Pod for `curl` / `nslookup` from inside cluster

---

## Phase 3: Advanced (Optional)

### Production Patterns
- [ ] Service mesh intro (Istio, Linkerd) vs plain Service
- [ ] Multi-cluster Service (when needed)
- [ ] ExternalName Service for external DNS

### Network Policies (Teaser)
- [ ] Basic idea: restrict Pod-to-Pod traffic by namespace/labels
- [ ] Relation to Service: Policy can block even if Service allows
