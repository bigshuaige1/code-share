---
name: code-share
description: Create or revise source-grounded project explanations for technical systems. A bare `$code-share` produces separate deep-dive WHAT, WHY, and HOW guides; users may select low, high, or ultra mode, a track subset, or a combined guide. Use $archify for evidence-backed diagrams and a specialist skill for execution or benchmarking.
metadata:
  short-description: Build source-grounded technical project guides
---

# Code Share

Create presentation-ready explanations from inspected source, artifacts, and execution evidence. Never fill an evidence gap with a plausible architecture, result, or design intent.

Code Share owns investigation, reader contracts, evidence mapping, figure semantics, narrative, and Markdown assembly. `$archify` owns diagram type, construction, layout, routing, rendering, perceptual inspection, and export.

## Select mode and delivery set

`work_mode` controls depth and the figure artifact set. WHAT, WHY, and HOW are reader tracks, not modes.

| Mode | Select when | Required outcome |
|---|---|---|
| `low` | The user explicitly requests `$code-share low`, `walkthrough`, an overview, or a lighter complete treatment | Walkthrough depth: explain every major question needed for practical understanding. Figures carry only the core teaching route (fewer, per the tier rules in figure-workflow.md); static SVG only, no interactive HTML. |
| `high` | The user requests `$code-share high`, invokes bare `$code-share`, asks for a full or in-depth share, or requests a durable project share without naming a mode | Deep-dive depth with full figure-first coverage; static SVG only, no interactive HTML. This is the default. |
| `ultra` | The user explicitly requests `$code-share ultra` or an interactive deliverable | Everything `high` produces, plus a checked interactive HTML companion per figure with full delivery receipts. |

Depth names used inside the templates and figure-workflow.md map onto modes: `low` runs `walkthrough` depth; `high` and `ultra` run `deep-dive` depth and differ only in the figure artifact set. An explicit mode wins. A request for selected tracks changes scope, not depth. Do not silently reduce one track because its evidence or draft is sparse; mark the gap instead.

The default delivery set is three separate, independently readable WHAT, WHY, and HOW documents. Change it only when the user explicitly requests a combined guide or a track subset:

- A bare `$code-share` therefore means `high`: deep-dive depth plus separate WHAT, WHY, and HOW documents with static SVG figures.
- An explicit `low` changes the depth of all three default tracks, not the delivery set.
- An explicit WHAT, WHY, or HOW subset changes the delivery set while preserving the selected mode.
- An explicit combined request may use one guide while keeping the track boundaries visible.
- For a combined guide, preserve the track boundaries in the outline and coverage ledger; do not blend conceptual explanation into an untraceable implementation story.
- Short answers, presentation scripts, and narrow revisions do not expand into a full document set.

Prefer project naming conventions. For separate new files, use `<subject>_WHAT.md`, `<subject>_WHY.md`, and `<subject>_HOW.md` unless clearer names already exist. Preserve an existing walkthrough filename unless the user asks to rename it.

## Interview for document and figure design

When the user explicitly asks for `grill me`, a design interview, or to be questioned about the documents or figures, use `$grill-me` before drafting or drawing. Inspect available source, existing guides, and figures first; ask the user to choose priorities and tradeoffs, not to supply facts Codex can verify. Build a decision tree and ask only the current frontier, grouping independent questions in one round. Give each question concrete options, a recommendation, and the effect of each choice. Do not re-ask choices the user has already made.

Move through these dependent decisions:

1. **Reader job:** Who will read this, what must they understand or decide first, and which misconception would cause the wrong conclusion? Use the answers to rank the top reader questions.
2. **Document design:** Given that reader job, propose a small outline and ask about material choices still open: selected tracks, depth, separate or combined delivery, language, reading order, and the balance of domain explanation, source detail, and reproducible steps. Keep explicit mode and delivery choices fixed.
3. **Figure design:** Given the outline and evidence, propose a figure portfolio by reader question. Ask which relationships deserve visual emphasis, which comparison or path must be legible on first pass, and any delivery or accessibility constraints. Offer a brief for each consequential figure: question, intended takeaway, semantic scope, and what it must not imply. Let `$archify` choose renderer type and layout; do not ask the user to prescribe them unless they have a real preference.

After each answer, update the decision tree and ask the next unresolved frontier. When the choices are resolved, summarize the proposed document structure and figure briefs, including assumptions and rejected options, and ask for confirmation as `$grill-me` requires. If the user asks to proceed directly, end the interview and continue with the authorized Code Share workflow. Otherwise, use the normal clarification rule in [figure-workflow.md](references/figure-workflow.md).

## Keep the reader questions distinct

