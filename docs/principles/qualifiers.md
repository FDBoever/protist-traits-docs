# Qualifiers: adding context to assertions

In EukTrait, **qualifiers are how we capture context**.

Biological traits are rarely absolute. They often depend on:

- life stage
- environmental conditions
- experimental method or evidence type
- spatial or structural location
- inferred vs observed status

Qualifiers allow assertions to record these dependencies explicitly. They do **not** define new traits or features, and they do **not** change the structure of the assertion itself. Instead, they modify how the assertion should be interpreted.

---

## When to use qualifiers

You should add qualifiers whenever the trait is **conditional, partial, or otherwise context-dependent**. Here are the most common scenarios:

### 1. Life stage

Some traits are present only in specific stages of the organism’s life cycle.

    - feature: flagellum
      trait: presence
      value: true
      qualifiers:
        life_stage: active
        evidence_method: light_microscopy

Without the `life_stage` qualifier, the assertion might incorrectly imply that the flagellum is present in all stages.

### 2. Environmental conditions

Traits can depend on habitat, temperature, salinity, or light conditions.

    - feature: organism
      trait: growth_rate
      value: 0.8
      qualifiers:
        temperature: 20C
        medium: f2
        evidence_method: experimental_culture

Qualifiers preserve the experimental or natural context so results can be compared correctly.

### 3. Evidence type or method

It is important to distinguish **how** a trait was observed or inferred.

    - feature: organism
      trait: feeding_mechanism
      value: phagotrophy
      qualifiers:
        evidence_method: light_microscopy

    - feature: organism
      trait: energy_source
      value: chemotrophy
      qualifiers:
        evidence_method: inference
        evidence_basis: morphology

This distinction helps users evaluate confidence and reproducibility.

### 4. Spatial or structural localization

Sometimes traits are not uniform across the organism or its structures.

    - feature: flagellum
      trait: length
      value: 10
      qualifiers:
        position: anterior
        measurement_unit: μm
        evidence_method: electron_microscopy

Without specifying the location, an assertion could be misleading.

### 5. Polarity or relational qualifiers

Traits may be relative or comparative rather than absolute.

    - feature: flagellum
      trait: relative_length
      value: long
      qualifiers:
        reference: posterior_flagellum
        evidence_method: light_microscopy

This allows capturing statements like “the anterior flagellum is longer than the posterior one.”

---

## Practical guidelines

1. **Add qualifiers when the trait depends on context.**  
   Life stage, environment, method, or position are the most common reasons.

2. **Keep qualifiers structured and standardized.**  
   Use controlled vocabularies wherever possible. For example, `life_stage: cyst` instead of free text like “dormant form.”

3. **Do not create new traits for context.**  
   Qualifiers modify interpretation; they do not redefine biology.

4. **Use multiple qualifiers when needed.**  
   Many assertions require both life stage and evidence method, or environment and spatial position.

---

## Example: combining multiple qualifiers

    - feature: organism
      trait: feeding_mechanism
      value: phagotrophy
      qualifiers:
        life_stage: active
        evidence_method: light_microscopy
        environment: freshwater

This assertion clearly communicates *what was observed, in which stage, under which conditions, and how*.

---

**Summary:** Qualifiers are the keys to making assertions precise, interpretable, and trustworthy. They allow EukTrait to capture the true complexity of protist biology without turning the database into a flat or misleading summary.
