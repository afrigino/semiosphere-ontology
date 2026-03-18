# Semiosphere Ontology — Diagrams

These diagrams are rendered natively by GitHub from the Mermaid fenced blocks below.
No build step or CI pipeline is required.

---

## Diagram 1 — Conceptual Topology of the Semiosphere

Illustrates the relational structure of the semiosphere: heterogeneous semiotic systems, texts, boundaries, and translation processes operating within a contextual field, with a constructed outside.

```mermaid
flowchart TB
  subgraph S["SemiosphereContext\n(Contextual field — not an entity, not enumerable)"]
    direction TB

    subgraph SYS["Heterogeneous Semiotic Systems (plural)"]
      direction LR
      A["SemioticSystem A\n(PrimaryModelingSystem)"]
      B["SemioticSystem B\n(SecondaryModelingSystem)"]
      C["SemioticSystem C\n(Other code / language)"]
    end

    T["Text\n(coherent semiotic formation — Lotmanian sense)"]
    BD["Boundary\n(productive interface / bilingual filters)"]
    TR["TranslationProcess\n(invertible = false)\nsourceSystem ≠ targetSystem"]

    A -->|generates / contains| T
    B -->|interacts with| T
    BD -->|enablesTranslation| TR
    TR -->|transformsMeaningAcross| BD
    TR -->|sourceSystem| A
    TR -->|targetSystem| B
  end

  OUT["OutsideDomain / NonSemioticOutside\n(constructed outside; placeholder)\nNOT a populated world"]:::outside

  S ---|adjacentOutside| OUT

  classDef outside stroke-dasharray: 5 5;
```

---

## Diagram 2 — Core and Periphery as Time-Indexed Role Assignments

Shows that core and periphery are not fixed classes but reversible roles assigned to semiotic systems over time within a given semiosphere context.

```mermaid
gantt
  title Core and Periphery as Time-Indexed Role Assignments (not Fixed Classes)
  dateFormat  YYYY-MM-DD
  axisFormat  %Y-%m

  section SemiosphereContext ctx1
  RoleAssignment ra1: sysB assigned PeripheryRole   :a1, 2026-01-01, 2026-06-30
  RoleAssignment ra2: sysB assigned CoreRole        :a2, 2026-07-01, 2026-12-31

  section Guardrail
  Roles are reversible over time                    :milestone, m1, 2026-07-01, 0d
```

---

## Diagram 3 — Boundary and Translation Flow (Constraint Diagram)

Captures the required relations between Boundary, TranslationProcess, and SemioticSystems, along with the asymmetry and non-invertibility constraints.

```mermaid
flowchart LR
  BD["Boundary"] -->|enablesTranslation| TR["TranslationProcess"]
  TR -->|transformsMeaningAcross| BD

  TR -->|sourceSystem| SS["SemioticSystem (source)"]
  TR -->|targetSystem| TT["SemioticSystem (target)"]

  TR --- INV["invertible = false"]:::constraint
  TR --- ASYM["sourceSystem ≠ targetSystem"]:::constraint

  NOTE["Constraint diagram:\narrows represent required relations,\nnot causal sequence"]:::note

  classDef constraint stroke-dasharray: 5 5;
  classDef note stroke-dasharray: 3 3;
```

---

## Diagram 4 — OWL vs SHACL Layer Responsibilities

Maps the division of responsibility between the OWL vocabulary layer, the SHACL guardrails layer, and the CI test suite.

```mermaid
flowchart TB
  subgraph OWL["OWL Layer (Vocabulary)\nont/semiosphere.owl.ttl"]
    direction TB
    OWL1["Defines classes\n(SemiosphereContext, SemioticSystem, Text, Boundary, Process, Event)"]
    OWL2["Defines properties\n(dependsOnContext, boundedBy, enablesTranslation, etc.)"]
    OWL3["Conservative axioms / defaults\n(soft constraints)"]
  end

  subgraph SHACL["SHACL Layer (Guardrails)\nshacl/semiosphere.shacl.ttl"]
    direction TB
    S1["Semiosphere is Context\n(not SemioticEntity)"]
    S2["dependsOnContext required\nfor SemioticEntity"]
    S3["RoleAssignment time-indexing\n(core/periphery as roles)"]
    S4["Boundary ↔ Translation integrity\n+ invertible=false + asymmetry"]
    S5["Explosion predictable=false\n(post-hoc only)"]
    S6["Outside placeholder + heterogeneity\n+ boundary minimums"]
  end

  subgraph CI["Tests + CI"]
    direction TB
    V["tests/valid.ttl\nMUST PASS"]
    I["tests/invalid/*.ttl\nMUST FAIL"]
    R["Artifact: ALL_REPORTS.ttl\n(single consolidated report)"]
  end

  OWL -->|provides vocabulary| SHACL
  SHACL -->|validation authority| V
  SHACL -->|validation authority| I
  V --> R
  I --> R
```
