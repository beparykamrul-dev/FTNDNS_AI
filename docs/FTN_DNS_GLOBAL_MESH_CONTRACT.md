# FTN DNS Global Mesh Contract

## Scope

FTNDNS is the DNS mesh domain of FTN. Server/application service-mesh responsibilities remain separate.

## Core functions

- Authoritative DNS
- Recursive/cache DNS where permitted
- Anycast/health-based node selection
- Provider DNS federation through adapters
- DNSSEC and certificate-aware service endpoints
- DNS health, latency and failover
- Node/service registry integration

## Provider adapter model

Each provider has a versioned profile containing only supported/public/authorized interfaces:

- DNS API
- edge/CDN interface
- health checks
- TLS/CA trust profile
- telemetry interface
- credentials reference (never the secret itself)
- rate limits
- license/version metadata

## DNS engines

PowerDNS, Hickory DNS, CoreDNS, Technitium DNS, Unbound and dnsdist may be selected by workload. The control plane must not assume every engine is active on every node.

## Node lifecycle

`DISCOVER -> REGISTER -> CONFIGURE -> VALIDATE -> PUBLISH -> HEALTH CHECK -> FAILOVER -> RECONCILE`

New DNS providers/nodes enter the registry through the same contract; FTN does not require rebuilding the existing familytimenet.com DNS architecture.

## Security

DNS administration uses FTN PKI/mTLS where applicable. Provider trust chains remain provider-specific. Private CA keys are never imported into the repository or control plane configuration.

## Traffic separation

DNS Global Mesh carries DNS traffic and DNS control metadata. Application/backend traffic is handled by the FTN Server/Service Mesh. The control plane provides the bridge through service discovery and health state.

## Resilience

DNS nodes are independently health-checked. Failed nodes are removed from eligible serving state and restored only after successful reconciliation and health verification.
