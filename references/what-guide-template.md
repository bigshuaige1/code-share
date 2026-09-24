# WHAT — Subject and Foundations Guide Template

Use this template for the WHAT track of a full project-sharing delivery, or when the user asks what a system, model, method, service, or pipeline is. The reader outcome is a working knowledge system of the domain plus confident recognition of the subject: the reader can explain the domain problem, its governing definitions and mathematics, why the problem is hard, and the landscape of approach families, then place the subject in that landscape and use its observable interface correctly.

Do not explain the internal model idea, conceptual representations, mechanism interactions, or signal formation; those belong in the [WHY guide](why-guide-template.md). Do not trace source architecture, concrete data/control flow, source paths, repository layout, runtime calls, setup, or reproduction; those belong in the [HOW guide](how-guide-template.md). Source anchors support facts but do not drive the section structure.

**The domain is the body of this document, not a preamble.** Build it as a knowledge system, the way a good textbook chapter does: every concept is introduced because a later concept needs it, each gets intuition first, then a precise definition, then its boundary, and the section closes able to answer why each idea exists and how the ideas relate. Subject-specific identification is compressed into a compact tail and must never crowd out the domain foundations. Every section must pass the information-gain rule in SKILL.md; state evidence status inline using its labels.

When the full set is delivered, add one sentence near the top linking to WHY for the core idea and conceptual mechanism design and HOW for implementation. This WHAT document must remain independently readable. Do not label any track as an appendix.

Maintain the shared author-only coverage ledger from [figure-workflow.md](figure-workflow.md) with `deliverable: what` or an explicit list of shared tracks and the selected WHAT depth. Reconcile WHAT coverage after its headings and prose stabilize. Reuse a figure from WHY or HOW only when it answers the same WHAT reader question at the selected depth.

## Depth contract

The selected depth changes how completely the reader can reconstruct the domain and classify the subject. It must not change WHAT into internal mechanism explanation or implementation tracing.

| Depth | Required WHAT outcome |
|---|---|
| `Walkthrough` | State the domain problem, identify the subject and its primary boundary, then teach the governing definitions, approach-family landscape, and relationships among major domain objects, with one concrete worked illustration when evidence permits. |
| `Deep dive` | Also teach the governing mathematics with every symbol defined, the structural source of difficulty, the domain formal objects and invariants, and the subject's instance parameters as a compact card. |

Before drafting, enumerate the major WHAT questions in the live ledger. At `Walkthrough` and `Deep dive`, assess at least the applicable questions below independently; do not let one generic subject overview silently close them all.

| Visual slot ID | Candidate visual question | Typical semantic axis | Preferred form family |
|---|---|---|---|
| `what-domain-landscape` | Where does the subject sit in its domain, and what surrounds it? | Context and boundaries | Context or nested boundary map |
| `what-concept-relations` | How do the core terms or domain objects relate? | Concept hierarchy or relationships | Concept map, relationship graph, or tree |
| `what-subject-context` | What is in scope, and which adjacent categories are commonly confused with it? | Category boundary and contrast | Boundary map, nested map, or evidence-backed overlap view |
| `what-observable-contract` | What may enter and emerge at the observable boundary? | Contract or representation mapping | Paired input/output or interface schematic |
| `what-variant-taxonomy` | How are families, variants, or operating forms organized? | Taxonomy or crossed classification | Taxonomy tree or classification matrix |

These five stable IDs are the WHAT template's visual coverage contract; seed all five into the ledger even when a section is later `not_applicable`. Applicability, disposition, deep-dive figure-first, and reuse rules live in [figure-workflow.md](figure-workflow.md). In the sections below, each conditional `when` is an applicability test for its named slot, not permission to skip the ledger row.

## 0. Reader promise and route

State in plain language:

- what domain the reader will understand and what they will then be able to recognize;
- what prior knowledge is and is not assumed;
- which background concepts are genuinely necessary;
- what this document leaves to WHY and HOW.

Suggested route:

```text
domain problem → governing definitions and mathematics → why it is hard
→ approach-family landscape → vocabulary and domain objects
→ subject card → observable contract
```

## 1. Domain background and foundations

This section is the body of the document. Teach the domain itself before the subject. It must stand without the repository: a reader new to the domain should learn what problem class is being solved, the definitions every serious treatment relies on, and why the problem is technically hard. Do not reduce this section to placing the repository in a technology stack.

The foundations must assemble into a visible system, not a sequence of topics: by the end of the section the reader can redraw the domain's concept dependency skeleton—which concept presupposes which—and locate where the difficulty lives in that structure. Keep the altitude uniform until the system stands; do not zoom into any single object before its position in the system is visible.

Teach every skeleton step concretely, not only definitionally: each step gets at least one inspectable anchor—a constructed micro-example with real numbers, a quantified difficulty (a condition number, a cost law, a cardinality), or one fully computed instance—so the reader learns the system through objects they can check by hand. A foundations section that only names and defines, however precise, leaves the reader able to recite but not to reconstruct. At `Walkthrough` depth and above, this section is normally the document's largest; if the subject-identification tail outweighs the foundations body, the document has inverted its contract.

Cover, as applicable:

1. **The domain problem.** What real-world or technical problem class the subject addresses, what information exists before a system acts, and what result a consumer needs.
2. **Governing definitions and mathematics.** The domain's canonical definitions, equations, or laws, with every symbol defined. For a mathematical or computational domain, state the governing equations themselves rather than only naming them. Repository configuration values never substitute for domain formal objects.
3. **Why the problem is hard.** The structural source of difficulty—scale, asymptotic cost, memory or bandwidth limits, statistical limits, concurrency, or similar—and the standard way the domain frames that difficulty.
4. **The domain landscape.** The major approach families or adjacent problem classes, and where the subject sits among them.

