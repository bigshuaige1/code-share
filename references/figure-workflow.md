# Figure Workflow and Handoff Contract

Read this reference before visual-coverage decisions for every durable `low`, `high`, or `ultra`, and for any explicit figure request or revision. A short inline answer may skip it when prose is sufficient.

Mode names map onto depth for every rule below: `low` runs `walkthrough` depth; `high` and `ultra` run `deep-dive` depth and differ only in the figure artifact set (see "Delivery tiers").

Code Share owns the reader question, source evidence, semantic scope, and acceptance contract. `$archify` owns diagram type, authoring, layout, routing, rendering, inspection, and export. Do not create a second drawing pipeline.

## Resolve intent

A figure brief is ready when it has one reader question, a reader outcome, scope and exclusions, one dominant semantic axis, source-backed critical semantics, facts it must not imply, an evidence boundary, a static-delivery need, and concrete acceptance questions.
Order candidate figures by the reader's prioritized questions, not by source-file order or the number of available facts. For each figure, state the one relationship or conclusion a first-pass reader should notice before inspecting supporting labels. Source evidence decides what is true; the reader task decides what is prominent.

In normal mode, infer the smallest defensible reader intent from source and context, label assumptions, and continue. Ask one focused clarification only when a material choice blocks a truthful figure. Enter grill mode only when the user explicitly asks to be grilled, challenged, or questioned about the figure.

## Keep a slot-complete coverage ledger

Keep the ledger outside the reader document. Before drafting, copy every explicit `visual_slot_id` from each selected template into its own base row. Freeze applicability first: a slot is applicable when its named relationship is within the frozen reader contract and material to the selected track and depth. Evidence sufficiency does not decide applicability; record it separately and use `unavailable` when an applicable instance lacks evidence. A template placeholder or an existing section alone does not make it applicable. Never seed the ledger from a preferred asset count or from figures that already exist.

Every applicable slot has at least one instance. Name even a single instance `<visual_slot_id>#1`; use `#2`, `#3`, and so on for additional independent questions. Do not force several mechanisms or axes into one figure merely to keep the asset count near the template slot count. A `not_applicable` base row has no instance. Give a material question outside the template a purpose-based `visual_slot_id` such as `extra-<track>-<purpose>` and name its instances the same way; exclude these extra slots from `template_slots_total` but include their instances in the disposition counts.

Record `visual_slot_id`, `slot_instance_id`, `deliverable`, `depth`, `section_or_topic`, `reader_question`, `abstraction_level`, `dominant_semantic_axis`, `semantic_pattern`, `preferred_visual_form`, `disposition`, `figure_id_or_rationale`, and `evidence_status`. Use `semantic_pattern: none` when the dominant axis and form hint fully express the need. After rendering, also record the `renderer_type` returned by `$archify` and the accepted static asset path for every figure placement; Code Share does not preselect the renderer type.

Use only these dispositions:

- `figure`: this instance has its own accepted figure contract, asset, and Markdown placement;
- `merged_same_question`: an accepted figure answers the same reader question at the same abstraction level, on the same dominant axis, and within the same evidence scope; name its `figure_id` and place it in this slot; report this disposition as a reused figure placement;
- `prose_or_table`: a compact table, formula, or prose is demonstrably clearer; the rationale must be checkable in three parts—what nodes, relations, or axes a figure would encode, why that encoding is isomorphic to the non-figure answer or would distort the evidence, and where the acceptance question is fully answered. A lone appeal to precision, compactness, or lookup convenience fails this rationale;
- `not_applicable`: the object or relationship is outside the frozen reader contract/depth or genuinely absent from the subject; use it only on the base row, state which condition applies, and never use sparse evidence as the reason;
- `unavailable`: the slot is applicable but evidence or a delivery gate is missing; state the unresolved condition.

