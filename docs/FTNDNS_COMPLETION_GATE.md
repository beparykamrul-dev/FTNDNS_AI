# FTNDNS Completion Gate

FTNDNS is complete only when DNS nodes and provider adapters can be registered, reconciled, health-checked and safely failed over.

## DNS engines

PowerDNS, Hickory DNS, CoreDNS, Technitium DNS, Unbound and dnsdist are workload-selectable adapters. A node does not need every engine installed.

## Provider model

Each provider is represented by a versioned adapter and trust profile. Only documented/public/authorized interfaces are used. Provider private credentials and private CA keys never enter source control.

## Lifecycle

`DISCOVER -> REGISTER -> CONFIGURE -> VALIDATE -> PUBLISH -> HEALTH CHECK -> FAILOVER -> RECONCILE`

## Security

DNS administration is protected by the FTN trust boundary, with mTLS/PKI where appropriate. DNSSEC and provider-specific trust chains are preserved where supported.

## Acceptance

- configuration is reproducible
- health checks are active
- failed nodes leave serving state
- recovered nodes re-enter only after verification
- audit events are emitted
- new DNS providers do not require rebuilding the existing FTN DNS architecture
