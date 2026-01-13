# Modeling Guidelines

This document explains how Lotman’s theory is operationalized without distortion.

---

## Semiosphere as Context

The semiosphere is modeled as `SemiosphereContext`, not as a normal entity.
All semiotic entities must explicitly depend on it.

This prevents detached or decontextualized modeling.

---

## Core and Periphery

Core and periphery are modeled as **roles**, not fixed classes.

- Assigned via `RoleAssignment`
- Time-indexed
- Reversible

This enforces historical dynamism.

---

## Boundaries and Translation

Every boundary must:
- Enable translation
- Mediate at least one process

Every translation must:
- Be asymmetric
- Be non-invertible
- Occur within a semiosphere

---

## Dialogue

Dialogue is modeled as a process with memory.
It is not a message exchange or transaction.

---

## Explosion

Explosions are modeled as events that:
- Are explicitly unpredictable
- Generate texts or structural change
- Cannot be forecast by rules

---

## Validation Philosophy

OWL defines what exists.
SHACL defines what is allowed.

If SHACL fails, the model is wrong.
