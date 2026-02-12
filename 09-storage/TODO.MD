# Storage (PV / PVC / StorageClass) Learning Plan

> Prerequisite: **Pod** volume basics (emptyDir, configMap, secret)  
> PV and PVC provide persistent storage that survives Pod restarts. Essential for databases and stateful apps.

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1.5–2 weeks | PV, PVC, binding, StorageClass           |
| Phase 2    | ~1–1.5 weeks | Dynamic provisioning, expand, reclaim     |
| Phase 3    | ~1 week   | Optional, CSI, production patterns           |

---

## Phase 1: Core Basics (Do First)

### PV & PVC Concept
- [ ] **PV (PersistentVolume)**: cluster-level storage resource (like a "disk")
- [ ] **PVC (PersistentVolumeClaim)**: Pod's request for storage (like "I need 10Gi")
- [ ] Binding: PVC finds a matching PV (or dynamic provisioning creates one)

### Basic Usage
- [ ] Create PV (e.g. hostPath for local dev, or cloud disk)
- [ ] Create PVC with `storage`, `accessModes`
- [ ] Pod uses PVC via `volumes` → `persistentVolumeClaim`
- [ ] Verify data persists across Pod delete/recreate

### StorageClass
- [ ] StorageClass: "type" of storage (fast SSD, cheap HDD, etc.)
- [ ] `storageClassName` in PVC; default StorageClass in cluster
- [ ] Dynamic provisioning: no manual PV, PVC triggers creation

### Access Modes
- [ ] `ReadWriteOnce` (RWO), `ReadOnlyMany` (ROX), `ReadWriteMany` (RWX)
- [ ] Which workloads need which (e.g. RWO for single-Pod DB)

---

## Phase 2: Intermediate (Return After Core Path)

### Dynamic Provisioning
- [ ] How Provisioner works (e.g. local-path, AWS EBS, etc.)
- [ ] PVC without PV: auto-created when StorageClass exists
- [ ] Default StorageClass: omit `storageClassName` to use it

### Volume Expansion
- [ ] `allowVolumeExpansion: true` in StorageClass
- [ ] Edit PVC `spec.resources.requests.storage` to resize
- [ ] Not all provisioners support expansion

### Reclaim Policy
- [ ] `Retain`: keep PV after PVC delete (manual cleanup)
- [ ] `Delete`: delete PV when PVC deleted (cloud storage)
- [ ] When to use each

### StatefulSet & volumeClaimTemplates
- [ ] Link to 04-stateful-set: each Pod gets its own PVC via template
- [ ] Naming: `<claimName>-<podName>`

---

## Phase 3: Advanced (Optional)

### CSI & Custom Storage
- [ ] Container Storage Interface (CSI): plugin model
- [ ] Common CSI drivers: NFS, Ceph, cloud providers
- [ ] Ephemeral volumes: inline CSI (K8s 1.16+)

### Production Patterns
- [ ] Backup/restore for PV data
- [ ] Snapshots (VolumeSnapshot)
- [ ] Multi-zone storage and scheduling
