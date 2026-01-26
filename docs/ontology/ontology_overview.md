# EukTrait Ontology Framework — Overview

## Purpose and scope

This document provides a **human-readable overview** of the EukTrait ontology framework. It is intended for:

- collaborators and domain experts
- data curators and annotators
- future users of the framework
- reviewers and readers of associated publications

The goal is to explain **how the ontology is structured**, **what biological domains it covers**, and **how data are represented**, without requiring prior familiarity with the underlying YAML schemas.

---

## Conceptual model (core idea)

At its core, EukTrait is a **trait assertion framework**. It does not store raw observations directly, but structured *assertions* about biological properties.

Every assertion:

- applies to a **taxon**
- is supported by a **source**
- describes a **trait** of a **feature**
- may be contextualized by **qualifiers**

### High-level structure

```
Taxon ──┐
        │
        ▼
+--------------------+
|  Assertion File    |
+--------------------+
| taxon_id           |
| source_id          |
| assertions[]       |
+--------------------+
        │
        ▼
+--------------------+
|    Assertion       |
+--------------------+
| feature            |
| trait              |
| value              |
| qualifiers (opt.)  |
+--------------------+
        │
        ├──────────────► Feature (ontology)
        │
        ├──────────────► Trait (ontology)
        │                     │
        │                     └── Vocabulary (optional)
        │
        └──────────────► Qualifiers (shared ontologies)

Source ───────────────────────────────────────┘
```

This model is **domain-agnostic**: morphology, ecology, physiology, genome, and other domains all conform to the same assertion structure.

---

## Ontology domains

EukTrait is organized into **modular domain ontologies**, each covering a major aspect of protist biology. Domains are independent but interoperable.

### Domain summary

| Domain        | Biological scope | Typical questions answered |
|--------------|-----------------|----------------------------|
| Morphology   | Cell structure and form | What does the cell look like? |
| Physiology   | Functional and biochemical traits | How does the cell function? |
| Nutrition    | Resource acquisition and trophic strategy | How does it obtain energy and matter? |
| Behavior     | Motility, aggregation, lifestyle | How does it move or interact? |
| Ecology      | Environmental context and interactions | Where does it live and interact? |
| Life history | Reproduction, dormancy, life cycle | How does it persist over time? |
| Genome       | Genome-level properties | What are the properties of its genomes? |
| Sequence     | Molecular sequence records | What sequences are associated with it? |

Each domain contains:

- **features**: biological entities or aspects
- **traits**: properties that can be asserted
- **vocabularies** (optional): controlled value sets

---

## Features, traits, and vocabularies

### Features

Features represent **biological targets** of assertions. Examples include:

- `flagellum`, `nucleus` (morphology)
- `habitat`, `substrate` (ecology)
- `nucleus`, `mitochondrion` (genome)

Features are **domain-specific**, but not exclusive: the same feature may appear in multiple biological contexts.

### Traits

Traits represent **properties** that can be asserted about features. Each trait defines:

- a value type (boolean, integer, measurement, categorical, string)
- optional links to controlled vocabularies
- a biological meaning independent of any specific feature

Traits are intentionally **feature-agnostic**, allowing reuse across domains and future extension.

### Vocabularies

Vocabularies are controlled lists of allowed values for categorical traits. They are:

- stored separately from traits
- reusable across domains
- extensible without schema changes

This design balances **semantic rigor** with **long-term flexibility**.

---

## Qualifiers

Qualifiers provide **context** for assertions. They are shared across domains and include:

- life stage
- evidence type
- environmental condition
- spatial position
- polarity

Qualifiers never define traits themselves; they *modify the interpretation* of an assertion.

---

## Example assertion (illustrative)

```yaml
taxon_id: TAXON:12345
source_id: SOURCE:doi_10.1234/example
assertions:
  - feature: flagellum
    trait: presence
    value: true
    qualifiers:
      life_stage: [active]
      evidence: [microscopy]
```

This states that the taxon possesses a flagellum, observed in the active life stage, based on microscopy.

---

## Design principles

EukTrait follows several guiding principles:

1. **Assertion-based** — all data are explicit, contextualized claims
2. **Modular** — domains evolve independently
3. **Feature–trait separation** — avoids combinatorial explosion
4. **Vocabulary externalization** — promotes reuse and stability
5. **Future-proofing** — accommodates legacy and emerging data types

---

## Intended use

The framework supports:

- manual expert curation
- automated extraction pipelines
- integration with external databases
- long-term comparative synthesis

It is not a replacement for raw data repositories, but a **semantic layer** on top of them.

---

