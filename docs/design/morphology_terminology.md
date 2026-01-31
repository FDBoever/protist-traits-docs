# Design decision: adopting legacy morphological terminology

## Background

Much of the terminology used to describe protist cell surface structures predates modern ultrastructural methods. Many commonly used terms were introduced before the advent of electron microscopy and were based on light-microscopic appearance, gross morphology, or inferred function.

As a result, the same term has often been applied across very different protist lineages to describe structures that are **not homologous**, and sometimes not even structurally comparable.

This problem is well documented in the protistological literature and is explicitly addressed by Preisig (1994), who notes that cell surface terminology remains inconsistent, historically layered, and in many cases biologically ambiguous.

Rather than attempting to resolve these inconsistencies prematurely, EukTrait makes a deliberate choice to **represent terminology as it is used**, while keeping biological interpretation explicit and contextual.

---

## Source and scope

For extracellular and cell surface structures in the morphology domain, EukTrait draws extensively on:

> Preisig, H. R. (1994). *Terminology and nomenclature of protist cell surface structures.*

This work provides:

- explicit definitions of terms as used in the literature  
- historical context for their usage  
- acknowledgment of ambiguity and non-homology  
- a pragmatic overview of how terms are applied across protist groups  

The goal is not to treat Preisig (1994) as biologically authoritative in all cases, but to use it as a **terminological anchor** when formalising morphological features.

---

## Observed problem: terminological overload and ambiguity

As Preisig (1994) summarizes, many terms associated with the cell surface of protists originate from a period before ultrastructural information was available. Subsequent electron-microscopic studies have shown that identical terms are often used in different protist groups for structures that are fundamentally different.

A well-known example is the term *theca* in thecate amoebae, which has also been referred to as *test*, *shell*, *lorica*, *pellicle*, or *tectum*. Electron microscopy later revealed that some of these structures correspond to scaly periplasts similar to those found in many flagellates.

Other terms used in widely different contexts include *alveoli*, *extracellular matrix*, *pellicle*, *periplast*, and *theca*.

This ambiguity is not a problem introduced by EukTrait — it is an inherited feature of the field.

---

## Design choice: model terms as features, not interpretations

EukTrait adopts the following strategy for such terminology:

- Terms defined in the literature are represented as **features**
- Features correspond to named biological structures or entities
- No assumption of homology, developmental origin, or equivalence is encoded
- Definitions preserve historical usage, including known ambiguity

By modeling these terms as features rather than as traits or vocabulary values, EukTrait allows:

- traits to be asserted *about* these structures  
- qualifiers to capture taxonomic, methodological, or life-stage context  
- future reinterpretation without invalidating existing assertions  

For example, a term such as *basket* is modeled as a single feature, even though it has multiple distinct meanings across protist groups. These multiple usages are documented in the feature description rather than being artificially split or unified.

---

## What EukTrait does not attempt to do

This design decision deliberately avoids:

- enforcing homology where none is established  
- collapsing distinct structures under abstract umbrella categories  
- redefining or correcting historical terminology  
- encoding functional or taxonomic assumptions into feature identity  

Interpretation is instead handled through:

- traits  
- qualifiers  
- taxon constraints  
- sources  
- downstream synthesis  

---

## Rationale

This approach prioritizes:

- transparency over tidiness  
- traceability over abstraction  
- stability over premature optimisation  

Protist morphology is a domain where terminology has evolved unevenly and remains under active reinterpretation. EukTrait is designed to accommodate this reality rather than obscure it.

As understanding improves, features may be related, grouped, or reinterpreted — but existing assertions should remain intelligible and valid.

---

## Implications for curators and contributors

When working with morphological features:

- expect some terms to be broad or context-dependent  
- use qualifiers to clarify interpretation where needed  
- rely on sources to anchor meaning  
- do not assume equivalence across taxa unless explicitly stated  

Ambiguity is not a failure of curation — it is often an accurate reflection of biological knowledge.

---

## Outlook

Future extensions may include:

- grouping related features under higher-level conceptual categories  
- annotating features with taxonomic or structural scope  
- mapping features to external ontologies where appropriate  

Such work will build on the existing framework without rewriting its foundations.