For deep-dive depth (`high`, `ultra`), every applicable template slot starts as `figure`. `prose_or_table` is an exception, not a time-saving default: brevity, an existing table, asset cost, renderer inconvenience, or the availability of a broad overview figure is not sufficient. Recheck every exception after the narrative stabilizes. `low` (walkthrough depth) may choose prose or tables more freely, but still requires one row per slot. In `low`, figure-first applies only to the slots that carry each track's core teaching route—including the protected slots below when applicable—so the delivered figure set stays small; every other applicable slot still gets a ledger row and a disposition.

In `deep-dive` depth (`high`, `ultra`), the slots that carry each track's core teaching may not resolve to `prose_or_table`: `why-unifying-idea` and `why-mechanism-deep-dive` for WHY, and `what-domain-landscape` and `what-concept-relations` for WHAT. In `low`, these four slots remain figure-first when applicable, because they carry the core teaching route. When an applicable protected slot lacks evidence, mark it `unavailable` instead of closing it with prose. Additionally, when more than half of a track's applicable instances resolve to `prose_or_table` at deep-dive depth, reopen that track's dispositions and re-justify every exception against the three-part rationale before delivery.

Reuse is also an exception. Topic overlap, shared entities, or a common source path is insufficient. WHY and HOW normally need different figures because conceptual semantics and implementation/runtime semantics are different abstraction levels. A reused asset must answer every acceptance question for both instances from the same static SVG, preserve both critical-semantic sets, and have compatible `must_not_imply` sets without relying on surrounding prose. Independent questions never become `merged_same_question`; give them separate figures or a justified non-figure disposition.

This is a coverage contract, not a decorative quota. Applicability and evidence still govern what is drawn, but a broad orientation figure cannot close independent questions about taxonomy, representation, mechanism interaction, signal derivation, runtime order, state, ownership, or artifact lifecycle merely because it names them.

Seed the ledger before drafting and reconcile it after headings and prose stabilize. Reopen it when a revision adds or materially changes a mechanism, transformation, path, branch, state, boundary, lifecycle, or comparison. Split a figure when independent questions or competing axes require separate reading paths.

Before delivery, report both placement and asset counts:

- `template_slots_total`, `not_applicable_slots`, and `applicable_slots`;
- `slot_instances_total`, `new_figure_instances`, `reused_figure_instances`, `prose_or_table_instances`, and `unavailable_instances`;
- `figure_placements` and `unique_accepted_assets`;
- the `semantic_pattern` and `renderer_type` distributions.

The counts must satisfy:

```text
template_slots_total = applicable_slots + not_applicable_slots
slot_instances_total = new_figure_instances + reused_figure_instances
                     + prose_or_table_instances + unavailable_instances
figure_placements = new_figure_instances + reused_figure_instances
slot_instances_total >= applicable_slots
```

Also report the counts per WHAT, WHY, and HOW. A summary such as `coverage accepted` without these counts fails the coverage gate.

## Select semantic pattern before renderer type

Choose the visual form from the information relationship, not from a desire for variety and not merely because the explanation contains steps. Record the intended semantic pattern and preferred visual form before `$archify` chooses a supported renderer type.

| Reader question or relationship | Information pattern | Preferred visual form |
|---|---|---|
| What surrounds the subject, and where is its boundary? | Context and boundary | Context map, nested boundary map, or architecture |
| How are concepts, categories, or variants related? | Hierarchy, containment, or crossed classification | Concept map, taxonomy tree, nested map, or classification matrix |
| What may enter or emerge at a boundary? | Contract mapping | Paired input/output map, interface schematic, or compact schema map |
| Which capabilities apply to which objects or guarantees? | Comparison and exclusion | Capability matrix, quadrant, or boundary map |
| How do conceptual mechanisms cooperate? | Composition and interaction | Hub-and-spoke composition, layered mechanism map, or dependency map |
| What becomes what? | Transformation | Typed transformation pipeline, data flow, or quantity-backed Sankey |
| Why does a result follow from internal signals? | Derivation or causality | Formula-led derivation chain, causal chain, or signed-contribution view |
| How does one example cross stages or owners? | Worked trace | Storyboard, swimlane, or annotated trace |
| Who communicates with whom, and in what order? | Temporal interaction | Sequence or swimlane |
| What decisions and gates execute? | Branching and control | Flowchart or decision tree |
| How does state change? | State transition | Lifecycle or state machine |
| Where do persisted objects come from and go? | Provenance and lineage | Artifact lineage or data flow |
| How do measured values compare or change? | Quantitative relationship | Bar, line, scatter, heatmap, waterfall, or another evidence-backed chart |

