# Nutrition Ontology

The Nutrition ontology describes how protists acquire energy and carbon, capture resources, and interact nutritionally with other organisms.  
It captures **functional biology**, integrating traits from physiology, feeding, and ecological interactions.

---

## Features in Nutrition

Features define **what biological entity the trait applies to**.  
In nutrition, most traits are applied at the level of the **whole organism** or **cell**.

### Examples:

```yaml
- feature_id: organism
  label: Organism
  description: Whole living individual

- feature_id: cell
  label: Cell
  description: Single cell of the organism
```

Features anchor assertions so traits can be interpreted in the correct biological context.  

---

## Traits in Nutrition

Traits describe **properties related to nutrition**, independent of any specific organism.

### Examples of nutritional traits:

```yaml
- trait_id: energy_source
  label: Energy source
  description: Primary source of energy used by the organism
  value_type: categorical
  vocabulary: ontology/nutrition/vocabularies/energy_source.yaml

- trait_id: carbon_source
  label: Carbon source
  description: Primary source of carbon for biomass synthesis
  value_type: categorical
  vocabulary: ontology/nutrition/vocabularies/carbon_source.yaml

- trait_id: feeding_mechanism
  label: Feeding mechanism
  description: Mechanism by which resources are internalised
  value_type: categorical
  vocabulary: ontology/nutrition/vocabularies/feeding_mechanism.yaml

- trait_id: resource_capture
  label: Resource capture structures or processes
  description: Means by which external resources are accessed
  value_type: categorical
  vocabulary: ontology/nutrition/vocabularies/resource_capture.yaml

- trait_id: trophic_strategy
  label: Trophic strategy
  description: Integrated nutritional strategy of the organism
  value_type: categorical
  vocabulary: ontology/nutrition/vocabularies/trophic_strategy.yaml

- trait_id: symbiosis
  label: Nutritional symbiosis
  description: Nutritional dependence or association with other organisms
  value_type: categorical
  vocabulary: ontology/nutrition/vocabularies/symbiosis.yaml

- trait_id: mixotrophy_type
  label: Mixotrophy type
  description: Functional subtype of mixotrophy describing the balance and integration of phototrophic and phagotrophic nutrition
  value_type: categorical
  vocabulary: ontology/nutrition/vocabularies/mixotrophy_types.yaml
```

Traits are **feature-agnostic**: the same trait can apply to an organism or a single cell, depending on the context.

---

## Vocabularies

Controlled vocabularies define **the allowed values for categorical traits**, ensuring consistency across assertions and contributors.

### Example: `trophic_strategy.yaml`

```yaml
- autotroph
- heterotroph
- mixotroph
- photoautotroph
- chemoheterotroph
- saprotroph
- parasitotroph
- bacterivore
- eukaryvore
- omnivore
- fungivore
- detritivore
```

Other vocabularies include:

```yaml
- `energy_source.yaml` — e.g., light, chemical energy
- `carbon_source.yaml` — e.g., inorganic carbon, organic carbon
- `feeding_mechanism.yaml` — e.g., phagotrophy, osmotrophy
- `resource_capture.yaml` — e.g., cytostome, pseudopodia
- `mixotrophy_types.yaml` — e.g., constitutive, non-constitutive
- `symbiosis.yaml` — e.g., mutualistic, parasitic, commensal
```

---

## Example assertions in Nutrition

### Energy and carbon sources

```yaml
- feature: organism
  trait: energy_source
  value: chemotrophy
  qualifiers:
    evidence_method: inference

- feature: organism
  trait: carbon_source
  value: heterotrophy
  qualifiers:
    evidence_method: inference

### Feeding and resource capture

- feature: organism
  trait: feeding_mechanism
  value: phagotrophy
  qualifiers:
    evidence_method: light_microscopy

- feature: organism
  trait: resource_capture
  value: cytostome
  qualifiers:
    evidence_method: light_microscopy

### Trophic strategy and symbiosis

- feature: organism
  trait: trophic_strategy
  value: mixotroph
  qualifiers:
    evidence_method: inference
    evidence_basis: morphology

- feature: organism
  trait: symbiosis
  value: mutualistic
  qualifiers:
    evidence_method: literature
    source_id: yubuki_etal_2009
```

---

## Best practices for nutritional curation

1. **Select the correct feature first.**  
   Most nutritional traits apply at the organism level; some can also be applied to cells.

2. **Use controlled vocabularies whenever possible.**  
   Avoid free-text values for categorical traits.

3. **Attach qualifiers for context.**  
   Include evidence type, life stage, environment, or material if relevant.

4. **Distinguish observations from inferences.**  
   Use qualifiers like `evidence_method: inference` to indicate inferred traits.

5. **Document sources.**  
   Every assertion should be traceable to a publication or dataset.

---

**Summary:**  
The Nutrition ontology allows curators to capture **how protists acquire energy and nutrients, how they feed, and how they interact nutritionally with other organisms**.  
Combining features, traits, vocabularies, and qualifiers ensures that assertions are **precise, reproducible, and semantically meaningful**.
