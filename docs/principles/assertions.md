# What is an assertion?

An assertion is the fundamental unit of knowledge in EukTrait.

It represents a single, explicit biological claim: that a particular trait applies to a particular feature, for a particular taxon or material, according to a particular source, and under a particular context.

Assertions are not facts. They are *statements made by sources*.

---

## Why assertions?

In much of biology, data are presented as if they were universally true properties of organisms. In practice, most biological knowledge is conditional, incomplete, or inferred, and often revised as new evidence appears.

EukTrait uses assertions to preserve this reality. By treating each claim as a distinct object, the framework makes it possible to:

- track provenance,
- represent uncertainty,
- preserve conflicting interpretations,
- and revise conclusions without rewriting history.

---

## The anatomy of an assertion

Every assertion in EukTrait has four core components:

1. **A target**  
   What the assertion applies to: a taxon or a material.

2. **A feature**  
   The biological entity being described (for example, an organism, a cell, or a cellular structure).

3. **A trait and value**  
   What property is being asserted and what value it takes.

4. **A source**  
   The reference that supports the claim.

Assertions may also include **qualifiers** that provide additional biological or epistemic context.

---

## A simple example

Consider the statement:

> *Rictus lutensis feeds by phagotrophy.*

In EukTrait, this is represented as an assertion rather than a bare fact.

```yaml
taxon_id: rictus_lutensis
source_id: yubuki_etal_2009

assertions:
  - feature: organism
    trait: feeding_mechanism
    value: phagotrophy
    qualifiers:
      evidence_method: light_microscopy
```

This makes several things explicit:

- the claim applies to a specific taxon,
- it concerns the organism as a whole,
- it describes a feeding mechanism,
- and it is supported by a particular source and method.

---

## Assertions describe claims, not beliefs

An assertion records what a source reports. It does not imply that the claim is correct, complete, or universally applicable.

Different sources may assert different traits for the same taxon, or the same trait with different values. These assertions can coexist without being resolved or reconciled.

Preserving this multiplicity is a feature, not a flaw.

---

## Contextualizing assertions

Biological traits are often conditional. Assertions can be qualified to indicate the conditions under which a claim applies.

For example:

```yaml
- feature: organism
  trait: presence
  value: true
  qualifiers:
    life_stage: active
    evidence_method: microscopy
```

This indicates that the feature was observed in a particular life stage and using a particular method. If another source reports a different observation under different conditions, both assertions can be represented without conflict.

---

## Assertions can be inferred

Not all assertions are direct observations. Some are inferred from other data or general biological reasoning.

For example:

```yaml
- feature: organism
  trait: energy_source
  value: chemotrophy
  qualifiers:
    assertion_type: inferred
    evidence_basis: morphology
```

Making inference explicit allows users to distinguish between observed and derived claims, and to revisit or revise inferences as understanding improves.

---

## Assertions and materials

Whenever possible, assertions should apply to concrete biological materials such as strains or cultures.

For example:
```yaml
applies_to:
  material_id: RCC299

feature: organism
trait: feeding_mechanism
value: phagotrophy
```

Material-level assertions capture biological variability and experimental context more precisely than taxon-level assertions. Taxon-level assertions may be appropriate when supported by broader evidence, but they are not assumed by default.

---

## Assertions are independent and immutable

Each assertion stands on its own.

Once created, an assertion is not edited to reflect new interpretations. Instead, new assertions are added, or existing ones are superseded or deprecated. This preserves a transparent record of how knowledge has evolved over time.

---

## Thinking in assertions

Working with EukTrait requires a shift in perspective.

Instead of asking “What traits does this organism have?”, ask:

!!! note ""

    What claims have been made about this organism, by whom, and under what conditions?
