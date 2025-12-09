---
title: "Simpler Hybrid DNS Management with Delegation for Amazon Route 53 Resolver Endpoints"
date: ""
weight: 1
chapter: false
pre: " <b> 3.3. </b> "
---

# Networking & Content Delivery

## Simpler Hybrid DNS Management with Delegation for Amazon Route 53 Resolver Endpoints

By Tekena Orugbani | 25 Aug 2025

AWS announced that Route 53 Resolver endpoints now support DNS delegation. This feature allows you to delegate subdomain management between on‑premises DNS infrastructure and Route 53, simplifying hybrid DNS architectures that previously required customers to operate their own authoritative DNS servers.

Why delegation matters

Large organizations often run decentralized DNS: a central team manages the parent domain while individual teams manage subdomains. With delegation support, you can delegate a subdomain to Route 53 (or delegate it back to on‑premises), enabling unified private DNS namespaces across on‑premises and AWS without running additional authoritative DNS infrastructure.

Inbound delegation (on‑premises → AWS)

Inbound delegation lets on‑premises resolvers forward queries to Route 53 Resolver endpoints and receive referrals for subdomains hosted in private hosted zones in AWS. Typical steps:

1. Create a private hosted zone for the subdomain (for example `aws.healthtech.example.com`) and associate it with the VPC.
2. Create records in the private hosted zone for the applications.
3. Create an inbound resolver delegation endpoint and record its IP addresses.
4. On the on‑premises DNS, add an NS record for the delegated subdomain and ensure the NS name resolves to the resolver endpoint IPs.

Outbound delegation (AWS → on‑premises)

Outbound delegation enables VPC resources to resolve names hosted on on‑premises authoritative servers. Steps include creating an outbound resolver endpoint, adding an NS record in the parent zone that points to on‑premises authoritative servers, and creating a delegation rule associated with the VPC. If the authoritative server FQDN is in‑zone, create a glue A record in the private hosted zone; otherwise create a forwarding rule for the FQDN.

When both parent and child zones remain on‑premises

If both the parent and subdomain are hosted on‑premises, you can still use outbound delegation to enable Route 53 Resolver to follow the delegation chain to the on‑premises authoritative server and return authoritative answers to VPC clients.

Benefits

- Reduces operational overhead by removing the need for customer‑managed authoritative DNS servers in many hybrid scenarios.
- Simplifies delegation management: a single delegation rule can cover many subdomains.
- Integrates into the Resolver pricing model (hourly and per‑query); there is no separate delegation charge.

See the Route 53 documentation on inbound and outbound delegation for implementation details and pricing guidance.

Author

Tekena Orugbani — Senior Specialist Solutions Architect at AWS, specializing in Microsoft workloads and hybrid connectivity.
