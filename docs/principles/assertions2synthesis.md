# From assertions to synthesis

EukTrait preserves biological knowledge as a collection of **assertions**, each tied to a taxon or material, a feature, a trait, and a source.  
But scientists rarely want to read raw assertions one by one. They want **synthesized information**: summaries of what is known about a species, trait distributions, or ecological patterns.

This page describes how assertions can be aggregated and interpreted conceptually, while still respecting provenance, context, and variability.

---

## The challenge of synthesis

Biological knowledge is rarely simple:

- Traits vary between life stages, environments, and strains.
- Different sources may make conflicting claims.
- Some traits are observed directly, others are inferred.

Simply collapsing assertions into a table risks losing context, erasing uncertainty, and conflating observations with generalizations.

EukTrait addresses this by keeping **assertions as the canonical record**, while providing principles for **deriving synthesized views**.

---

## Conceptual steps to synthesis

While implementation may vary, synthesis generally involves three stages:

### 1. Selecting the scope

Decide which assertions to consider:

- **Taxon-level** or **material-level**?
- Specific life stages, environments, or experimental methods?
- Direct observations only, or including inferences?

Using qualifiers to filter assertions ensures that the synthesis reflects exactly the intended context.

### 2. Grouping and aggregation

Assertions are grouped by:

- taxon or material,
- feature and trait,
- optionally, other contextual qualifiers (life stage, evidence type).

Aggregation may include:

- counting how many sources report a trait,
- identifying the range of values observed,
- summarizing conflicting assertions with context intact.

Example (conceptual):

    Trait: feeding_mechanism
    Taxon: Rictus lutensis

    Observed:
      - phagotrophy (material RCC299, light microscopy)
      - phagotrophy (material RCC300, electron microscopy)
    Inferred:
      - chemotrophy (species-wide, inferred from morphology)

This keeps both the observations and inferences visible.

### 3. Interpreting patterns

Once aggregated, synthesized views can answer questions like:

- What feeding strategies are reported for this species, and under what conditions?
- Which traits are variable between materials or life stages?
- Where do sources agree or conflict?

Importantly, **no assertion is discarded**. Users can always drill down to the original claim.

---

## Best practices for synthesis

1. **Preserve provenance.**  
   Always retain links to the sources supporting each assertion.

2. **Respect context.**  
   Life stage, environment, and evidence method are not optional; they shape interpretation.

3. **Distinguish observation from inference.**  
   Aggregated views should mark which claims were measured directly versus inferred.

4. **Do not overgeneralize.**  
   Avoid assuming that a trait observed in one material applies to the entire taxon unless explicitly supported.

5. **Document decisions.**  
   Any filtering, aggregation rules, or weighting applied during synthesis should be transparent and reproducible.

---

## Conceptual example: trophic traits

    Taxon: Rictus lutensis

    Feature: organism
    Trait: feeding_mechanism

    Aggregated summary:
      - phagotrophy: observed in RCC299, RCC300 (active stage, microscopy)
      - chemotrophy: inferred from morphology (species-wide)

Here, both observed and inferred assertions coexist. Users can see which traits are directly supported, and which are inferred.

---

## Why this matters

Synthesis is how EukTrait becomes **useful for comparative biology**:

- It allows identifying patterns across taxa or materials.
- It preserves complexity rather than flattening it.
- It keeps evidence explicit, allowing reinterpretation as new data appear.

Even without fully automated tools, thinking in terms of assertions and synthesis ensures that all trait knowledge is **traceable, transparent, and contextually meaningful**.

---

## Looking forward

Future implementations may include:

- automated aggregation pipelines,
- trait dashboards for taxa or clades,
- visualizations of variability and conflict,
- and programmatic interfaces for comparative analysis.

Until then, the principles described here serve as a guide for **manual synthesis and careful curation**, ensuring that EukTrait remains both flexible and robust.
