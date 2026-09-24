# HOW — Engineering Walkthrough Template

Use this template for the HOW track of a project-sharing delivery, or when the user explicitly requests only an implementation/source walkthrough. Remove sections that do not apply; do not invent facts, paths, or figures to fill the layout. When a figure is selected through the [figure workflow](figure-workflow.md), define its contract from source evidence, hand it to `$archify`, and accept the returned artifact before drafting figure-dependent prose.

When the full set is delivered, add one sentence near the top linking to the [WHAT guide](what-guide-template.md) for background and terminology and the [WHY guide](why-guide-template.md) for the core idea, conceptual mechanism design, and model-level information flow. This HOW document must still stand alone. Keep prerequisite teaching and extended conceptual explanation out of the implementation trace, and do not label any track as an appendix.

This template is the reader-facing document only. Keep full figure contracts, detailed source and inactive-path ledgers, validation checklists, hashes, receipts, run logs, and generated-artifact inventories in working evidence or a separate sidecar. Do not append them to the walkthrough unless the user explicitly requests an audit/reference appendix or the intended reader needs one. The final handoff still reports concise artifact and validation status.

Tell the system or project story, not the repository story. Use domain concepts for headings and figures; keep filenames, modules, commands, and source anchors subordinate unless the user requested a codebase tour.

Keep the abstraction boundary explicit. WHY explains semantic representations, model states, mechanism roles, and conceptual information flow. HOW maps those ideas to concrete interfaces, fields, functions, processes, devices, artifacts, calls, side effects, and failure paths. A conceptual flow does not belong here merely because it has ordered stages; include it only when the implementation mapping is the reader question.

Maintain the author-only live coverage ledger defined by [figure-workflow.md](figure-workflow.md). Seed it from the explanation contract, mark entries `how` or list all applicable shared tracks, then reconcile it after the final headings and prose stabilize.

## Depth contract

| Depth | Required HOW outcome |
|---|---|
| `Walkthrough` | Locate the active entrypoint and observable output, then trace repository responsibilities, data/control/state flow, boundaries, artifacts, runtime calls, failure paths, and validation. |
| `Deep dive` | Also establish component internals, shape/schema/precision and state changes, artifact/runtime lifecycle, detailed reproduction, and an evidence index. |

Record the selected HOW depth in the live ledger and assess its major implementation questions independently. A high-level architecture figure is orientation, not automatic coverage of transformations, state changes, artifact lifecycle, runtime interaction, or component internals.

| Visual slot ID | Candidate visual question | Typical semantic axis | Preferred form family |
|---|---|---|---|
| `how-active-architecture` | Which concrete components and boundaries own the active path? | Runtime ownership and dependency | Architecture or nested context map |
| `how-data-flow` | Which schemas, shapes, units, layouts, devices, or dtypes transform? | Typed transformation | Data flow or typed transformation pipeline |
| `how-control-flow` | Which states, decisions, gates, retries, failures, or fallbacks change execution? | Branching or state transition | Flowchart, decision tree, or lifecycle |
| `how-artifact-lifecycle` | Which persisted objects are produced, transferred, loaded, and consumed? | Provenance and lineage | Artifact lineage or lifecycle |
| `how-runtime-call-chain` | Which participants or functions interact, and in what order? | Temporal interaction and call order | Sequence, swimlane, or annotated call trace |

These five stable IDs are the HOW template's visual coverage contract; seed all five into the ledger even when a section is later `not_applicable`. Applicability, disposition, deep-dive figure-first, and reuse rules live in [figure-workflow.md](figure-workflow.md). In the sections below, each conditional `only when` is an applicability test for its named slot, not permission to skip the ledger row.

For every selected figure, follow the static-artifact rules and figure gates in [figure-workflow.md](figure-workflow.md); do not duplicate or weaken them in the generated HOW guide.

## 0. One-page summary and reading route

| Item | Content |
|---|---|
| One-sentence goal | What the system solves or provides |
| Non-goals | What the system does not replace or guarantee |
| Active entrypoint | Real entrypoint and source anchor |
| Key output | Return value, artifact, response, state change, or side effect |
| Owner | Repository, service, component, or runtime ownership boundaries |
| Evidence status | `STATIC` / `SOURCE-DERIVED` / `ARTIFACT-INSPECTED` / `OFFLINE` / `TARGET-DEVICE` / `ONLINE` / `E2E` / `UNVERIFIED` / `UNAVAILABLE` |

