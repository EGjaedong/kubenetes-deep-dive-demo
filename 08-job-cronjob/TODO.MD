# Job & CronJob Learning Plan

> Prerequisite: **Pod** basics  
> Job and CronJob run batch and scheduled workloads. Different from long-running apps (Deployment, StatefulSet, DaemonSet).

---

## Suggested Time (1–2h/night)

| Phase      | Estimated | Note                                         |
|------------|-----------|----------------------------------------------|
| Phase 1    | ~1 week   | Job basics, CronJob basics                   |
| Phase 2    | ~1 week   | Retries, parallelism, backoff                |
| Phase 3    | ~0.5–1 week | Optional, production patterns             |

---

## Phase 1: Core Basics (Do First)

### Job Basics
- [ ] Job vs Deployment: run to completion, then stop
- [ ] Create Job: `restartPolicy: OnFailure` or `Never`
- [ ] `kubectl get jobs`, `kubectl logs job/<name>`
- [ ] Job completes → Pod stays as `Completed` (until cleanup)

### CronJob Basics
- [ ] CronJob creates Jobs on a schedule (cron expression)
- [ ] Create CronJob: `schedule`, `jobTemplate`
- [ ] `kubectl get cronjobs`, observe triggered Jobs
- [ ] Cron syntax: `*/5 * * * *` (every 5 min), `0 2 * * *` (daily at 2am)

### Use Cases
- [ ] One-off: backup script, migration, report generation
- [ ] Recurring: daily sync, cleanup, health checks

---

## Phase 2: Intermediate (Return After Core Path)

### Job Advanced
- [ ] `completions`, `parallelism`: multiple Pods, run in parallel
- [ ] `activeDeadlineSeconds`: max runtime
- [ ] `backoffLimit`: retries on failure
- [ ] `ttlSecondsAfterFinished`: auto-cleanup completed Jobs

### CronJob Advanced
- [ ] `concurrencyPolicy`: `Forbid` / `Allow` / `Replace`
- [ ] `startingDeadlineSeconds`: schedule drift tolerance
- [ ] `suspend: true` to pause schedule
- [ ] Timezone (K8s 1.27+): `timeZone`

### Debugging
- [ ] Job stuck: check Pod events, image pull, resource limits
- [ ] CronJob not triggering: verify schedule, controller running
- [ ] Too many Jobs: check `successfulJobsHistoryLimit`, `failedJobsHistoryLimit`

---

## Phase 3: Advanced (Optional)

### Production Patterns
- [ ] Job as init/setup for StatefulSet (careful ordering)
- [ ] CronJob + ConfigMap/Secret for configurable scripts
- [ ] Alternatives: Argo Workflows, Tekton for complex DAGs

### Resource Management
- [ ] Jobs and cluster resources; avoid overloading
- [ ] Priority classes for critical batch jobs
