# Design decision: using public protist trait databases

## Background

A growing number of protist trait datasets already exist. These are typically published as supplementary tables, spreadsheets, or small repositories, each focused on a specific taxonomic group, environment, or ecological question.

Individually, these datasets are useful. Collectively, they represent a substantial body of trait knowledge that is difficult to reuse because of differences in terminology, structure, and scope.

Rather than starting with an empty framework, EukTrait explicitly integrates these public databases as an initial source of trait information.

---

## Why integrate existing databases?

The decision to integrate public trait databases is pragmatic.

- They contain expert-curated trait information that would be unrealistic to recreate manually.
- They reflect how traits are currently defined and used in the protist literature.
- They provide immediate taxonomic and ecological coverage across many lineages.
- They expose inconsistencies and ambiguities that would otherwise remain implicit.

In other words, these datasets capture *how the community currently talks about traits*, even if that usage is inconsistent or underspecified.

---

## What role do these datasets play?

Imported trait records are treated as **assertions**, not as definitive truth.

Each trait statement is stored together with:
- its original source,
- the original column and value,
- and the associated publication or repository.

This allows multiple, even conflicting, trait assertions to coexist. The goal is not to resolve disagreement at import time, but to preserve it transparently.

---

## Structural standardisation, not semantic harmonisation

At the point of integration, EukTrait focuses on **structural alignment only**.

Specifically, datasets are:
- converted into a common long-format structure,
- annotated with consistent metadata fields,
- and linked to explicit provenance.

Trait meanings, value vocabularies, and conceptual equivalences are *not* harmonised at this stage. This avoids imposing interpretations that are not justified by the source data.

Semantic alignment is handled later using ontologies and explicit mapping steps.

---

## Why flat files are acceptable

Most public trait datasets are distributed as flat tables. EukTrait does not attempt to redesign these formats at the source.

Instead, flat files are treated as a stable interchange format that can be:
- read reproducibly,
- translated into an internal representation,
- and traced back to their original form.

This keeps the integration process simple, auditable, and reversible.

---

## What this approach enables

Using public databases as inputs allows EukTrait to:

- rapidly populate the framework with real data,
- compare trait usage across datasets and domains,
- identify conflicting definitions and gaps,
- and provide a concrete basis for ontology development.

It also makes clear which parts of the trait landscape are well covered by existing data, and which remain largely undocumented.

---

## Limitations

This approach inevitably carries forward:
- biases present in source datasets,
- uneven taxonomic and ecological coverage,
- ambiguous or historically inconsistent terminology.

These limitations are accepted explicitly. They are documented rather than hidden, and they help motivate later harmonisation and curation steps.

---

## In context

Integration of public trait databases is an early step in the EukTrait workflow. It provides a starting point, not an endpoint.

Ontologies, literature-derived traits, and expert curation are required to move from a collection of assertions toward a more coherent trait synthesis.
