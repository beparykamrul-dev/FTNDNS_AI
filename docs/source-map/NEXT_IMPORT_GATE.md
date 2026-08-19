# Next Import Gate

## Generator → Filesystem Builder

The next source integration gate is the production boundary between generated artifacts and filesystem/deployment operations.

Required properties:

- deterministic artifact generation
- path traversal protection
- allowed-root enforcement
- atomic writes
- manifest and content hashes
- conflict detection
- rollback metadata
- permission/policy checks
- audit records
- real validation before deployment

Incomplete source behavior must remain marked as incomplete until implemented and tested. In particular, an empty ZIP/export, unconditional validation success, or no-op deployment is not a production result.

## Runtime path

```text
Plan
  -> Generator
  -> Artifact Set
  -> Filesystem Policy
  -> Atomic Write
  -> Manifest/Hash
  -> Validator
  -> Build/Test
  -> Security Gate
  -> Audit
  -> Deployment
```

## Repository rule

This file is an import gate, not a claim that the complete backend/frontend/live deployment has already been implemented. The `main` branch must only receive verified production source.
