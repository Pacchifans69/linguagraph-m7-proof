# LinguaGraph M7 external proof preparation

This independent repository contains proof infrastructure only for
**M7 — Alignment Mutation Concurrency Hardening**. It does not modify the
LinguaGraph Product repository and it is intentionally separate from the
historical `Pacchifans69/linguagraph-m6-proof` evidence repository.

## Status

```text
checkpoint:        M7
exception:         M7-EXI-01 — Alibaba ECS Hosted Gate 2 Proof
stage:             P1 — proof harness preparation
proof execution:   NOT AUTHORIZED / NOT EXECUTED
run authorization: NOT ISSUED
Gate 2 result:     NOT ESTABLISHED
```

This repository was prepared only after the exact-candidate canonical GitHub
Actions attempt failed before all repository-defined steps:

```text
Product run:       #124 / 35422565869
Product head:      854137cd498569f7c3d770d3b82be51042080edd
job steps:         []
log retrieval:     BlobNotFound
classification:    provider / pre-step failure
semantic evidence: none
```

M7-EXI-01 is an **execution-environment exception only**. It waives no M7
semantic requirement.

## Exact Product binding

```text
repository:     Pacchifans69/LinguaGraph
branch:         m7-alignment-mutation-concurrency-hardening
candidate SHA:  854137cd498569f7c3d770d3b82be51042080edd
candidate tree: 7b5306fbd37a158cd1fb688fd050d20cfc5aec74
unique parent:  945d9d4bbe081eedd11088315b5007d80d8910d4
frozen main:    3f08eca99f03180eef9dcd7008287892f0e6501d
Alembic head:   0006
```

The provider-neutral core fails closed unless the remote Product branch, remote
main, detached candidate checkout, tree, unique parent, and frozen-main
ancestry all match these exact values.

## Technical basis

The harness architecture was adapted from the reviewed M6 proof source:

```text
repository: Pacchifans69/linguagraph-m6-proof
source SHA: 274aae9f86fb8da9571edf1e197696035d6fb4a3
source tree: b331cd16642ba2c293bb6b83d2310f85b2af35e6
```

The M6 proof repository is historical evidence and is not modified by M7.

M7 deliberately uses a new namespace and independent state:

```text
proof repository:       Pacchifans69/linguagraph-m7-proof
evidence env:           M7_PROOF_EVIDENCE_DIR
run auth env:           M7_PROOF_RUN_AUTHORIZATION
host state env:         M7_PROOF_HOST_STATE
default host state:     ~/.local/state/linguagraph-m7-proof
PostgreSQL container:   linguagraph-m7-proof-postgres
authorization namespace:
  M7-EXI-01-RUN-<approved-proof-sha-prefix>-<nonce>
```

No M6 run token is valid in this harness.

## Harness architecture

```text
scripts/run-m7-proof-core.sh
  provider-neutral semantic Gate 2 core

scripts/run-m7-proof-alibaba-ecs.sh
  Alibaba ECS provider / identity / one-shot authorization adapter
```

The core owns:

- exact Product candidate/tree/parent/frozen-main guards;
- clean detached Product checkout;
- Python 3.13;
- Node 24.17.0;
- uv 0.12.10;
- PostgreSQL 18;
- frozen dependency installation;
- empty-database migration to Alembic `0006`;
- `alembic current` and `alembic check`;
- full real-PostgreSQL pytest;
- explicit JUnit presence checks for the M7 concurrency matrix;
- zero skipped/xfailed/xpassed/deselected backend tests;
- frontend lint/typecheck/Vitest/build;
- retained M0–M6 Playwright regression with `--retries=0`;
- dependency hash integrity;
- candidate clean-tree integrity;
- disposable database cleanup;
- final remote Product guards;
- fail-closed `outcome.txt` and artifact manifest.

The Alibaba adapter owns:

- canonical proof repository origin and exact proof-main SHA guard;
- independent M7 one-shot run authorization;
- persistent spent-token hashes outside the worktree;
- Alibaba IMDS token-mode identity verification;
- signed instance identity document / PKCS7 capture;
- exact expected instance/region/zone/type/image guard;
- minimal Docker bootstrap when required;
- deterministic proof-artifact archive and external SHA-256.

## Required M7 concurrency evidence

The full backend suite must contain and execute all of the following exact test
cases:

```text
test_c_r01_patch_patch_same_group_is_serial_equivalent
test_c_r01_partial_patch_omission_preserves_other_serialized_field
test_c_r02_patch_delete_same_group_has_stable_serial_outcome
test_c_r03_delete_delete_same_group_is_ok_plus_not_found
test_c_r04_create_vs_force_delete_text_version
test_c_r05_patch_vs_force_delete_text_version
test_c_r06_delete_alignment_vs_force_delete_text_version
test_c_r07_create_vs_replace_content_uses_one_canonical_text
test_c_r08_shared_span_survives_competing_topology_mutation
test_c_r09_true_orphans_are_removed_under_competing_mutation
test_c_a01_alignment_mutation_vs_delete_parallel_document_audit
test_c_a01_delete_parallel_document_first_yields_not_found
test_c_a02_alignment_mutation_vs_delete_project_audit
test_c_a02_delete_project_first_yields_not_found
test_cross_document_input_is_rejected_before_text_version_lock
```

The core writes the complete pytest JUnit XML as retained evidence and fails
closed if any required case is absent.

## Preparation-time expected suite counts

These values are guards for the exact bound Product tree, not proof results:

```text
pytest:     602 passed
Vitest:     519 passed
Playwright: 32 passed
```

A formal hosted run must still actually produce these results with no required
test skipped or filtered.

## Provider boundary

The Alibaba adapter contains the previously measured ECS identity values as
execution guards:

```text
instance id:   i-j6c13vpnkuq6xbbhyxzw
region:        cn-hongkong
zone:          cn-hongkong-d
instance type: ecs.g9i.xlarge
image:         ubuntu_24_04_x64_20G_alibase_20260828.vhd
```

Their presence in source does **not** assert that the instance is currently
running, reachable, or unchanged. Stage P3 must separately authorize provider
restart/access and freshly verify provider identity before any formal proof
authorization is issued.

## One-shot authorization

A formal invocation requires all of:

1. this proof repository checked out cleanly on `main`;
2. `APPROVED_PROOF_SHA` equal to the exact Human-approved proof commit;
3. remote proof `main` equal to that same SHA;
4. a fresh token matching
   `M7-EXI-01-RUN-<approved-proof-sha-prefix>-<nonce>`;
5. the token not previously present in the persistent M7 spent-token state.

Only the SHA-256 of the authorization token is retained. Reuse fails closed.

## Stage P1 boundary

This preparation commit authorizes and performs **none** of the following:

```text
NO ECS start/restart
NO security-group change
NO provider mutation
NO proof invocation
NO run token issuance
NO Product repository mutation
NO M6 proof repository mutation
NO PR
NO merge
```

The next stage is independent **P2 exact proof-source static audit**. Only after
P2 acceptance may provider preflight be separately considered.
