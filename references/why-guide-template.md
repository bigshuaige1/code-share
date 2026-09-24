# WHY — Core Idea and Mechanism Design Guide Template

Use this template for the WHY track of a full project-sharing delivery, or when the reader needs the model idea, internal design, and conceptual flow that make a system understandable beyond its surface contract. In this track, WHY means explanatory understanding delivered as **one systematic development**: state the governing principle, derive the properties any realization of it must have, then teach each mechanism as the answer to one derived requirement. The development must read as one connected argument—every section hands its conclusion to the next, and each mechanism subsection closes by showing how its property composes with the others in the complete system. A list of independent "why is it done this way" entries is fragmented and does not ship.

Do not force the document into a long argument about preliminary motivation, a naive baseline, or rejected alternatives. Design pressures, comparisons, and tradeoffs belong only where they clarify the mechanism being taught. The narrative spine is the principle and its derivation at a conceptual level.

Assume only the minimum definitions supplied by the [WHAT guide](what-guide-template.md), and restate a term briefly when standalone readability requires it. Conceptual architecture, representation flow, state evolution, mechanism interaction, and signal formation belong here—woven into the systematic development, not as standalone inventory sections. Concrete files, classes, functions, runtime objects, call order, deployment boundaries, artifact lifecycle, commands, and reproduction belong in the [HOW guide](how-guide-template.md). Cite implementation as evidence without using repository structure as the narrative.

Cut from the reader document: shape or inventory restatements, standalone flow retellings, evidence-boundary appendices, and summary or "what to remember" lists. State evidence status inline on claims using the labels from SKILL.md and keep audit apparatus in the author-only files. A section that only renames what the WHAT guide or the repository already says does not ship.

When the full set is delivered, add one sentence near the top linking to WHAT for foundations and HOW for implementation. This WHY document must remain independently readable. Do not label any track as an appendix.

Maintain the shared author-only coverage ledger from [figure-workflow.md](figure-workflow.md) with `deliverable: why` or an explicit list of shared tracks and the selected WHY depth. Reconcile WHY coverage after its headings and prose stabilize. A HOW figure is reusable only when it answers the same conceptual reader question at the selected depth; a source/runtime diagram does not automatically explain the model idea.

## Depth contract

The selected depth changes how completely the reader can mentally simulate the idea. It must not turn WHY into either a glossary, a design-review dossier, or a source/runtime trace.

| Depth | Required WHY outcome |
|---|---|
| Walkthrough | State the core principle, derive its required properties, explain how the major mechanisms realize them, follow one worked example, and state the important design intuition and limits. |
| Deep dive | Also teach each major mechanism through the five-beat arc of section 4—mismatch, resolution, quantitative closure, illustration, coda—plus phase and branch semantics, assumptions, and evidence boundaries stated inline. |

Before drafting, enumerate the major WHY questions in the live ledger. At Walkthrough and Deep dive, assess at least the applicable questions below independently; do not let one generic architecture picture silently close the internal mechanism questions.

| Visual slot ID | Candidate visual question | Typical semantic axis | Preferred form family |
|---|---|---|---|
| `why-unifying-idea` | What single idea unifies the system or model? | Conceptual composition or shared principle | Hub-and-spoke composition or conceptual map |
| `why-conceptual-architecture` | What conceptual parts exist, and what role does each play? | Mechanism hierarchy and responsibility | Layered mechanism or dependency map |
| `why-mechanism-deep-dive` | How does one mechanism realize its required property? | Interaction, transformation, or dependency | Annotated mechanism view, typed transformation, or dependency map |
| `why-worked-example` | How does a concrete example pass through the idea? | Worked conceptual trace | Storyboard, swimlane, or annotated trace |

These four stable IDs are the WHY template's visual coverage contract; seed all four into the ledger even when a section is later `not_applicable`. Applicability, disposition, deep-dive figure-first, and reuse rules live in [figure-workflow.md](figure-workflow.md). In the sections below, each conditional `when` is an applicability test for its named slot, not permission to skip the ledger row.

