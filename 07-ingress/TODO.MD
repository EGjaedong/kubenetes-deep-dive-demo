# Ingress Learning Plan

> Prerequisite: **Service** basics  
> Ingress manages external HTTP/HTTPS access to Services. Learn after Service.

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1–1.5 weeks | Ingress resource, Ingress Controller     |
| Phase 2    | ~1–1.5 weeks | TLS, annotations, path rules               |
| Phase 3    | ~1 week   | Optional, production setup                  |

---

## Phase 1: Core Basics (Do First)

### Ingress Concept
- [ ] Why Ingress: one LB for many Services, host/path-based routing
- [ ] Ingress Controller: required to fulfill Ingress (e.g. ingress-nginx, traefik)
- [ ] Ingress vs Service: Ingress sits in front of Services

### Basic Setup
- [ ] Install an Ingress Controller (e.g. ingress-nginx)
- [ ] Create Ingress resource: `host`, `path`, `backend` (Service)
- [ ] Access app via host or path (e.g. `curl http://myapp.local/hi`)

### Common Annotations
- [ ] `ingress-nginx` (or your controller) path rewrite, proxy settings
- [ ] `cert-manager` for TLS (covered in Phase 2)

---

## Phase 2: Intermediate (Return After Core Path)

### TLS/HTTPS
- [ ] Add TLS section to Ingress spec
- [ ] cert-manager for automatic certificates (Let's Encrypt)
- [ ] HTTP → HTTPS redirect

### Advanced Routing
- [ ] Multiple hosts and paths in one Ingress
- [ ] Default backend
- [ ] Path type: `Prefix` vs `Exact` vs `ImplementationSpecific`

### Debugging
- [ ] Ingress Controller logs and events
- [ ] Wrong host/path → 404; backend not ready → 502
- [ ] Test with `curl -H "Host: ..."`

---

## Phase 3: Advanced (Optional)

### Production Practices
- [ ] Ingress Controller tuning (replicas, resources)
- [ ] Rate limiting, WAF integration
- [ ] Canary / A/B routing via annotations or controller features

### Alternatives
- [ ] Service LoadBalancer for simple single-app exposure
- [ ] Gateway API (newer, more flexible than Ingress)