Do not use a quantitative chart without measured values, a Sankey without meaningful quantities, a Venn without real set overlap, or a tree when cycles or many-to-many dependencies are material. A table remains preferable for a plain list, exact lookup, or small before/after comparison.

`$archify` still owns the final supported diagram type, construction, and layout. Renderer types are implementation choices, not the semantic vocabulary of the brief. It may map a preferred form to the nearest supported type only when the static result preserves the information pattern and answers the acceptance questions. If the mapping collapses a taxonomy, matrix, derivation, hierarchy, or worked trace into a generic process flow, record a `type_capability_gap`; split the figure or mark the instance `unavailable` rather than silently drawing another workflow. Split ownership, transformation, and temporal interaction when they compete for the same arrows.

After planning all figures, review them as a portfolio. Repeated renderer types are valid when the reader questions genuinely share a semantic pattern; visual variety by itself is not a goal. Reopen the type decisions when taxonomy, contract, comparison, derivation, worked-example, and runtime-order questions all collapse to the same workflow-like composition, or when most figures differ only in box labels.

## Figure expression

Coverage and correctness decide *whether* a figure may ship; expression decides how much it teaches. Apply these rules to every brief and every delivered figure:

1. **Declared reading order.** Every brief states where the eye starts and the order the reading follows—for ordered figures this is `active_path`; for unordered figures, name the entry point and the sequence in which the focal relation is meant to be read. The layout must make that order dominant; a figure whose reading order is ambiguous fails even when every element is correct.
2. **Both sides of a mismatch.** A figure answering "why this design, not the naive approach" shows both sides of the mismatch and annotates the deciding quantity on the figure itself (scale, norm, count, or growth law), not only in the surrounding prose. A figure that shows only the chosen design argues nothing.
3. **Dependency direction in concept systems.** When prerequisite structure is material to the reader question, a knowledge-system, concept, or landscape figure encodes which concept presupposes which—directed prerequisite edges or explicit layering. Do not flatten a real dependency order into an undirected grouping; conversely, a genuinely symmetric correspondence stays undirected.
4. **Caption as claim.** The caption states the claim the figure supports or decides, then the reading path—not an inventory of what is depicted. Caption plus figure must be readable without the surrounding paragraph.

## Define the handoff contract

Every selected figure supplies:

| Field | Required content |
|---|---|
| `figure_id` | Stable purpose-based ID |
| `reader_question` | The single question the figure answers |
| `reader_outcome` | What the reader can explain, compare, or locate from the standalone static figure |
| `audience_depth` | Figure-specific override, otherwise inherited from the document |
| `scope` | Included boundaries and excluded paths |
| `dominant_semantic_axis` | One primary axis such as order, flow, transformation, hierarchy, ownership, or comparison |
| `semantic_pattern` | Optional specialized structure or behavior grammar when it adds information beyond the dominant axis; otherwise `none` |
| `preferred_visual_form` | A non-binding form hint that best expresses the reader question before renderer constraints, plus a one-sentence rationale |
| `focal_relation` | The primary hierarchy, grouping, contrast, overlap, correspondence, or composition when the figure is not ordered, plus the reading entry point and sequence for that relation; otherwise `not_applicable` |
| `critical_semantics` | Evidence-backed entity, relationship, branch, or message IDs essential to the outcome |
| `must_not_imply` | False equivalences, paths, or boundaries the figure must not suggest |
| `active_path` | Ordered path that must dominate only when order is real; otherwise `not_applicable` rather than an invented flow |
| `entities` | Stable IDs, labels, roles or states, source anchors, and priority |
| `relationships` | Direction, meaning, condition or protocol, source anchor, and priority |
| `branches` | Real gates, loops, retries, failures, fallbacks, outcomes, priority, and source anchor |
| `interaction_semantics` | Initiator, recipients, operation, order, synchronization, concurrency, repeat scope, payload, priority, and source/runtime anchor when applicable |
| `static_critical` | One static-presentation mapping for every critical ID |
| `acceptance_questions` | Questions answerable from the standalone static figure |
| `evidence_status` | Inspected or executed status, assumptions, and gaps |
| `delivery_need` | Language, surface, renderer, checked HTML, standalone SVG, and requested non-PNG fallback |

