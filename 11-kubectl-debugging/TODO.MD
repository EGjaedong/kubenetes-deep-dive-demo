# kubectl & Debugging Learning Plan

> Can be learned **alongside** other modules.  
> Practical skills for daily use: inspect, debug, and troubleshoot.

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1 week   | Essential commands, can start immediately    |
| Phase 2    | ~1 week   | Debugging workflows, return as needed        |
| Phase 3    | Ongoing   | Optional, advanced tips                      |

---

## Phase 1: Core Basics (Do First)

### Essential kubectl Commands
- [ ] `kubectl get` / `kubectl describe` for pods, deployments, svc, etc.
- [ ] `-o wide`, `-o yaml`, `-o json`, `-o name`
- [ ] `kubectl apply -f`, `kubectl delete -f`
- [ ] `kubectl logs <pod>` / `kubectl logs -f` (follow)
- [ ] `kubectl exec -it <pod> -- /bin/sh` (or bash)
- [ ] `kubectl get events -A` or `-n <ns>` (sorted by time)

### Context & Config
- [ ] `kubectl config get-contexts` (list clusters)
- [ ] `kubectl config use-context <name>` (switch cluster)
- [ ] `~/.kube/config` structure (optional peek)
- [ ] `kubectl cluster-info` (verify connectivity)

### Quick Debugging
- [ ] Pod Pending: check `kubectl describe pod` → Events (scheduling, image pull)
- [ ] Pod CrashLoopBackOff: `kubectl logs` (previous: `--previous`)
- [ ] Service not routing: check Endpoints, Pod labels, readiness

---

## Phase 2: Intermediate (Return When Needed)

### Debugging Workflows
- [ ] Run a temporary debug Pod: `kubectl run debug --rm -it --image=busybox -- sh`
- [ ] `kubectl port-forward svc/<name> 8080:80` for local testing
- [ ] `kubectl top nodes` / `kubectl top pods` (metrics, if enabled)
- [ ] `kubectl cp <pod>:/path /local` (copy files)
- [ ] `kubectl debug` (ephemeral container, K8s 1.18+)

### Logs & Tracing
- [ ] Multi-container Pod: `kubectl logs <pod> -c <container>`
- [ ] Log aggregation ideas (outside K8s: Loki, EFK)
- [ ] Trace request flow: Client → Ingress → Service → Pod

### Common Failure Modes
- [ ] ImagePullBackOff: wrong image, private registry auth
- [ ] OOMKilled: increase memory limit or fix leak
- [ ] Node not ready: kubelet, network, disk pressure
- [ ] Evicted: resource pressure, check `kubectl describe node`

---

## Phase 3: Advanced (Optional)

### Productivity
- [ ] kubectl aliases (e.g. `k`, `kgp`, `kdp`)
- [ ] kubectx / kubens for context and namespace switching
- [ ] k9s or similar TUI (optional)
- [ ] Shell completion: `kubectl completion zsh`

### Deep Debugging
- [ ] `kubectl get events` with custom columns
- [ ] API server audit logs (cluster-admin)
- [ ] crictl / nerdctl on nodes (container runtime level)