Keep history, literature review, and design comparison out unless required to define the domain or the object. A concrete worked illustration of the domain objects may live here inline when it helps recognition; it does not need its own section.

| Background question | Reader-facing answer |
|---|---|
| What domain problem is being solved, and for whom? |  |
| Which definitions, equations, or laws govern this domain? |  |
| What makes the problem hard at a structural level? |  |
| Which domain distinction would a newcomer otherwise miss? |  |

When the domain contains several approach families, actors, information sources, or adjacent problem classes, create a domain-landscape figure. Keep it observational: show what exists and where the subject class sits, not why its mechanisms were chosen or how code executes.

<!-- visual-slot: what-domain-landscape -->
![Domain landscape](<relative path to accepted .svg>)

## 2. Vocabulary and domain objects

Define terms before first use, domain terms before repository terms. Give a plain-language intuition, then the precise meaning in this domain, then the boundary of the analogy. Where the domain allows, make the definition decidable: give a membership criterion—a condition, an equation, or a construction—that lets the reader classify a new instance on their own, not only a description to recognize. And when an object can be constructed from the problem's structure rather than stipulated, show the construction before naming it: an object derived from the problem reads as necessary; one that is merely named reads as arbitrary. Repository-specific values appear only as instances of domain terms, never as definitions.

| Term | Plain-language intuition | Precise meaning here | Not the same as |
|---|---|---|---|
|  |  |  |  |

Do not assume that common terms such as token, state, embedding, checkpoint, request, transaction, schema, artifact, or metric are self-explanatory for the intended audience.

At `Walkthrough` or `Deep dive`, the slot is applicable when composition, containment, hierarchy, correspondence, cardinality, or mutually exclusive categories are material to recognizing the subject. When prerequisite structure is material to the reader question, its figure encodes which concept presupposes which, per the expression rules in [figure-workflow.md](figure-workflow.md). Decide figure versus non-figure only through the ledger disposition.

<!-- visual-slot: what-concept-relations -->
![Concept and object relationships](<relative path to accepted .svg>)

For `Deep dive`, add the applicable formal object definitions in two layers, without introducing implementation variables: first the domain formal objects—the mathematical or schema objects and invariants that define the problem class and would exist without this repository—then the subject's instance parameters (this artifact's concrete values, shapes, or configuration) as instances of them. A table of repository hyperparameters alone does not discharge the domain layer. Quantify the concrete instance when one exists: cardinalities, proportions, and scales of the actual data or objects (for example, how many points fall in each category), so the reader can judge which cases dominate.

| Object or field | Formal type/schema | Unit, range, or cardinality | Invariant | Related object |
|---|---|---|---|---|
|  |  |  |  |  |

## 3. The subject card

Identify the subject in one compact section, not a chapter:

> **Technical definition:** ___

> **Plain-language restatement:** ___

| In scope | Out of scope or commonly confused |
|---|---|
|  |  |

Include variants, families, or operating forms only when they materially change what the subject is or what it can do; define the axes that distinguish them, the shared core, and combinations that do not exist. Capability or guarantee notes belong here only as brief scope statements with evidence status inline; do not build a separate guarantees inventory.

The `what-subject-context` slot is applicable when the in-scope boundary and commonly confused categories form a material category relationship. Do not overload its figure with the concept graph, input/output contract, and variant taxonomy merely to reduce asset count.

<!-- visual-slot: what-subject-context -->
![Subject context](<relative path to accepted .svg>)

The `what-variant-taxonomy` slot is applicable when branches or crossed classification axes materially distinguish the shared core and variant differences. Decide figure versus table only through the ledger disposition.

<!-- visual-slot: what-variant-taxonomy -->
![Family and variant taxonomy](<relative path to accepted .svg>)

## 4. Inputs, outputs, and observable contract

Describe what enters and what becomes externally visible without tracing the implementation between them.

| Contract item | Meaning | Example or shape/schema | Evidence |
|---|---|---|---|
| Input |  |  |  |
| Context or configuration |  |  |  |
| Output |  |  |  |
| Side effect, if any |  |  |  |
| Consumer |  |  |  |

Define units, score direction, labels, and evidence status where they are part of recognizing the output. Leave conceptual signal formation and mechanism flow to WHY, and concrete computation and runtime mapping to HOW.

When multiple representations, modalities, schemas, units, or consumer-visible result forms must be matched, create an observable-contract figure. Show boundary mappings only; omit internal transformations.

<!-- visual-slot: what-observable-contract -->
![Observable input and output contract](<relative path to accepted .svg>)

For `Deep dive`, make compatibility and interpretation constraints explicit:

| Contract dimension | Allowed form | Invariant or compatibility rule | Invalid or ambiguous case |
|---|---|---|---|
|  |  |  |  |

## Delivery test

Before delivery, test the guide against its reader promise and selected depth. A reader new to the domain must first be able to restate the domain problem, its governing definitions or equations, why the problem is hard, and the major approach families, and to redraw the dependency skeleton of the domain's core concepts—which concept presupposes which. They must then be able to define the subject, use its vocabulary correctly, identify inputs and outputs, distinguish variants, and state the main boundary without consulting WHY or HOW. Then apply the information-gain test to every section: if deleting the section loses nothing the reader could not already get from the sibling documents or the repository itself, delete the section.
