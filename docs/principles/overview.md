# Overview

## What is EukTrait?

EukTrait is a framework for representing biological traits of eukaryotic microorganisms, with a particular focus on protists. It is designed to capture not only *what* is known about organisms, but also *how* that knowledge was obtained, *where* it applies, and *under which assumptions* it was made.

Rather than treating traits as fixed facts (for example, “species X is heterotrophic”), EukTrait represents biological knowledge as a collection of explicit, structured **assertions**. Each assertion links a claim to a source (literature, book, etc), a taxonomic (species, genus, etc) or material context (strain, speciimen, ...), and any relevant qualifiers such as life stage or evidence type.

The aim is to support a long-lived, community-curated trait resource that can evolve alongside biological understanding, rather than becoming outdated or internally inconsistent as knowledge changes.

---

## Why another trait framework?

Protists routinely break the assumptions built into many existing biological databases. Traits often differ between life stages, environments, or strains. Morphology, physiology, and ecology do not always align neatly. Taxonomy is frequently revised. Many observations are indirect, inferred, or context-dependent.

Flattening this complexity into tables, or encoding it directly into ontology class hierarchies almost inevitably leads to infromation loss or over-generalisation. A strictly tabular mindset - one row per organism and one column per trait - may produce enormous matrices where most entries are empty (NA), while forcing us to compare "apples to pears" (ie chanoflagellates to ciliares). More importantly, a single row per organism risks to onbscure uncerainty, context dependency, and even contradictory claims, rather than preserving them as features of the data.

EukTrait starts from the position that this complexity is not an inconvenience to be simplified or swept under the carpet, but that this complexity is an inherent feature of how knowledge accumulates in microbial eukaryotic biology. We agrue that an underlying data structure should capture and preserve this complexity, rather than forcing it into a single "best" answer.

---

## Assertions, not facts

A central principle of EukTrait is that biological knowledge consists of **claims** (=`assertions`), not universal truths.

Every piece of information in the system is an `assertion` that says, in effect: *this source reports that this trait applies to this taxon or material, under these conditions*. Different assertions may agree, overlap, or disagree, and all of that information is better preserved than lost.

By treating assertions as first-class objects, EukTrait makes it possible to track where ideas come from, compare alternative interpretations, and update conclusions as new data or methods become available. Hence, no assertion is assumed to be final, and no statement is considered globally valid.

---

## Ontologies as constraints on meaning

EukTrait makes use of ontologies, but not in the traditional sense of encoding biological facts as rigid class hierarchies. In this framework - ntologies guide how traits and assertions are structured, ie providing their **meaning and structure**, without pretending that biolofy will neatly obey the rules.

They specify what kinds of `features` can be described - ie what kinds of things we can talk about (such as organisms, cells, or cellular structures); what `traits` can be asserted (such as presence, length, or trophic mode), what kinds of values those traits may take (`vocabularies`), and how assertions can be qualified (capturing the context or method by which they were observed).

In this way, ontologies act as semantic guardrails. They help prevent invalid or ambiguous statements while remaining stable even as the underlying biological data grows and changes, or refuses to behave.

---

## Keeping different kinds of information separate

A deliberate design choice in EukTrait is to separate different layers of information that are often tangled together elsewhere - usually to everyone's regret.

`Taxa` handle names and classification, including alternative taxonomic opinions. `Materials` represent physical biological entities such as strains, cultures, or isolates. `Sources` capture literature references or datasets. Ontologies define shared meaning. `Assertions` connect all of these into concrete biological claims.

Keeping these layers separate allows each one to evolve indedpendently. For example, taxonomy can be revised without rewriting trait data. New traits can be introduced without disturbing existing records. Sources can be revised and reinterpreted without erasing what was thought before. In short, the system can evolve the way biology does; incrementally, messily, and without erasing historical claims.

---

## Domains as ways of asking questions

EukTrait is organised into domain `ontologies` such as morphology, nutrition, ecology, physiology, and life history. These domains reflect different ways biologists ask questions — what an organism looks like, how it functions, where it lives — rather than rigid partitioning of reality.

These domains are intentionally modular. For example, features and traits may appear in more than one domain, and domains can evolve or expand over time. Their role is to provide structure, but not to impose boundaries on systems that rarely respect them.

---

## Context matters

Traits in biology are rarely absolute. Many apply only to certain life stages, under particular environmental conditions, or in specific experimental settings. In EukTrait, this context is recorded alongside each assertion through `qualifiers`, rather than left or burried in methods sections.

These `qualifiers` allow description of biological scope (such as life stage or cellular location) or how to observations were made, for example the type of evidence or method used. Making context visible assertions to be compared, filtered, and interpreted with the caution they deserve, instead of teing treated as universally true for a given taxon or strain.

---

## Designed for change

EukTrait is built on the assumption that biological knowledge will change.  Contributors will disagree. New data types will appear. Classifications will be revised - sometimes repeatedly.

With that in mind, the framewok favors clarity over clever shortcuts, and explicit statements over convenient simplifications. The goal is to support careful curation, automated data extraction, and large-scale comparative analyses without losing track of where the information care from, how it was originally interpreted, or what it actually states.

---

## What EukTrait is not

EukTrait is not a flat trait table, a replacement for raw data repositories, or a definitive authority on taxonomy or organismal biology.

Think of it instead as a semantic layer, **a way of connecting biological claims to their meaning, context and evidence**, so that the messy, contradictory and ever-changing nature of biology can be explored rather than ignored.