---
title: "Kubernetes Network for SREs"
date: 2026-02-07
tags: ["kubernetes", "network", "CNI", "calico", "cilium", "networkpolicy", "sre"]
---

## Why this matters
In production Kubernetes clusters, unrestricted pod-to-pod traffic increases blast radius.

## How NetworkPolicy works
- Enforced by CNI
- Namespace & Pod selectors
- Default allow vs default deny

## Common SRE mistakes
- Assuming policies work without CNI support
- Forgetting egress rules

## Debugging checklist
```bash
kubectl describe networkpolicy
kubectl exec -it busybox -- wget <service>

