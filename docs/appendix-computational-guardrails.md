# Appendix: Computational Guardrails and Interpretive Constraints

This appendix specifies the **computational guardrails** and
**interpretive constraints** governing the Semiosphere Ontology. Its
purpose is to make explicit which aspects of Juri Lotman’s theory are
enforced computationally, which are constrained interpretively, and
which are intentionally left irreducible.

This appendix is normative. It does not offer optional guidance; it
documents binding constraints and the theoretical reasons for them.

Guardrail identifiers (C1–C12) correspond directly to SHACL constraint
groups defined in `shacl/semiosphere.shacl.ttl`.

---

## A. Purpose of Guardrails

The ontology does not attempt to model culture exhaustively or
predictively. Instead, it establishes **guardrails**: constraints that
prevent computational representations from violating foundational
semiotic principles.

Each guardrail serves three functions:

1. **Negative constraint** — forbids theoretically invalid modeling moves  
2. **Positive structure** — channels modeling into theory-compatible forms  
3. **Epistemic boundary** — marks where computation must stop

Guardrails are enforced through SHACL rather than OWL to preserve a
permissive vocabulary while maintaining strict validation discipline.

---

## B. Semiosphere as Context, Not Entity (C1)

**Statement**  
The semiosphere is modeled as a contextual field (`SemiosphereContext`),
not as a semiotic entity.

**Theoretical basis**  
For Lotman, the semiosphere is ontologically prior to languages, texts,
and codes. It is the condition of their existence, not one object among
others.

**Computational expression**  
- SHACL forbids `SemiosphereContext` from also being a `SemioticEntity`
- All semiotic entities must reference a semiosphere context

**Not claimed**  
The ontology does not attempt to enumerate or bound the semiosphere as a
dataset.

---

## C. Dependence of Semiotic Entities on Context (C2)

**Statement**  
Every semiotic entity must explicitly depend on a semiosphere context.

**Theoretical basis**  
Meaning is not intrinsic to isolated objects; it arises only within a
semiotic space that enables interpretation and translation.

**Computational expression**  
- SHACL requires `dependsOnContext` for all `SemioticEntity` instances

**Not claimed**  
Dependence does not imply determinism or total explanation.

---

## D. Core and Periphery as Time-Indexed Roles (C3)

**Statement**  
Core and periphery are modeled as time-indexed roles, not fixed classes.

**Theoretical basis**  
Lotman emphasizes the historical reversibility of cultural dominance.
What is central can become marginal, and vice versa.

**Computational expression**  
- Core/periphery represented via `RoleAssignment`
- Role assignments require explicit `timeStart` and `timeEnd`
- Direct instantiation of core or periphery is forbidden

**Not claimed**  
Core status does not imply value, correctness, or superiority.

---

## E. Boundary as Productive Interface (C4)

**Statement**  
Every boundary must enable translation and mediate at least one process.

**Theoretical basis**  
Boundaries are sites of meaning production, not passive separators.

**Computational expression**  
- SHACL requires `enablesTranslation` for each `Boundary`
- Boundaries must mediate a `Process`

**Not claimed**  
Translation is not assumed to be neutral or lossless.

---

## F. Translation as Asymmetric and Non-Invertible (C5)

**Statement**  
Translation is asymmetric and non-invertible by default.

**Theoretical basis**  
Lotman rejects the notion of perfect equivalence between semiotic
systems; translation transforms meaning.

**Computational expression**  
- `invertible = false` required
- Source and target systems must be distinct
- Bidirectional integrity between boundary and translation enforced

**Not claimed**  
Approximate reversibility is not denied; *assumed* reversibility is.

---

## G. Dialogue as Memory-Bearing Process (C6)

**Statement**  
Dialogue is modeled as a process with memory.

**Theoretical basis**  
Dialogue is historically situated and accumulates asymmetry over time.

**Computational expression**  
- SHACL requires `hasMemory = true` for all `DialogueProcess` instances

**Not claimed**  
The ontology does not prescribe how memory is implemented.

---

## H. Explosion as Post-Hoc Event (C7)

**Statement**  
Cultural explosions are unpredictable and identifiable only
retrospectively.

**Theoretical basis**  
Lotman explicitly rejects predictive models of cultural rupture.

**Computational expression**  
- `predictable = false` required
- Explosion events must generate at least one `Text`

**Not claimed**  
The ontology does not simulate or forecast explosions.

---

## I. Nonsemiotic Outside as Constructed Limit (C8)

**Statement**  
The outside of the semiosphere is modeled as a constructed placeholder,
not as a populated domain.

**Theoretical basis**  
The semiosphere constructs its own notion of what lies beyond meaning.

**Computational expression**  
- At most one outside placeholder per semiosphere
- Outside entities may not be semiotic entities

**Not claimed**  
Objective, mind-independent reality is not modeled here.

---

## J. Heterogeneity as Mandatory Condition (C10)

**Statement**  
A semiosphere must contain at least two distinct semiotic systems.

**Theoretical basis**  
Meaning arises from difference and polyglotism, not monoliths.

**Computational expression**  
- SHACL enforces a minimum of two `SemioticSystem` instances per context

**Not claimed**  
The ontology does not constrain system types beyond this minimum.

---

## K. Relational Meaning and Anti-Reductionism (C9, C12)

**Statement**  
Meaning is modeled relationally, not as an intrinsic property.

**Theoretical basis**  
Semiotic meaning emerges from relations, translation, and dialogue.

**Computational expression**  
- Intrinsic meaning properties are discouraged or forbidden
- Object relations are favored over literals

**Not claimed**  
Material substrates are not denied; reductionism is.

---

## L. Final Constraint

This ontology does not explain culture.

It constrains how culture may be represented computationally without
violating semiotic theory.

A model that passes validation has accepted these constraints.
A model that fails has encountered a theoretical boundary.

That boundary is not a limitation. It is the point.