Facts and semantic priority belong here; coordinates, colors, renderer primitives, concrete routing, and export internals do not.

Mark an item `critical` only when removing its static presentation would make an acceptance question unanswerable or would allow a `must_not_imply` misconception. Mark other useful context `supporting`. The IDs in `critical_semantics`, items marked `priority: critical`, and `static_critical` must form the same evidence-backed set, with exactly one resolution per ID.

Every word visible in the delivered figure—node labels, legend entries, color keys, axis titles, and annotations—must trace to `entities`, `relationships`, `branches`, or an explicit annotation in this contract. Renderer template defaults, leftover placeholder legends, and unused category keys are contract violations, not cosmetic issues. Do not accept a figure whose legend names categories that appear nowhere in the brief, and do not leave the legend check to the renderer's structural validation.

Do not hand off a materially incomplete or contradictory brief. Missing optional supporting context is not a blocker.

Before the first Archify candidate, check the brief once for an answerable reader question, supported critical IDs, one reading axis, genuine branches or interactions, exclusions, concise labels in the chosen language, and the first-pass conclusion. Resolve semantic gaps in the brief before rendering; do not use geometry retries to discover missing facts. Reuse this checked brief as the source of truth for any repair.

## Communication figures

These rules apply when arrows represent communication or ordered interaction, not static dependencies:

1. One arrow represents one verified cross-boundary interaction with sender, receiver, operation or protocol, direction, payload or state effect, phase, and evidence anchor.
2. Show local computation as a phase, activation, or note unless a self-directed event is part of the runtime contract.
3. Preserve message direction and happens-before order independently. A reverse arrow must be a real reverse interaction.
4. Represent bidirectional, concurrent, asynchronous, and same-batch exchange explicitly when material.
5. Keep collective and point-to-point operations distinct; never substitute an invented transport algorithm for a verified collective invocation.
6. Record participant set, root or destination, synchronization, payload, condition, per-operation repeat scope, and total count only when evidence supports them.
7. Use a loop or segment annotation for repetition. Prefer a sequence-oriented result when foldbacks or crossings obscure message order.

A communication figure fails semantic review if an arrow is missing, reversed, duplicated, ambiguously shared, or unsupported.

## Delivery tiers (figure artifact set)

The mode selects the artifact pipeline per figure; the accuracy gates do not change across tiers.

- **`ultra`:** validate at `showcase` → `deliver` the interactive HTML → `visual-check` (record `skipped` when chrome-unavailable) → browser-free `export-static-svg.mjs` → perceptual review of the exact SVG. Receipts include the deliver SHA-256 binding; the HTML ships as the interactive companion.
- **`low` / `high`:** validate at `showcase` → `deliver` HTML to an author-only evidence path → `visual-check` (record `skipped` only for `viewer/chrome-unavailable`) → browser-free `export-static-svg.mjs <evidence.html> <figure.svg> light` → perceptual review of the exact SVG. Keep the checked HTML and receipts as author evidence; the reader-facing document links only the standalone SVG.
- Every selected figure uses Archify's atomic `deliver` gate and its specification/artifact receipt. `low`/`high` omit the reader-facing interactive companion, not final acceptance or traceability. Showcase validation (all 9 artifact checks, 0 diagnostics), label fidelity, glyph safety, and perceptual review remain mandatory.

