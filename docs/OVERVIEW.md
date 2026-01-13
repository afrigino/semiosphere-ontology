# Semiosphere Ontology — Overview

This project provides a computationally disciplined formalization of Juri Lotman’s theory of the semiosphere using OWL (vocabulary) and SHACL (enforcement).

The ontology is designed to make explicit:
- What aspects of semiosphere theory can be modeled
- What aspects must remain constrained, non-predictive, or irreducible
- How computational systems can participate in semiotic modeling without violating theory

This is not a data model of culture.
It is a constraint system for meaning-making systems.

---

## What This Is

- A theory-aligned ontology for cultural semiotics
- A guardrailed knowledge-graph foundation
- A reusable research and infrastructure artifact
- A reproducible reference for interdisciplinary work

---

## What This Is Not

- A predictive model of culture
- A semantic labeling scheme
- A reduction of meaning to data
- A general NLP ontology

---

## Core Design Principle

**If a computational system violates Lotman’s theory, it must fail validation.**

This principle governs the entire architecture.

---

## Repository Structure

- `ont/` — OWL/Turtle vocabulary and semantics
- `shacl/` — Enforced theoretical guardrails
- `tests/` — Executable examples (valid and invalid)
- `.github/workflows/` — Continuous validation
- `docs/` — Theory, modeling, and rationale

---

## Status

This ontology is stable, conservative, and intentionally extensible.
