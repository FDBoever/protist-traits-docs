# Taxa, materials, and sources

Traits do not exist in isolation. Every biological claim is anchored to *something* it applies to, *something* it is based on, and *something* that makes it citable and traceable.

In EukTrait, these anchors are handled by three foundational ontology layers:

- **Taxa**
- **Materials**
- **Sources**

Together, they define *what* is being described, *what biological entity was examined*, and *where the claim comes from*.

---

## Why these are ontologies

Taxa, materials, and sources are sometimes treated as metadata in biological databases. In practice, they behave like ontologies: they define entities, relationships, constraints, and semantics that shape all downstream data.

In EukTrait, these layers are first-class citizens. They are versioned, structured, and explicitly described, just like trait ontologies.

---

## Taxa: biological concepts, not specimens

A taxon represents a **biological concept**: a named lineage as defined by taxonomic practice.

Taxa in EukTrait are:

- name-bearing entities,
- defined by rank and authority,
- historically contingent,
- and subject to revision.

They are *not* physical things.

### What taxon assertions do

Taxon-level assertions typically describe:

- nomenclatural relationships (parent taxa, rank),
- name etymology,
- type designations,
- or broadly applicable traits supported by multiple lines of evidence.

```yaml
- trait: parent_taxon
    value: Bicosoecida
    qualifiers:
      rank: order
      authority: Karpov, 1998
```

This is not a biological observation. It is a taxonomic claim tied to a source and a historical context.

---

## Materials: biological instances

Materials represent **concrete biological entities** that can be observed, manipulated, preserved, or sequenced.

Examples include:

- cultures,
- strains,
- isolates,
- environmental samples,
- or voucher specimens.

A material always refers to a taxon, but it is not equivalent to it.

```yaml
material_id: RCC299
taxon_id: rictus_lutensis
material_type: culture
```

---

## Why materials matter

Many biological traits are observed on *individual instances*, not on taxa as abstract concepts.

Materials allow EukTrait to:

- capture intraspecific variation,
- distinguish observations made on different strains,
- associate traits with experimental context,
- and avoid overgeneralization.

When a claim is based on a specific culture or isolate, it should be asserted at the material level whenever possible.

---

## Material descriptors

Materials are described using a dedicated descriptor ontology that covers:

- identity (material type),
- provenance (collection, accession),
- curation (preservation method),
- nomenclatural role (type status),
- and isolation context.

These descriptors are not traits of organisms; they are properties of the *material as an object of study*.

---

## Sources: the provenance of knowledge

A source represents the **origin of an assertion**.

Sources may include:

- primary literature,
- taxonomic monographs,
- database records,
- personal communications,
- or automated pipelines.

Every assertion in EukTrait must be linked to exactly one source.

---

## What sources capture

Source entities store structured bibliographic and contextual information, such as:

- authorship,
- year and venue,
- DOI or identifier,
- source type (e.g. primary description, review),
- language,
- and curation notes.

```yaml
source_id: yubuki_etal_2009
year: 2009
journal: Journal of Eukaryotic Microbiology
```

This ensures that every claim remains traceable, inspectable, and citable.

---

## Assertions connect everything

Assertions are the glue that binds taxa, materials, traits, and sources into a coherent semantic structure.

An assertion always:

- applies to a taxon *and/or* a material,
- refers to a feature and a trait,
- and is supported by a source.

Nothing “floats free”

---

## Why this separation matters

Separating taxa, materials, and sources allows EukTrait to reflect how biology actually works:

- taxa are hypotheses about evolutionary relationships,
- materials are biological realities,
- sources are acts of communication.

Conflating these leads to ambiguity and loss of meaning. Keeping them distinct preserves clarity, provenance, and flexibility.

---

## A practical guideline

When curating data, ask three questions:

1. *What biological entity was examined?*  
   → material

2. *To which biological concept does this observation relate?*  
   → taxon

3. *Where does this claim come from?*  
   → source

If all three cannot be answered explicitly, the assertion is incomplete.

---

## A shared foundation

Traits may differ across domains, and features may evolve over time, but taxa, materials, and sources provide a stable foundation on which all trait knowledge is built.