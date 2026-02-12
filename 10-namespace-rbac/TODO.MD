# Namespace & RBAC Learning Plan

> Prerequisite: **Pod**, **Deployment**, **Service** basics  
> Namespace and RBAC provide multi-tenancy and access control. Learn when you need to share or secure a cluster.

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1 week   | Namespace, ResourceQuota, LimitRange         |
| Phase 2    | ~1–1.5 weeks | ServiceAccount, Role, RoleBinding       |
| Phase 3    | ~1 week   | Optional, ClusterRole, production patterns    |

---

## Phase 1: Core Basics (Do First)

### Namespace Basics
- [ ] Namespace: logical boundary for resources (Pods, Services, etc.)
- [ ] Default namespaces: `default`, `kube-system`, `kube-public`
- [ ] Create namespace: `kubectl create namespace <name>`
- [ ] Resources are namespaced (mostly) or cluster-scoped
- [ ] `kubectl get pods -n <namespace>`, `-A` for all

### ResourceQuota
- [ ] Limit total resources per namespace (CPU, memory, PVC count, etc.)
- [ ] Create ResourceQuota, verify Pod creation blocked when over quota
- [ ] Scoped quotas: by compute resources, object counts

### LimitRange
- [ ] Default and max/min for Pod/Container resources in namespace
- [ ] Automatically set `requests`/`limits` when not specified
- [ ] Create LimitRange, create Pod without resources, observe defaults

---

## Phase 2: Intermediate (Return After Core Path)

### ServiceAccount
- [ ] ServiceAccount: identity for processes running in Pods
- [ ] Default SA per namespace; each Pod has one
- [ ] Use SA for API access (e.g. from app or CI)
- [ ] `automountServiceAccountToken: false` when not needed

### Role & RoleBinding
- [ ] **Role**: permissions in one namespace (e.g. "get pods")
- [ ] **RoleBinding**: bind Role to user/group/ServiceAccount
- [ ] Create Role + RoleBinding, test with `kubectl --as` or SA
- [ ] `kubectl auth can-i get pods -n X --as=user`

### ClusterRole & ClusterRoleBinding
- [ ] ClusterRole: cluster-wide or for non-namespaced resources
- [ ] ClusterRoleBinding: bind ClusterRole to subject
- [ ] When to use Role vs ClusterRole
- [ ] Built-in: `view`, `edit`, `admin`, `cluster-admin`

---

## Phase 3: Advanced (Optional)

### Production Patterns
- [ ] Per-team or per-env namespaces with quotas
- [ ] Least privilege: minimal Role for app SA
- [ ] Audit: who did what (audit logs, not covered in detail here)

### NetworkPolicy (Teaser)
- [ ] Restrict Pod-to-Pod traffic by namespace/labels
- [ ] Different from RBAC (RBAC = API access; NetworkPolicy = network)
- [ ] Basic Ingress/Egress rules