- **WHAT — domain foundations and subject:** the domain problem, its governing definitions and mathematics, why the problem is hard, and the vocabulary, with definitions decidable enough that the reader can classify new instances on their own; the foundations are taught as a concept dependency system the reader can redraw, not as a sequence of topics. This is followed by a compact identification of the subject: identity, observable inputs and outputs, variants, and boundaries. The domain is the body of the document and repository identification is the tail, never the reverse.
- **WHY — core idea and mechanism:** the principle that makes the subject work, taught as domain insight that would remain true if this repository were deleted, then developed systematically: derive the properties any realization of the principle must have, and teach each mechanism as the answer to one derived requirement—presented as a stated mismatch, resolved by the mechanism, and closed by a quantity that makes the claim decidable—not as a list of independent why-questions. Source anchors are evidence, not the section structure.
- **HOW — implementation:** architecture, active entrypoints, data/control/state flow, ownership and runtime boundaries, artifacts, calls, failure gates, validation, and reproduction. It follows the active implementation path rather than listing files.

A semantic flow belongs in WHY when its nodes are concepts, representations, or model states. A concrete flow belongs in HOW when its nodes are files, functions, services, runtime objects, artifacts, devices, calls, or side effects.

WHAT and WHY must stay correct and instructive for the domain even if the inspected repository were deleted: the repository is the instance and the evidence, never the theory. HOW is where the repository itself is the subject. In WHAT and WHY, every reader-facing section must deliver information gain over the sibling documents and the repository itself; restatement, inventory, and boilerplate sections (standalone evidence appendices, guarantee inventories, "what to remember" lists) do not ship there—keep audit apparatus in the author-only files and evidence labels inline.

For a durable deliverable, read only the applicable templates:

- [WHAT template](references/what-guide-template.md)
- [WHY template](references/why-guide-template.md)
- [HOW template](references/how-guide-template.md)

For an explicitly combined guide, use the applicable sections from each template without copying their repeated orientation or closing sections.

## Freeze the explanation contract

Before drafting, record only what the selected tracks need:

- mode, delivery form, selected tracks, depth, audience, reader outcome, non-goals, language, surface, and output paths;
- the reader's top one to three questions in priority order, what they must grasp on first pass, and the likely misconception that would change their decision; take explicit reader feedback as the priority signal when available, otherwise infer from the stated audience and task and mark it as an assumption;
- repository or workspace, revision set, dirty state, active path, excluded paths, and known evidence gaps;
- evidence and validation required for claims, links, figures, artifacts, renderers, and measurements;
- WHAT domain problem and foundations, objects, vocabulary, observable contract, variants, and category boundaries;
- WHY central principle, derived required properties, mechanism roles and internals, worked example, intent-versus-inference status, and limits;
- HOW versions, entrypoints, interfaces, runtime state, side effects, ownership boundaries, artifacts, failure conditions, and reproduction path.

Define important symbols and fields before use. Map implementation symbols to a runtime variable, file field, API field, object attribute, or source anchor.

Keep authoring evidence outside the reader document by default: source indexes, inactive-path inventories, full figure contracts, coverage ledgers, hashes, receipts, logs, and generated-artifact inventories. Include them only when the audience needs an audit appendix.

## Authoring loop

1. **Inspect the boundary.** Resolve the project root, revision and dirty state, active entrypoints, existing documents, artifacts, and evidence. Preserve the user's requested scope and existing files.
2. **Map evidence by track.** WHAT locates authoritative domain foundations and contract facts; WHY locates the domain principle, the conceptual model, and evidence for intent; HOW locates active source, runtime, artifact, and failure paths.
3. **Trace only the required chains.** WHY traces semantic input → representation → mechanism interaction or state change → signal or behavior. HOW traces concrete input → calls and state → side effects → visible result. WHAT records classification and observable contract without inventing internals.
4. **Trace relevant boundaries.** Record category boundaries for WHAT, assumption and interpretation boundaries for WHY, and repository, process, service, language, device, and artifact boundaries for HOW.
5. **Plan visual coverage before drafting.** For every durable `low`, `high`, or `ultra`, or any explicit figure request, read [figure-workflow.md](references/figure-workflow.md). Seed one ledger row for every explicit visual slot in the selected templates before drafting. A short inline answer may skip this when no figure is needed.
6. **Draft for the reader job.** Organize WHAT and WHY around domain concepts, and HOW around active responsibilities and execution. Do not use repository layout, internal process metadata, or a file inventory as the narrative. Teach the domain before the instance: a WHAT or WHY section that only makes sense to a reader who has already seen this repository has not finished its job.
   Put the answer to the highest-priority reader question where a first-pass reader will find it; let evidence and detail follow. Before delivery, cut or move to author-only evidence any paragraph, label, table, or extra figure that does not help a selected reader question, disambiguate a material claim, or satisfy a required coverage/evidence gate. Keep the requested depth and the evidence needed to trust the answer; do not apply a fixed word or figure quota.
7. **Create accepted figures when selected.** Write a source-backed contract, delegate to `$archify`, and continue through its validation and delivery path, using the artifact pipeline of the selected mode's tier (static SVG for `low`/`high`, interactive HTML plus SVG for `ultra`). A candidate specification is not a delivered figure.
8. **Reconcile after the narrative stabilizes.** Recheck depth, track boundaries, coverage, figures, cross-links, terminology, evidence labels, and gaps. Any material narrative change invalidates the affected coverage result until reconciled again.