## 0. Reader promise and conceptual route

State:

- which governing principle the reader will understand;
- which derived requirements and which mechanisms the reader will be able to explain;
- what concrete example the reader will be able to follow;
- what this document leaves to WHAT and HOW.

The route is:

~~~text
governing principle → derived required properties
→ conceptual parts and their roles
→ mechanism internals (one per derived property)
→ worked example → tradeoffs, assumptions, and limits
~~~

Do not default to pressure → failed baseline → alternatives unless that is genuinely the clearest route for the subject.

## 1. The unifying idea

State the central idea in one precise sentence and one plain-language restatement. The unifying idea must be a principle about the domain or the mechanism that would remain true if this repository were deleted: a mathematical fact, a structural insight, an information or resource argument, or an invariance the design exploits. The repository and its artifacts are instances and evidence of that principle, not the principle itself. An experiment design, a benchmark setup, a project goal, or a configuration choice is never the unifying idea; when such a controlled comparison matters, it is reported with the evidence, not framed as the idea.

> Technical idea: ___

> Plain-language mental model: ___

Explain what is genuinely unified, what remains separate, and what the analogy helps the reader see. State where the analogy breaks.

Create a core-idea figure when several capabilities, stages, or outputs derive from one shared modeling principle.

<!-- visual-slot: why-unifying-idea -->
![Unifying model or system idea](<relative path to accepted .svg>)

## 2. From the principle to required properties

Derive the properties that any realization of the principle must have. Each property gets a one-paragraph argument that follows from the principle, not from the implementation. This derivation is the skeleton of the document: every mechanism section after it answers one of these properties, in the same order. If a mechanism answers no derived property, either the derivation is incomplete or the mechanism does not belong in this document.

| # | Required property | Why the principle demands it | Mechanism that realizes it |
|---|---|---|---|
|  |  |  |  |

## 3. Conceptual parts and their roles

Name parts by their conceptual responsibility, not their source location.

| Conceptual part or mechanism | Information it receives | Role in the idea | Information it exposes or changes | What it does not do |
|---|---|---|---|---|
|  |  |  |  |  |

Explain why the parts must be distinguished and which ones cooperate. A mechanism may be a model family, representation, state, routing rule, objective, scoring rule, control policy, or domain-specific operation; it need not correspond one-to-one with a class or module.

The slot is applicable when relationships among mechanism roles are material to explaining how the idea works. Do not label its figure with filenames or call stacks unless the user explicitly asks for implementation context.

<!-- visual-slot: why-conceptual-architecture -->
![Conceptual mechanism architecture](<relative path to accepted .svg>)

## 4. Mechanism internals, one per derived property

Use one subsection per required property derived in section 2, in the same order. Teach each mechanism as the resolution of a stated mismatch, in five beats. The beat names are authoring scaffold, not reader-facing vocabulary: in the delivered document, head each beat with a plain-language phrase the intended reader understands—for example, in Chinese, 差距在哪（mismatch）、怎么补上（resolution）、拿什么判定（quantitative closure）、图示（illustration）、职责边界（coda），and 容易误读的地方 for the closing misreading beat—keeping the same order and content. A reader who must decode the scaffold vocabulary before reading the argument has been handed the skeleton instead of the teaching.

1. **The mismatch.** Restate the derived property as a requirement, then show the structural reason the naive or default approach fails it—with both sides in the domain's precise terms (equations, norms, commutators, densities, or growth laws when available). The gap must be an object the reader can inspect, not an adjective.
2. **The mechanism as resolution.** Introduce the mechanism as the minimal structure that removes exactly this mismatch: what enters, what leaves or changes, and the governing formula, recurrence, or rule—with every symbol defined.
3. **Quantitative closure.** Close the argument with the quantity that decides it: receptive-field or information range versus domain scale, contraction or condition number, covariance or spectrum, asymptotic or exact complexity, conserved or broken quantity. The reader must be able to decide the claim from the stated quantity; a mechanism whose argument never becomes decidable does not meet `Deep dive`. When no honest quantity exists, state what would decide the claim and label the gap inline.
4. **The illustration.** An abstract illustration of the state or information change; for a mismatch-driven mechanism, the figure shows both sides of the mismatch with the deciding quantity annotated, per the expression rules in [figure-workflow.md](figure-workflow.md).
5. **The coda.** End with the one-sentence division of responsibility the mechanism establishes—what it does and what it deliberately leaves to the other parts—plus the invariant it must preserve.