### Reading route

```text
problem and contract → active architecture → data/control flow
→ artifact/runtime boundary → component internals → evidence and limitations
```

## 1. Scope, version, and evidence boundary

| Item | Value | Evidence |
|---|---|---|
| Audience and prior knowledge |  |  |
| Target repository/workspace |  |  |
| Related producer/consumer |  |  |
| Version boundary / branches, revisions, and dirty states |  |  |
| Runtime/build version |  |  |
| Active path |  |  |
| Excluded paths needed to understand scope |  |  |
| Delivery surface and target renderer |  |  |
| Output document and asset root |  |  |
| Known gaps |  |  |

## 2. Repository, entrypoints, and responsibilities

Give the reader a bounded implementation map before tracing execution. Include only directories, packages, modules, services, or scripts that own a stage of the active path.

| Location or deployable unit | Responsibility | Active entrypoint or public interface | Consumed by | Source anchor |
|---|---|---|---|---|
|  |  |  |  |  |

State where the source project ends and external checkpoints, datasets, generated artifacts, services, runtimes, or deployment configuration begin. Do not enumerate inactive files merely because they exist.

## 3. Active architecture figure

The slot is applicable when concrete component ownership or execution boundaries are material to the active path. Use the contract in [figure-workflow.md](figure-workflow.md), and keep that contract outside the reader document.

<!-- Replace the path below with the accepted primary static asset relative to this document. -->
<!-- visual-slot: how-active-architecture -->
![Active architecture](<relative path to accepted .svg>)

**How to read:** Start at the input or request and follow the marked active path to the final output. Distinguish optional or historical paths only when they are needed for scope.

## 4. Implementation contract

Explain what the system solves and what it explicitly does not solve.

| Contract field | Meaning | Runtime field/object | Source anchor |
|---|---|---|---|
| Goal | What the system computes, transforms, serves, or controls |  |  |
| Non-goals | What it does not replace or guarantee |  |  |
| Input | Type, shape/schema, units, layout, device, or request fields |  |  |
| Core operation | Mathematical, algorithmic, or business transformation |  |  |
| Output | Return value, artifact, response, state change, or side effect |  |  |
| Control | State, gate, retry, timeout, convergence, or fallback |  |  |
| Acceptance | Correctness, quality, compatibility, latency, or service condition |  |  |

Define important symbols and fields before using them. Put mathematical expressions here and map them directly to implementation variables:

$$
\text{output} = F(\text{input};\,\text{state},\,\text{configuration})
$$

Implementation mapping: `input = ...`, `state = ...`, `F = ...`, and `output = ...`.

## 5. Data, control, and state flow

### 5.1 Data/schema/shape/precision flow

Create this figure only when transformations are central to the explanation.

<!-- visual-slot: how-data-flow -->
![Data flow](<relative path to accepted .svg>)

**How to read:** Mark each real schema, shape, unit, layout, encoding, device, or dtype change. Do not redraw unchanged stages.

| Stage | Owner/process | Input | Operation | Output | Boundary | Source anchor |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

### 5.2 State, gate, retry, and fallback

Create this figure only when gates or state transitions can change the active path.

<!-- visual-slot: how-control-flow -->
![Control flow](<relative path to accepted .svg>)

**How to read:** Show rejection, error, timeout, retry, early exit, and fallback only when they exist in source or runtime evidence.

```text
initial state → work/proposal → real operation → candidate state
→ validity or acceptance gate → accepted update or preserved state
→ termination → final result or fallback
```

Distinguish a proposal, delta, direction, or candidate from accumulated state and an accepted result. A configured step count is not proof that every update executes.

### 5.3 Runtime interaction and communication

Use this subsection only when the explanation depends on who communicates with whom, in what order, or under which synchronization semantics. It applies to interaction messages, not static dependency edges.

| Message ID | Phase/order | Sender | Receiver | Operation/protocol | Payload or state effect | Synchronization/concurrency | Condition/repeat scope | Source/runtime anchor |
|---|---|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |  |  |

