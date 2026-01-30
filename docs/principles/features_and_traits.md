# Features and Traits

At the heart of every EukTrait assertion are **features** and **traits**.  
Together, they define *what* is being described and *what property* is being claimed.  

Understanding the distinction is essential for contributors and curators.

---

## Features: the biological targets

A **feature** is the entity or structure that a trait describes.  
Features are biological “things” rather than properties. They are usually domain-specific, but can appear in multiple contexts.

Examples of features:

- organism (the whole living individual)
- cell (single cell of the organism)
- flagellum (motile appendage)
- habitat (environmental setting)
- nucleus (genome-related structure)

Features provide the **semantic anchor** for assertions. They answer the question:

> *“What part of biology is being described?”*

---

## Traits: properties applied to features

A **trait** is a measurable, observable, or inferable property of a feature.  
Traits are **feature-agnostic**: the same trait can apply to different features across domains, depending on semantics.

Examples of traits:

    - trait_id: presence
      label: Presence
      value_type: boolean
    - trait_id: length
      label: Length
      value_type: measurement
    - trait_id: trophic_strategy
      label: Trophic strategy
      value_type: categorical
      vocabulary: ontology/nutrition/vocabularies/trophic_strategy.yaml

Traits define **what is being said about the feature**, not the feature itself.

---

## The feature–trait separation

Separating features from traits is one of the **core design principles** of EukTrait:

- **Avoids combinatorial explosion**: we don’t need a separate trait for “length of flagellum” and “length of cilium”; one trait can apply to both features.
- **Supports reuse**: traits like `presence`, `composition`, or `energy_source` can be applied across multiple features or domains.
- **Maintains clarity**: features define *what*, traits define *what property*, and qualifiers define *under what conditions*.

---

## Value types and vocabularies

Traits have a **value type** that determines what kind of data can be recorded:

- boolean (true/false)
- integer (countable quantities)
- measurement (numerical with units)
- categorical (selected from a controlled vocabulary)
- string (free text)

Many categorical traits are linked to **controlled vocabularies** to ensure consistency:

    - trait: trophic_strategy
      value: mixotroph
      qualifiers:
        evidence_method: inference

Controlled vocabularies are stored separately from traits so that they can be reused and extended independently.

---

## Qualifiers modify traits, not features

Qualifiers like life stage, environment, evidence type, or position always attach to **assertions**, modifying how a trait should be interpreted. They never become part of the trait or feature definition itself.

Example:

    - feature: flagellum
      trait: length
      value: 12
      qualifiers:
        position: posterior
        life_stage: active
        measurement_unit: μm

Here, the feature is `flagellum`, the trait is `length`, and the qualifiers describe context.

---

## Examples of assertions combining features and traits

**Morphology example:**

    - feature: flagellum
      trait: presence
      value: true
      qualifiers:
        life_stage: active
        evidence_method: light_microscopy

**Nutrition example:**

    - feature: organism
      trait: trophic_strategy
      value: mixotroph
      qualifiers:
        evidence_method: inference
        evidence_basis: morphology

**Ecology example:**

    - feature: habitat
      trait: habitat_type
      value: freshwater
      qualifiers:
        evidence_method: observation

---

## Best practices

1. **Identify the correct feature** before applying a trait.  
   Features are the semantic anchor for assertions.

2. **Reuse existing traits whenever possible.**  
   Only define new traits when there is no suitable existing trait.

3. **Use vocabularies to standardize values.**  
   Categorical traits should reference controlled vocabularies to ensure consistency.

4. **Attach qualifiers appropriately.**  
   Contextual information goes with the assertion, not the trait.

---

**Summary:** Features define *what is being described*, traits define *what is being said about it*, and qualifiers define *under what conditions*.  
Together, they form the semantic core of EukTrait assertions, enabling precise, reusable, and interpretable representation of biological knowledge.
