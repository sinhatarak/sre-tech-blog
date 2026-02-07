---
title: "Kubernetes Networking for SREs"
date: 2026-02-07
tags: ["kubernetes", "networking", "cni", "calico", "cilium", "sre"]
categories: ["Kubernetes"]
draft: false
---

## Why Kubernetes Networking Matters for SREs

Most production outages in Kubernetes are not caused by code —
they are caused by **network assumptions**.

This post covers:
- Pod-to-Pod networking fundamentals
- Service networking & kube-proxy
- CNI plugins (Calico vs Cilium)
- NetworkPolicies in real production
- Common outage patterns SREs see

---

## Pod-to-Pod Networking

Every pod receives its own IP address.
Kubernetes assumes **flat networking**:
- No NAT between pods
- Direct reachability across nodes

This is implemented by the CNI plugin.

### Common SRE failure modes
- MTU mismatch
- Encapsulation overhead
- Broken routing between nodes

---

## Service Networking

Services provide stable virtual IPs backed by kube-proxy.

Modes:
- iptables
- IPVS

From an SRE perspective:
- iptables scales poorly at high service counts
- IPVS is more predictable under load

