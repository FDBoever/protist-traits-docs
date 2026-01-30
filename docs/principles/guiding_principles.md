# Guiding principles

The design of EukTrait is shaped by a small number of guiding principles. These are not implementation rules or technical constraints, but shared assumptions about how biological knowledge should be represented and maintained over time.

They exist to help contributors make consistent decisions, especially when extending the framework or resolving ambiguities.

---

## Biological knowledge is contextual

No biological statement is universally true.

Traits may vary with life stage, environment, strain, or experimental conditions. Even seemingly simple properties can depend on how and when they were observed.

For this reason, EukTrait does not treat traits as absolute facts. Every biological claim is expressed as an assertion with explicit context. When context is unknown or implicit in the source, this uncertainty is preserved rather than hidden.

---

## Claims matter more than conclusions

EukTrait represents what sources *say*, not what the framework believes to be true.

Different sources may describe the same organism in different ways, draw different conclusions from similar observations, or rely on different assumptions. These differences are informative and should be preserved.

Assertions are never silently merged or resolved. Agreement, conflict, and uncertainty are all part of the scientific record.

---

## Provenance is not optional

Every assertion must be supported by a source.

Provenance is not metadata added after the fact; it is a core part of the meaning of an assertion. Knowing *who* made a claim, *when*, and *on what basis* is essential for interpretation, reuse, and revision.

Assertions without sources are incomplete by definition.

---

## Ontologies define meaning, not truth

Ontologies in EukTrait are used to define concepts, relationships, and constraints. They exist to make assertions interpretable and comparable, not to encode biological facts.

Biological knowledge lives in assertion data, not in ontology class axioms. This separation allows ontologies to remain stable while the knowledge base evolves.

---

## Separate identity from observation

Taxa, materials, and biological traits represent different kinds of things and should not be conflated.

Taxa capture names and classifications. Materials represent physical biological entities such as strains or cultures. Traits describe biological properties. Observations and inferences connect these layers but do not collapse them.

Maintaining this separation allows data to be revised, reinterpreted, or extended without unintended consequences.

---

## Features and traits are distinct

A feature is what an assertion is about; a trait is what is being said about it.

Separating features from traits avoids combinatorial explosion, supports reuse, and allows traits to be applied consistently across different biological contexts. Traits are defined independently of the features they may be applied to, with applicability constrained semantically rather than hard-coded.

---

## Context modifies meaning, not structure

Qualifiers such as life stage, environmental condition, or evidence type modify how an assertion should be interpreted, but they do not define new traits themselves.

Contextual information is always attached to assertions, never baked into trait or feature definitions. This keeps the semantic core clean while allowing rich biological description.

---

## Materials are first-class entities

Whenever possible, assertions should apply to concrete biological materials rather than abstract taxa.

Strains, cultures, and isolates are the entities that are actually observed, sequenced, and experimented on. Treating materials as first-class entities allows EukTrait to represent biological variability, experimental reproducibility, and strain-specific traits without overgeneralization.

Taxon-level assertions are appropriate when supported by broader evidence, but they are not assumed by default.

---

## Design for change

EukTrait is built with the expectation that knowledge will change.

Taxonomies will be revised. New methods will appear. Old interpretations will be challenged. The framework should make such change visible and manageable rather than disruptive.

Design choices prioritize explicitness, modularity, and reversibility over compactness or convenience.

---

## Prefer clarity over cleverness

EukTrait favors structures that are easy to understand and explain, even if they are slightly more verbose.

The framework is intended for long-term community use by biologists, curators, and developers with different backgrounds. Clear semantics and transparent assumptions are more valuable than technically elegant shortcuts.

---

## Build for people, not just machines

Although EukTrait supports computational reasoning and integration, it is designed first for human understanding.

Assertions should be readable, interpretable, and justifiable by curators and domain experts. If a design choice makes the system harder to explain to a biologist, it should be reconsidered.

---

## A shared responsibility

EukTrait is a community effort. Its coherence depends on contributors making thoughtful, principled decisions and documenting their reasoning when extending or refining the framework.

These guiding principles are meant to support that shared responsibility, not to constrain it.
