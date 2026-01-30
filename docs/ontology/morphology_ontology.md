# Morphology Ontology

Morphology is one of the core domains in EukTrait.  
It describes the **form, structure, and organization of protist cells and organisms**.  
This domain is essential for understanding how organisms are built and how structures relate to function, behavior, and ecology.

---

## Features in Morphology

Features are the **biological entities or structures** being described.  
In morphology, features are typically **cellular or organismal structures**, but can also include extracellular components.

### Examples of key features

```yaml
    - feature_id: cell_body
      label: Cell body
      description: Main structural unit of the cell

    - feature_id: flagellum
      label: Flagellum
      description: Motile ciliary appendage

    - feature_id: plasma_membrane
      label: Plasma membrane
      description: Boundary membrane surrounding the cell

    - feature_id: cytostome
      label: Cytostome
      description: Cell mouth opening used for ingestion

    - feature_id: cilium
      label: Cilium
      description: Short motile appendage involved in movement or feeding
```

Features can also be **hierarchical**:

```yaml
    - feature_id: flagellum.anterior
      label: Anterior flagellum
      description: Front flagellum of the cell

    - feature_id: flagellum.posterior
      label: Posterior flagellum
      description: Rear flagellum of the cell
```

Hierarchical features allow precise assertions about **position and polarity** without creating redundant trait definitions.

---

## Traits in Morphology

Traits describe **properties of features**, independent of any particular organism.  
Morphological traits can be:

- **Boolean** — presence/absence
- **Measurement** — length, width, size
- **Categorical** — shape, type, composition
- **Integer** — counts of structures

### Examples of morphological traits

```yaml
    - trait_id: presence
      label: Presence
      value_type: boolean

    - trait_id: length
      label: Length
      value_type: measurement

    - trait_id: width
      label: Width
      value_type: measurement

    - trait_id: shape
      label: Shape
      value_type: categorical
      vocabulary: ontology/morphology/vocabularies/shape.yaml

    - trait_id: composition
      label: Composition
      value_type: categorical
      vocabulary: ontology/morphology/vocabularies/compositions.yaml

    - trait_id: count
      label: Count
      value_type: integer

    - trait_id: relative_length
      label: Relative length
      value_type: categorical
      vocabulary: ontology/morphology/vocabularies/relative_length.yaml
```

Traits are **feature-agnostic**: for example, `presence` applies to any structure, `length` can apply to a flagellum, cilium, or cell body.  
This keeps the ontology **flexible** and avoids combinatorial explosion.

---

## Vocabularies

Many morphological traits rely on **controlled vocabularies** to standardize values and avoid ambiguity.

### Examples:

- `shape.yaml` — possible values: `spherical`, `ovoid`, `elongated`, `filamentous`, etc.
- `compositions.yaml` — possible values: `proteinaceous`, `siliceous`, `cellulose-based`
- `relative_length.yaml` — possible values: `short`, `medium`, `long` (for comparisons between appendages)

Controlled vocabularies are **stored separately from traits** so they can be reused across features and domains.

---

## Example assertions in morphology

### Simple presence/absence

```yaml
    - feature: flagellum
      trait: presence
      value: true
      qualifiers:
        life_stage: active
        evidence_method: light_microscopy

### Measurements

    - feature: flagellum
      trait: length
      value: 12
      qualifiers:
        measurement_unit: μm
        evidence_method: electron_microscopy
        position: posterior

### Categorical trait with vocabulary

    - feature: cell_body
      trait: shape
      value: ovoid
      qualifiers:
        evidence_method: light_microscopy

### Combining count and relative features

    - feature: flagellum
      trait: count
      value: 2
      qualifiers:
        position: anterior
        evidence_method: light_microscopy

    - feature: flagellum
      trait: relative_length
      value: long
      qualifiers:
        reference: posterior_flagellum
        evidence_method: light_microscopy
```

These examples illustrate how **features, traits, and qualifiers** come together to form precise, interpretable assertions.

---

## Best practices for morphological curation

1. **Always select the correct feature** before applying a trait.  
   Hierarchical features help with position-specific data.

2. **Use existing traits and vocabularies** whenever possible.  
   Only add a new trait if no suitable trait exists.

3. **Attach qualifiers to capture context** (life stage, evidence method, position, polarity).

4. **Prefer precise measurements** over vague descriptors, but always note units and methods.

5. **Maintain provenance** by linking to sources and, where relevant, materials.

---

**Summary:**  
The Morphology ontology provides the **framework for capturing cell and organism structure**.  
By combining **features, traits, vocabularies, and qualifiers**, curators can record detailed, reproducible, and semantically precise information about protist morphology.  