Then resolve the reading a reader is most likely to get wrong, in the mechanism's own terms: an apparent contradiction (for example, nonlinear in one variable yet linear in another once the first is fixed), a misattributed distribution or role, a pair of objects that does not commute, or a borrowed classical structure—give the correspondence and state explicitly where it stops holding. Skip this beat only when no plausible misreading exists.

At `Deep dive`, a mechanism that carries the subject's main claim—the one the subject is named after, or the one its central advantage depends on—must be taught from first principles exactly as above. Prose alone cannot carry such a mechanism, and its visual slot may not resolve to `prose_or_table`; mark `unavailable` instead when evidence is missing.

Attach local design intuition immediately after the mechanism it explains. If a simple alternative, pressure, or tradeoff makes that mechanism clearer, explain it there in a short comparison; do not require a separate preliminary chapter. Where a representation change or a state transition is what makes the mechanism intelligible, show it inline here; do not create standalone representation-inventory or flow-retelling sections.

Split figures when two mechanisms require different reading paths or semantic axes; give each independent mechanism question its own `why-mechanism-deep-dive` instance (`#1`, `#2`, …). A generic box labeled core model, pipeline, engine, or algorithm is not internal-mechanism coverage.

<!-- visual-slot: why-mechanism-deep-dive -->
![Major mechanism deep dive](<relative path to accepted .svg>)

## 5. One worked conceptual example

Use the smallest realistic example that exercises the required properties, the mechanism interactions, and the final signal. Reuse the same objects across stages so the reader does not have to remap examples.

~~~text
concrete input
→ conceptual representation
→ state or information change in each major mechanism
→ intermediate signal
→ final result and interpretation
~~~

Mark illustrative values as illustrative. Never manufacture measured outcomes, benchmark effects, biological conclusions, or product behavior. If a worked example would be artificial, use an equivalent source-backed conceptual trace.

The slot is applicable when one shared example materially connects several transformations, mechanisms, stages, or branches. Decide figure versus prose only through the ledger disposition.

<!-- visual-slot: why-worked-example -->
![Worked conceptual trace](<relative path to accepted .svg>)

## 6. Design tradeoffs, concretely

Optional; include only choices that materially improve understanding of the mechanisms already taught. Every tradeoff must be concrete: a tiny numeric example, a small counterfactual illustration or figure, or a quoted measured effect with its evidence label. A bare benefit-versus-cost sentence or an abstract row in a table does not ship. Distinguish source-stated intent from explanatory inference; do not claim superiority, historical motivation, or an ablation result without evidence.

## 7. Assumptions and interpretation limits

Close with a compact prose statement: the assumptions the principle relies on, what the evidence does and does not establish, and the interpretation limits a reader must not cross. State known structural limitations with their mathematical form—a violated symmetry, homogeneity, conservation, or complexity law—rather than only in prose; a limit stated as an equation is worth a paragraph of hedging. Keep it to one short paragraph or a short list; no table, no appendix.

## Delivery test

Before delivery, test the guide against its reader promise and selected depth. An intended reader should be able to state the governing principle, reproduce the derivation of required properties, explain what each major mechanism contributes and which property it answers, and follow the worked example from semantic input to result. At Deep dive, the reader must also mentally simulate the applicable state changes, branches or phases, and preserved invariants. The reader should not need repository knowledge to do any of this. If the explanation stops making sense when the repository is removed, the idea has not been taught. If any section delivers no information gain over the sibling documents or the repository itself, remove the section.