## Domain adapters

Apply only the adapters supported by evidence:

- **Model or ML:** WHAT identifies task objects and outputs; WHY explains objective, representations, information mixing, routing, scoring, and mechanism interaction—for a learned component, WHY also derives what the training objective minimizes in operator or statistical terms, and argues why the training distribution covers the deployment distribution (or marks the gap); if the deployment or convergence criterion differs from what the objective minimizes, state the mismatch explicitly; HOW traces preprocessing, shapes, precision, checkpoints, export/loading, nested calls, and ownership.
- **Iterative or numerical:** WHAT defines the mathematical object and result; WHY explains state, proposal, operator relation, acceptance, convergence intuition, and invariants; HOW maps variables, updates, gates, termination, and fallback.
- **Service or application:** WHAT defines actors and the visible contract; WHY explains domain state, policy, coordination, and lifecycle meaning; HOW traces validation, queues or caches, external calls, retries, timeouts, persistence, response, and failure.
- **Library, compiler, or kernel:** WHAT defines the public surface; WHY explains abstraction, transformation, scheduling or memory model, and preserved correctness; HOW traces API, dispatch, layout and dtype changes, lowering or launch, workspace or stream, guards, and fallback.
- **Data or scientific pipeline:** WHAT defines sources, objects, outputs, units, and quality meaning; WHY explains representation choices, transformation logic, provenance, and information loss or preservation; HOW traces schemas, conversions, stages, intermediate artifacts, gates, storage, and consumers.

Adapters may compose. Do not force model vocabulary onto a library or solver vocabulary onto a service.

## Evidence and tool boundaries

- Label claims as `STATIC`, `SOURCE-DERIVED`, `ARTIFACT-INSPECTED`, `OFFLINE`, `TARGET-DEVICE`, `ONLINE`, `E2E`, `UNVERIFIED`, or `UNAVAILABLE` as applicable.
- Never imply that training, export, deployment, benchmarking, or online execution occurred without evidence, and never infer an end-to-end result from a component observation.
- Keep source, configuration, data or checkpoints, intermediate exports, packages, loaded runtime objects, and final outputs distinct.
- For iterative or gated systems, distinguish proposed or candidate state from accepted accumulated state. A configured iteration count is not proof that every update executes.
- Use `$codebase-design` for a requested redesign, `$markdown` for syntax-specific repair, and `$kernel` or `$inference-optimizer` for target-device performance work. Code Share may explain their verified results but does not replace their evidence contracts.

## Validate and deliver

Do not report completion until applicable gates pass or are explicitly unresolved:

1. Every source path and anchor exists and supports the claim; active, optional, historical, and fallback paths are not confused.
2. Each selected track meets its reader outcome and depth. Separate documents are independently readable; a combined guide may reuse earlier definitions when its full teaching route remains coherent and the track boundaries stay clear. For WHAT and WHY, a reader new to the domain must be able to restate the domain problem, its governing definitions or equations, and the core principle without seeing the repository.
   Check the top reader questions against the delivered pages without consulting author notes: can a fresh reader locate the answer, explain the deciding relationship, and avoid the recorded misconception? An author or model rehearsal is a proxy, not evidence that a human reader succeeded; record actual reader feedback separately when available.
3. The live coverage ledger has exactly one resolution for every template visual slot and every additional major reader question. At deep-dive depth (`high`, `ultra`), every applicable template slot is figure-first; a prose/table exception has a visual-counterfactual rationale, and every selected or reused figure has an accepted static asset and a Markdown placement.
4. Figures pass the contract, semantic, interaction, artifact, renderer, perceptual, and explainability gates in [figure-workflow.md](references/figure-workflow.md).
5. Captions, alt text, tables, fences, formulas, units, shapes, schemas, precision claims, links, and evidence labels are valid and consistent. A caption states the claim its figure supports or decides, not an inventory of what is depicted. Formulas use renderer-safe LaTeX per the `$markdown` rules: no non-LaTeX escapes such as `\*`, no CJK inside `\text{}`, and Unicode `‖…‖` instead of `\|` in table cells.
6. Separate documents are complementary and cross-linked; a combined guide keeps WHAT, WHY, and HOW boundaries legible without repeated orientation.
7. Validation checks the delivered artifact identity, not a stale candidate or earlier output.

When revising one topic, change only that topic and directly coupled captions or assets.

Report the selected mode, delivery form, track depth and paths, inspected revision boundary, coverage status, figure contracts and static assets, Archify receipts, renderer and perceptual status, evidence actually obtained, unresolved gaps, failed gates, and reproduction entrypoints when HOW or execution is in scope. Include the coverage counts required by [figure-workflow.md](references/figure-workflow.md); do not describe visual coverage only as complete or accepted. Do not paste a long completed document into chat when the user asked for files.
