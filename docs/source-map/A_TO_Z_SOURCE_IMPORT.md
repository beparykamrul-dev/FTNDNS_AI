# FTNDNS_AI — A–Z Production Source Import Map

Status: production-source import manifest.

## Source families

- Conversation to Code Compiler → `services/core-compiler/`, `apps/web/`, `apps/flutter/`, `infra/`
- Parser Engine → `services/parser/`
- Code Generator → `services/code-generator/`
- AI Engine → `services/ai/`
- Authentication → `services/auth/` + `services/iam/`
- Enterprise Project Manager → `services/project-manager/`
- Documentation → `services/documentation/`
- Cloud Infrastructure → `services/cloud/` + `infra/`
- Security Operations → `services/security/`
- Disaster Recovery → `services/backup/`
- Enterprise Search → `services/enterprise-search/`
- Billing / Payment → `services/billing/`, `services/payment/`
- ISP Network → `services/isp-network/`
- Customer → `services/customer/`
- MikroTik → `services/mikrotik/`
- OLT → `services/olt/`
- Fiber → `services/fiber/`
- GIS → `services/gis/`
- Telemetry → `services/telemetry/`
- Autonomous Network → `services/autonomous-network/`
- Smart NOC → `services/smart-noc/`
- AI Assistant → `services/ai-assistant/`
- Service Mesh → `services/service-mesh/`
- Event Bus → `services/event-bus/`
- API Security → `services/api-security/`
- Configuration → `services/configuration/`
- Asset Inventory → `services/asset-inventory/`
- Autonomous Intelligence 310–377 → `services/autonomous-expansion/`
- 378+ → roadmap only unless concrete source exists

## FTN.OS rules

1. FTN-owned interfaces and business/control logic are canonical.
2. External dependencies are allowed only at unavoidable protocol, hardware, or platform boundaries and must be isolated behind FTN adapters.
3. No duplicate service cores because of historical module numbering.
4. Web, Flutter, and AI Control Panel consume stable backend contracts.
5. AI execution is policy/permission/approval controlled and audited.
6. Stubs, no-op implementations, fixed-success health checks, and fake production results are not accepted as completed features.
7. Source import must preserve provenance and must not invent missing implementations.

## Canonical runtime

```text
Web / Flutter / AI Control Panel / Call Center
                    ↓
              FTN API Gateway
                    ↓
             Auth / IAM / Policy
                    ↓
                  FTN.OS
          ┌─────────┼─────────┐
          ↓         ↓         ↓
        AI       Network    Business
          ↓         ↓         ↓
          └─────────┼─────────┘
                    ↓
           Telemetry / Audit / DR
```

## Push gate

Before merging to `main`: deduplicate source, normalize module identity, extract real code from source documents, resolve stubs, normalize dependencies, wire backend/frontend contracts, run formatting/static checks/tests/builds, run secret/security checks, then perform live deployment verification.
