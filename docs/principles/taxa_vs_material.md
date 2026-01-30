# Taxon vs Material: deciding where assertions apply

In EukTrait, every assertion must be anchored to a **biological entity**. That entity can be:

- a **taxon** (an abstract biological concept), or
- a **material** (a concrete biological instance such as a culture, strain, or isolate).

Choosing the correct level is critical for accurately representing biology and preserving context.

---

## Taxon-level assertions

Taxon-level assertions describe traits that are **generalized across all members** of a taxon or for which no specific material evidence exists.

Use taxon-level assertions when:

- the trait applies broadly to the species or higher rank,
- no specific strain or culture was examined,
- multiple observations from different materials support a general statement,
- the assertion describes taxonomy, nomenclature, or type designations.

### Examples

    - trait: parent_taxon
      value: Bicosoecida
      qualifiers:
        rank: order
        authority: Karpov, 1998

    - trait: etymology
      value: "Rictus = 'opened mouth'"
      qualifiers:
        name_part: genus

These assertions describe the taxon concept itself and do not refer to a specific specimen or culture.

---

## Material-level assertions

Material-level assertions describe traits observed or measured on a **specific biological instance**.

Materials can be:

- cultures or strains,
- environmental isolates,
- or voucher specimens.

Use material-level assertions when:

- the observation is made on a specific strain or isolate,
- the trait varies between strains or conditions,
- experimental or environmental context is important,
- you want to capture intraspecific variability.

### Example

    applies_to:
      material_id: RCC299
    feature: organism
    trait: feeding_mechanism
    value: phagotrophy
    qualifiers:
      life_stage: active
      evidence_method: light_microscopy
      environment: freshwater

This assertion makes it clear *which biological instance was observed*, under *what conditions*, and *how*.

---

## How qualifiers interact with taxon and material levels

Qualifiers are always attached to assertions to describe context. Their role is the same regardless of taxon or material level:

- Life stage, environmental conditions, or evidence type can be recorded at both levels.
- Material-level assertions often require more detailed qualifiers, since the instance may have been measured under specific laboratory conditions.
- Taxon-level assertions can have qualifiers indicating generality, inferred status, or sources used to make a generalized claim.

### Example: taxon-level inference

    - trait: energy_source
      value: chemotrophy
      qualifiers:
        assertion_type: inferred
        evidence_basis: morphology
        generality: species-wide

This distinguishes a generalized, inferred statement from a direct measurement on a material.

---

## Practical guidelines

1. **Ask what was actually observed.**  
   If it was a specific strain or culture, assert at the material level.

2. **Ask whether the trait is generalizable.**  
   If multiple sources, materials, or observations consistently indicate the trait, it can be asserted at the taxon level.

3. **Use qualifiers liberally.**  
   Life stage, environment, evidence type, and inference status clarify applicability and confidence.

4. **Never assume taxon-level applicability from a single material.**  
   Only generalizations explicitly supported by multiple observations or sources should be asserted at the taxon level.

---

## Summary

- **Materials** = concrete, observed, context-rich.  
- **Taxa** = abstract, general, historical/conceptual.  
- **Qualifiers** = describe the conditions and context that shape the observation.  

Using these distinctions consistently ensures that EukTrait reflects both the **real biological variability** and the **conceptual structure of taxonomy**, while keeping assertions precise, traceable, and interpretable.