For an interaction figure, use one ledger row and one figure-contract message item per arrow. Show local computation as a phase, activation, or note rather than an invented self-message. Keep distinct communication operations distinct. If a workflow requires long foldbacks or ambiguous crossings to show temporal order, request a sequence-oriented result from `$archify`.

## 6. Ownership and system boundaries

| Scope | Responsibility | Key code or interface | Evidence |
|---|---|---|---|
| Producer/model/component |  |  |  |
| Consumer/runtime/service |  |  |  |
| Cross-boundary contract |  |  |  |
| Fallback or recovery owner |  |  |  |

Use hierarchical context, system, or component zoom only as deep as the reader needs. Label each abstraction level; do not mix repositories, runtime processes, deployable units, and source modules as if they were equivalent. Omit a repository inventory unless repository structure is the reader's question.

## 7. Artifact lifecycle

Create an artifact figure only when persisted, exported, packaged, or transferred objects affect the active path.

<!-- visual-slot: how-artifact-lifecycle -->
![Artifact lifecycle](<relative path to accepted .svg>)

| Artifact | Contents | Producer | Loader or consumer | Directly used at runtime? | Evidence |
|---|---|---|---|---|---|
| Source/configuration |  |  |  | No |  |
| Intermediate build/export |  |  |  | Verify |  |
| Packaged/runtime artifact |  |  |  | Verify |  |

Do not conflate source code, configuration, datasets or checkpoints, intermediate exports, packages, loaded runtime objects, and final outputs.

## 8. Runtime call chain

The slot is applicable when participant or function order, cross-boundary calls, concurrency, or return paths are material to the implementation. If a trace table is clearer, use the `prose_or_table` exception; let `$archify` choose the diagram type for a selected figure.

<!-- visual-slot: how-runtime-call-chain -->
![Runtime call chain](<relative path to accepted .svg>)

```text
entrypoint → parser/adapter → wrapper/dispatcher → core component
→ postprocess/assembly → returned value, response, artifact, or side effect
```

| Call stage | Function/module | Input | Output | Language/process/device boundary | Source anchor |
|---|---|---|---|---|---|
|  |  |  |  |  |  |

Explain what is constructed, converted, copied, validated, returned, written, sent, or committed. State which operations happen outside the deployed component.

## 9. Component internals

Choose only the applicable subsection.

### 9.1 Model or nested component

| Stage | Module | Input shape/schema | Output shape/schema | Precision/encoding | Main operation | Source anchor |
|---|---|---|---|---|---|---|
|  |  |  |  |  |  |  |

Trace preprocessing, nested calls, core computation, postprocessing, loading chain, and ownership boundaries.

### 9.2 Iterative or numerical component

Define state variables, proposal, real operation, candidate, gate, convergence or termination, and fallback from source evidence. Map every shown transition to a real branch or update.

### 9.3 Service or application component

Trace request validation, queue/cache, external calls, retries/timeouts, persistence, response, and failure paths. Keep operational assumptions separate from observed behavior.

### 9.4 Library, compiler, or kernel component

Trace API, dispatcher, layout/dtype changes, lowering/launch, workspace/stream, supported-case guards, and fallback. Keep the API contract separate from implementation-specific optimization claims.

### 9.5 Data or scientific pipeline

Trace source data, schema/unit conversions, transformations, intermediate artifacts, quality gates, provenance, and final consumer.

## 10. Validation, reproduction, and limitations

Give the shortest source-grounded reproduction path needed to exercise the active implementation. Separate setup, smoke checks, real execution prerequisites, expected outputs, and success criteria. Do not present a mock/self-test, import check, dry run, or compile as evidence of full execution.

| Validation level | Entrypoint or command | Required inputs/environment | Expected output | Evidence obtained |
|---|---|---|---|---|
|  |  |  |  |  |

### Evidence and limitations

| Claim | Status | Scope/limitation |
|---|---|---|
|  | `STATIC` / `SOURCE-DERIVED` / `ARTIFACT-INSPECTED` / `OFFLINE` / `TARGET-DEVICE` / `ONLINE` / `E2E` / `UNVERIFIED` / `UNAVAILABLE` |  |

Separate source inspection, artifact inspection, offline execution, target-device execution, online acceptance, and end-to-end measurement. Do not infer one scope from another. Keep detailed source anchors, commands, and receipts in working evidence; retain exact inline source links only where they help the reader understand or verify a claim.
