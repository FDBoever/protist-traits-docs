# EukTrait Ontologies Overview

EukTrait organizes knowledge about protist biology through a **structured set of ontologies**.  
These ontologies define **what can be described**, **how it can be described**, and **how assertions are semantically linked**.

While the Principles section explains *why* the framework is structured this way, this Ontologies section explains *what the ontologies are* and *how they fit together*.

---

## Ontology types in EukTrait

EukTrait ontologies fall into two main categories:

1. **Trait-based ontologies**  
   These describe **biological features and properties** that can be asserted about organisms.  
   Each domain contains:
   - **Features** — entities or structures being described
   - **Traits** — properties applied to features
   - **Vocabularies** — controlled value sets for categorical traits

   Examples of trait-based domains:
   - Morphology: cell shape, appendages, coverings
   - Nutrition: energy sources, feeding strategies, symbiosis
   - Ecology: habitat, substrate, environmental tolerances
   - Physiology, Behavior, Life history, Genome, Sequence

2. **Non-trait ontologies**  
   These describe **structural or contextual entities** that support assertions but are not traits themselves:
   - **Taxa** — biological concepts, lineages, nomenclatural hierarchy
   - **Materials** — strains, cultures, isolates, or specimens
   - **Sources** — bibliographic references or other provenance for assertions

   These ontologies ensure that every assertion is anchored in a **biological entity** and **traceable to a source**.

---

## Modular domain structure

Each trait-based ontology is organized into **domains**, which are:

- **Independent** — each domain evolves on its own timeline
- **Interoperable** — features, traits, and vocabularies can reference each other across domains
- **Extensible** — new features, traits, or vocabularies can be added without breaking existing data

Example: the morphology domain contains features such as `flagellum` and `cell_body` and traits such as `presence`, `length`, and `shape`.

---

## How features, traits, and vocabularies interact

- **Features** define *what* is being described (e.g., `flagellum`, `nucleus`, `habitat`)
- **Traits** define *what property* is being asserted about the feature (e.g., `length`, `presence`, `trophic_strategy`)
- **Vocabularies** constrain the allowed values for categorical traits, ensuring consistency

Example assertion connecting them:

    - feature: flagellum
      trait: presence
      value: true
      qualifiers:
        life_stage: active
        evidence_method: light_microscopy

Here, `flagellum` is the feature, `presence` is the trait, and the qualifiers provide context.

---

## Non-trait ontologies in action

Non-trait ontologies provide **structure and provenance**:

    taxon_id: rictus_lutensis
    source_id: yubuki_etal_2009
    material_id: RCC299

- `taxon_id` links assertions to the biological concept.
- `source_id` ensures traceability.
- `material_id` allows capturing observations at the strain or culture level.

These layers are crucial for maintaining **reproducibility, accuracy, and contextual integrity**.

---

## Summary

EukTrait ontologies form a **cohesive framework**:

- Trait-based ontologies capture the *biology* of features and traits across domains.
- Non-trait ontologies capture the *context* and *provenance* of observations.
- Modular design, feature–trait separation, and controlled vocabularies ensure **clarity, reusability, and long-term maintainability**.

Together, these ontologies provide the **semantic backbone** for assertions, synthesis, and downstream analyses.
