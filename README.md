# LinguaGraph M7 external proof / successor provider rebind

This independent repository contains proof infrastructure only for
**M7 — Alignment Mutation Concurrency Hardening**. It does not modify the
LinguaGraph Product repository and it is intentionally separate from the
historical `Pacchifans69/linguagraph-m6-proof` evidence repository.

## Status

```text
checkpoint:             M7
proof path:             M7-EXI-01 — alternate hosted Gate 2 proof framework
stage:                  successor provider rebind; final static re-audit pending
successor proof:        NOT AUTHORIZED / NOT EXECUTED
successor run auth:     NOT ISSUED
successor Gate 2:       NOT ESTABLISHED
provider preflight:     P3A / P3B / P3C PASS
provider binding:       fresh exact ECS / source-bound
prior 854137cd epoch:   Gate 2 PASS / ESTABLISHED (historical exact-epoch evidence)
```

The current Product target is the docs-only `M7-SHDR-F01` successor. Its own
canonical GitHub Actions attempt again failed before every repository-defined
step:

```text
Product run:       #125 / 35436499631
Product head:      c7aae26e3abaa34b3756ffe96ee718beaf8524b3
job steps:         []
runner id:         0
classification:    provider / pre-step failure
semantic evidence: none
```

This diagnostic is not application/test evidence. The successor proof source is
already bound to the exact Product candidate and, by this provider rebind, to a
fresh exact ECS identity. It still requires an independent exact static
re-audit and a fresh one-shot Human authorization before formal execution. No
successor execution is authorized by this rebind.

## Exact Product binding

```text
repository:     Pacchifans69/LinguaGraph
branch:         m7-alignment-mutation-concurrency-hardening
candidate SHA:  c7aae26e3abaa34b3756ffe96ee718beaf8524b3
candidate tree: 1afa65b74a41ef43699425bbcc3ccbb30cb64658
unique parent:  854137cd498569f7c3d770d3b82be51042080edd
frozen main:    3f08eca99f03180eef9dcd7008287892f0e6501d
Alembic head:   0006
```

The provider-neutral core fails closed unless the remote Product branch, remote
main, detached candidate checkout, tree, unique parent, and frozen-main
ancestry all match these exact values.

The successor changes only these four Product files relative to the already
reviewed/proved implementation epoch `854137cd...`:

```text
AGENTS.md
README.md
docs/development/CURRENT_STATE.md
docs/testing/testing-strategy.md
```

Application code, tests, dependencies, lockfiles, workflows, migration files,
and runtime baselines are unchanged. Therefore the preparation-time expected
suite counts remain `602 / 519 / 32`; they are guards only and must still be
observed by any authorized formal run.

## Prior exact-epoch evidence retained

The immediate predecessor `854137cd498569f7c3d770d3b82be51042080edd`
(tree `7b5306fbd37a158cd1fb688fd050d20cfc5aec74`) has historical exact-candidate
Gate 2 evidence:

```text
proof source:       4274eeae6211a1744ac63958a026ff95670f445b
proof tree:         2270f665b2659f88dcdd88bed216828e32e5a7ff
formal outcome:     PASS
pytest:             602 passed
Vitest:             519 passed
Playwright:         32 passed
archive SHA-256:    2529a1e06989058c2a7acdac69374912ba2ccee32ba59c5438d2c746c8eed2a3
authorization:      SPENT / MUST NOT REUSE
```

That evidence remains valid for `854137cd...` only. It does **not** transfer to
`c7aae26e...`, even though the successor is docs-only.

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
host state env:         M7_PROOF_HOST_STATE (unset or exact fixed path only)
fixed host state:       ~/.local/state/linguagraph-m7-proof
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
- clean-start rejection of pre-existing candidate/evidence paths;
- fixed, non-redirectable M7 spent-token authority;
- collision-rejecting per-authorization proof-artifact archive identity;
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

A separately Human-authorized fresh-provider establishment completed P3A, P3B,
and P3C before this source rebind. The Alibaba adapter is bound to this exact
fresh execution identity:

```text
instance id:   i-j6c6wx48n07xnkpoxsjc
region:        cn-hongkong
zone:          cn-hongkong-d
instance type: ecs.g9i.xlarge
image:         ubuntu_24_04_x64_20G_alibase_20260828.vhd
```

P3B control-plane observations were:

```text
system disk:   d-j6c6wx48n07xnkpm461g
disk shape:    cloud_essd / 40 GiB / DeleteWithInstance=true
VPC:           vpc-j6cgz9a4frhl3oxxbecsj
vSwitch:       vsw-j6c9f1ch565yr60wzx2rc
private IPv4:  172.23.68.215
EIP:           47.238.211.55
```

P3C independently established Ubuntu 24.04 / x86_64, 4 CPUs, sufficient RAM,
root account home `/root`, clean M7 host state, required outbound access,
unchanged proof/Product refs, tokenless IMDS rejection with HTTP 403, successful
IMDS token mode, exact instance/region/zone/type/image/VPC/vSwitch/private-IP
identity, and non-empty signed instance identity document / PKCS7 material.
Docker was intentionally left uninstalled; the reviewed adapter may bootstrap
`docker.io` during a later separately authorized formal run.

The adapter's executable immutable provider guard remains deliberately narrow:
exact instance ID, region, zone, instance type, and image. Disk/network values
above are retained preflight observations, not newly introduced execution
guards. In particular, runtime-assigned IP addresses are not treated as
immutable provider identity.

The predecessor host `i-j6c13vpnkuq6xbbhyxzw` remains historical only and is
not accepted by this rebound adapter.

## One-shot authorization

A formal invocation requires all of:

1. this proof repository checked out cleanly on `main`;
2. `APPROVED_PROOF_SHA` equal to the exact Human-approved proof commit;
3. remote proof `main` equal to that same SHA;
4. a fresh token matching
   `M7-EXI-01-RUN-<approved-proof-sha-prefix>-<nonce>`;
5. the token not previously present in the persistent M7 spent-token state.

Only the SHA-256 of the authorization token is retained. Reuse fails closed.

Each formal authorization also receives a distinct archive identity:

```text
m7-proof-artifacts-<approved-proof-sha>-<authorization-sha256>.tar.gz
```

Before any token is consumed, the adapter rejects a pre-existing
`proof-artifacts/` directory or `candidate/` checkout. The spent-token
authority is derived from the operating-system account home, not an injected
`HOME`; inherited `HOME` must match that account home, and an inherited
`M7_PROOF_HOST_STATE` may only repeat the resulting exact path.

Canonical archive and SHA-256 sidecar paths are reserved with no-clobber
semantics. A replay or any pre-existing archive slot therefore fails closed
without overwriting the first retained artifact.

## Successor provider-rebind boundary

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

This provider rebind changes only this README plus Alibaba-adapter
documentation/comments and the exact expected instance ID. The provider-neutral
core remains byte-identical; Product pins, semantic proof stages, suite-count
guards, runtime pins, one-shot/replay protection, and artifact packaging are
unchanged. Region, zone, instance type, and image guards are unchanged.

The next step after landing, if separately authorized, is an independent exact
proof-source static re-audit of the resulting new proof SHA. Only after that
audit passes may a fresh one-shot formal run authorization be considered.
