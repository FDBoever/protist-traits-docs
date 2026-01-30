# Overview

## What is EukTrait?

EukTrait is a framework for representing biological traits of eukaryotic microorganisms, with a particular focus on protists. It is designed to capture not only *what* is known about organisms, but also *how* that knowledge was obtained, *where* it applies, and *under which assumptions* it was made.

Rather than treating traits as fixed facts (for example, “species X is heterotrophic”), EukTrait represents biological knowledge as a collection of explicit, structured **assertions**. Each assertion links a claim to a source, a taxonomic or material context, and any relevant qualifiers such as life stage or evidence type.

The aim is to support a long-lived, community-curated trait resource that can evolve alongside biological understanding, rather than becoming outdated or internally inconsistent as knowledge changes.

---

## Why another trait framework?

Protists routinely break the assumptions built into many existing biological databases. Traits often differ between life stages, environments, or strains. Morphology, physiology, and ecology do not always align neatly. Taxonomy is frequently revised. Many observations are indirect, inferred, or context-dependent.

Flattening this complexity into tables or encoding it directly into ontology class hierarchies usually results in loss of information. Provenance disappears, uncertainty is hidden, and contradictory claims are silently resolved rather than preserved.

EukTrait starts from the position that this complexity is not a nuisance to be simplified away, but an inherent feature of microbial eukaryotic biology that needs to be represented explicitly.

---

## Assertions, not facts

A central principle of EukTrait is that biological knowledge consists of **claims**, not universal truths.

Every piece of information in the system is an assertion that says, in effect: *this source reports that this trait applies to this taxon or material, under these conditions*. Assertions can agree, overlap, or conflict with one another, and all of that information is preserved.

By treating assertions as first-class objects, EukTrait makes it possible to track provenance, compare interpretations, and revisit conclusions as new data or methods become available. No assertion is assumed to be permanent or globally valid.

---

## Ontologies as constraints on meaning

EukTrait makes use of ontologies, but not in the traditional sense of encoding biological facts as class axioms. Ontologies in this framework define the **meaning and allowable structure** of assertions.

They specify what kinds of features can be described (such as organisms, cells, or cellular structures), what traits can be asserted (such as presence, length, or trophic mode), what kinds of values those traits may take (vocabularies), and how assertions can be qualified.

In this way, ontologies act as semantic guardrails. They help prevent invalid or ambiguous statements while remaining stable even as the underlying biological data grows and changes.

---

## Keeping different kinds of information separate

A deliberate design choice in EukTrait is to separate different layers of information that are often conflated elsewhere.

Taxa are used to represent names and classifications, including alternative taxonomic opinions. Materials represent physical biological entities such as strains, cultures, or isolates. Sources capture literature references or datasets. Ontologies define shared meaning. Assertions connect all of these into concrete biological claims.

This separation allows each layer to evolve independently. Taxonomy can be revised without rewriting trait data. New traits can be added without changing existing records. Sources can be reinterpreted without erasing history.

---

## Domains as ways of asking questions

EukTrait is organized into domain ontologies such as morphology, nutrition, ecology, physiology, and life history. These domains reflect different biological questions—what an organism looks like, how it functions, where it lives—rather than rigid partitions of reality.

Domains are intentionally modular. Features and traits may appear in more than one domain, and domains can evolve or expand over time. Their purpose is to provide structure and clarity, not to enforce artificial boundaries.

---

## Context matters

Traits are rarely absolute. Many apply only to particular life stages, environmental conditions, or experimental settings. In EukTrait, this contextual information is captured explicitly through qualifiers attached to assertions.

Qualifiers may describe biological scope (such as life stage or cellular location) or epistemic context (such as evidence type or method). Making context explicit allows assertions to be compared, filtered, and interpreted with appropriate care.

---

## A framework built for the long term

EukTrait is designed with the expectation that scientific knowledge will change. Contributors will disagree. New data types will appear. Classifications will be revised.

For this reason, the framework emphasizes clarity over cleverness and explicitness over convenience. It is intended to support careful curation, automated data extraction, and large-scale comparative analyses without sacrificing transparency or flexibility.

---

## What EukTrait is not

EukTrait is not a flat trait table, a replacement for raw data repositories, or a definitive authority on taxonomy or organismal biology.

It is best understood as a semantic layer that connects biological claims to their meaning, context, and evidence.
