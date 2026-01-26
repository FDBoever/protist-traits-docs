# Ecology Ontology

## Overview

The **Ecology ontology** captures where and how a protist organism occurs in its environment, and how it interacts with abiotic and biotic ecological contexts.

This domain is concerned with **environmental association**, not intrinsic biological mechanisms. It complements, but does not overlap with, morphology, physiology, nutrition, behavior, or life-history ontologies.

All ecological information is expressed as **assertions**, each linked to:
- a **taxon**
- a **source**
- a defined **feature–trait–value** structure

---

## Scope and Design Principles

### What this ontology covers

The ecology ontology models:

- Habitat occupancy (e.g. marine, freshwater, terrestrial)
- Abiotic tolerance ranges (e.g. temperature, salinity, light)
- Trophic ecological roles (not mechanisms)
- Substrate association
- Symbiotic ecological context
- Dispersal ecology

### What this ontology does *not* cover

- Morphological adaptations (→ morphology)
- Physiological performance (→ physiology)
- Feeding mechanisms or nutrition sources (→ nutrition)
- Life cycle timing or stages (→ life_history)
- Genetic or genomic traits (→ genome, sequence)

This separation ensures **conceptual clarity** and avoids trait duplication across domains.

---

## Conceptual Model

Ecological assertions follow the shared framework:


---

## Features

Features represent **ecological dimensions** of an organism’s existence.

### Defined Features

| Feature ID | Description |
|----------|------------|
| `habitat` | Broad environmental setting in which the organism occurs |
| `abiotic_tolerance` | Environmental limits or preferences |
| `substrate` | Physical or biological surface associated with the organism |
| `trophic` | Ecological trophic role or strategy |
| `symbiosis` | Ecological association with other organisms |
| `dispersal` | Mode of ecological dispersal |

Features are **not taxa-specific** and may apply to many organisms.

---

## Traits

Traits describe **properties of ecological features**.

### Habitat traits

| Trait ID | Description | Value type |
|--------|-------------|------------|
| `type` | Habitat classification | categorical |

Vocabulary:
- `ontology/ecology/vocabularies/habitat_types.yaml`

---

### Abiotic tolerance traits

| Trait ID | Description | Value type |
|--------|-------------|------------|
| `temperature_tolerance` | Temperature range tolerated | measurement |
| `salinity_tolerance` | Salinity range tolerated | measurement |
| `light_preference` | Light regime preference | categorical |

Vocabularies:
- `light_preferences.yaml`

Measurements use **fixed units** and represent observed or inferred tolerances.

---

### Substrate traits

| Trait ID | Description | Value type |
|--------|-------------|------------|
| `type` | Substrate association | categorical |

Vocabulary:
- `substrate_types.yaml`

---

### Trophic ecology traits

| Trait ID | Description | Value type |
|--------|-------------|------------|
| `mode` | Ecological trophic mode | categorical |
| `feeding_strategy` | Ecological feeding strategy | categorical |

Vocabularies:
- `trophic_modes.yaml`
- `feeding_strategies.yaml`

Note: These traits describe **ecological roles**, not cellular mechanisms.

---

### Symbiosis traits

| Trait ID | Description | Value type |
|--------|-------------|------------|
| `type` | Type of symbiotic association | categorical |

Vocabulary:
- `symbiotic_types.yaml`

---

### Dispersal traits

| Trait ID | Description | Value type |
|--------|-------------|------------|
| `mode` | Ecological dispersal mode | categorical |

Vocabulary:
- `dispersal_modes.yaml`

---

## Qualifiers

Ecological assertions may be qualified using shared qualifier ontologies, including:

- `evidence` — how the ecological information was determined
- `condition` — environmental or experimental context
- `context` — ecological or geographic constraints

Life stage qualifiers are generally **not required**, as ecological traits are often species-level summaries.

---

## Example Assertions

### Habitat example

```yaml
- feature: habitat
  trait: type
  value: marine
  qualifiers:
    evidence: literature
```

