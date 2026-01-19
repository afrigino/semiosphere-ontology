# semiosphere-ontology

A theory-aligned OWL and SHACL ontology formalizing Juri Lotman’s semiosphere with enforceable computational guardrails.

This repository provides a computationally disciplined formalization of Juri Lotman’s theory of the semiosphere. It models culture as a semiotic system in which meaning is relational, boundaries are productive, heterogeneity is constitutive, and cultural change includes unpredictable “explosions.”

Unlike descriptive or reductionist ontologies, this project embeds theoretical constraints directly into machine-validated guardrails: models that violate the theory fail validation.

---

## What this repository contains

- **OWL vocabulary schema** (`ont/`)  
  Defines the core classes and relations of the semiosphere.

- **SHACL guardrails** (`shacl/`)  
  Enforces theoretical constraints such as:
  - Semiosphere as context (not entity)
  - Core/periphery as time-indexed roles
  - Asymmetric, non-invertible translation
  - Productive boundaries
  - Non-predictable cultural explosion

- **Executable validation tests** (`tests/`)  
  - `valid.ttl` must pass  
  - `invalid/*.ttl` must fail

- **Conceptual documentation** (`docs/`)  
  Overview, theory, modeling guidance, and diagrams.

- **Manifesto** (`MANIFESTO.md`)  
  A statement of scope, intent, and refusal of reductionism.

- **CI workflows** (`.github/workflows/`)  
  Continuous validation of theoretical integrity.

---

## Intended use

This ontology is intended for:

- Cultural and semiotic knowledge graphs  
- Digital humanities research  
- Ontology-driven constraint systems  
- Agentic or multi-system architectures  
- Theory-preserving computational modeling  

It is **not** intended for predictive cultural modeling or purely linguistic annotation.

---

## License

This repository is licensed under **Creative Commons Attribution 4.0 International (CC-BY-4.0)**.
Software implementations may reference or implement this work under their own licenses. See `LICENSE.md` for full terms.

---

## Citation

A DOI will be minted via Zenodo for tagged releases.  
Please cite the versioned DOI when referencing this work in publications.

---

## Status

This repository is intended to function as a **canonical, citable reference artifact**.  
Extensions and implementations should occur downstream, without altering the theoretical core.

---

## Contributing

To maintain the integrity of this canonical reference artifact, the `main` branch is protected. All changes must:

- Be submitted via pull request
- Pass all CI validation checks (SHACL validation, diagram rendering, and branch protection checks)
- Receive approval from code owners
- Maintain theoretical alignment with Lotman's semiosphere framework

See [`.github/BRANCH_PROTECTION.md`](.github/BRANCH_PROTECTION.md) for detailed branch protection configuration.