## Static artifact rules

- For Markdown, display a standalone SVG with meaningful alt text and a relative path. In `ultra`, keep checked HTML as the validated source or optional interactive companion; in `low`/`high` the SVG is the only reader-facing figure artifact.
- Never create, export, accept, or deliver PNG in this workflow, including temporary review images. Use SVG for the primary static figure and WebP for browser evidence.
- If the target cannot display SVG, use a verified non-PNG alternative when possible; otherwise ask one focused blocking question or mark `UNAVAILABLE`.
- A standalone SVG must be non-empty, parseable, static, and free of scripts, active animation, `foreignObject`, and external font, image, or stylesheet URLs.
- When `visual-check` reports `viewer/chrome-unavailable`, retain the skipped receipt and use Archify's supported browser-free exporter only on successfully delivered Archify HTML. It is not a renderer for arbitrary HTML or SVG. Do not search for or install Chrome. Browser containment remains `SKIPPED` or `UNVERIFIED`.
- Inspect the exact delivered SVG for missing glyphs, clipping, overlap, wrapping, spacing, contrast, and arrow ambiguity. Do not infer perceptual quality from structural validation.

For a multi-figure delivery, inspect each exact SVG at its intended display size, then view two or three adjacent figures together at reduced size to find inconsistent emphasis, repeated content, or an outlier in density, scale, or reading direction. This overview is a triage aid, not acceptance evidence: reopen the exact SVG for any suspect figure. Recheck the first-pass conclusion and acceptance questions before changing geometry. Repair only the failed figure and directly coupled caption or placement; preserve accepted assets and their receipts. If the same defect recurs, correct the shared brief or authoring choice once before more renders. No overview pass may waive the per-figure semantic, artifact, or perceptual gates.

## Figure gates

A selected figure is complete only when applicable gates pass or are marked unresolved:

1. **Coverage:** every template visual slot and additional material reader question has exactly one justified resolution; required counts reconcile.
2. **Contract:** required entities, relationships, conditions, evidence distinctions, and the active path or focal relation are present.
3. **Explainability:** the three critical-ID sets agree, acceptance questions are answerable from the static figure, `must_not_imply` remains false, and every visible label, legend entry, and annotation traces to the contract with no renderer-default or unused legend items.
4. **Interaction:** every message has the correct participants, direction, phase, synchronization, concurrency, and repeat scope.
5. **Readability:** the primary reading structure—path, hierarchy, comparison, grouping, or state relation—is immediately legible; ordered figures have no unrelated crossings, long foldbacks, ambiguous shared corridors, or masked routes.
6. **Artifact:** the exact SVG exists, parses, is self-contained, resolves from the document, and no new PNG exists.
7. **Renderer:** the declared target renderer was exercised, or the result is `UNVERIFIED`; the chosen renderer type preserves the recorded semantic pattern and preferred visual form, or a capability gap is explicit.
8. **Perceptual:** the exact SVG was visually inspected; browser evidence and perceptual review are reported separately.
9. **Portfolio:** repeated renderer types reflect repeated semantic patterns, not a generic box-and-arrow default; pattern and type distributions are reported.
10. **Expression:** the declared reading order is dominant in the layout; mismatch figures show both sides with the deciding quantity annotated; concept-system figures encode dependency direction where prerequisite structure is material; the caption states the claim the figure decides.
11. **Reader priority:** on a first pass of the exact static asset, the reader can find the figure's stated main conclusion before supporting detail; the figure answers its acceptance question without relying on prose, and adjacent figures do not compete to answer the same independent question.

A structural pass cannot override a failed semantic, interaction, renderer, or perceptual gate. Bind validation receipts to the exact delivered candidate and artifact identity.
