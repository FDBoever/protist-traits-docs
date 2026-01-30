# Step 1 — Compilation and Standardisation of Public Protist Trait Databases

## Overview and Rationale

Trait-based approaches are increasingly recognised as essential for understanding protist ecology, biogeography, and ecosystem functioning. However, compared to plants and animals, functional trait information for protists remains highly fragmented across studies, taxonomic groups, ecosystems, and data formats.

Although several public trait datasets exist, they differ strongly in:

* taxonomic scope and resolution,
* trait definitions and terminology,
* ecological focus (marine, freshwater, soil),
* file structure and accessibility.

The goal of **Step 1** is therefore to construct a transparent, reproducible foundation by structurally integrating existing public trait resources while preserving their original meaning and provenance.

Specifically, we aimed to:

1. Identify relevant peer-reviewed protist trait databases with public access.
2. Retrieve these datasets from their original repositories.
3. Read each dataset using appropriate, source-specific methods.
4. Convert all datasets into a unified *long-format trait representation*.
5. Preserve taxonomic resolution, trait context, and citations.
6. Defer semantic harmonisation to later workflow stages.

We specifically separate **structural standardisation** and **semantic harmonisation** to avoid premature interpretation of trait concepts.

---

## Conceptual Motivation and Literature Context

* **Jamy et al. (2025)** — *Towards a trait-based framework for protist ecology and evolution* (Trends in Microbiology, DOI: 10.1016/j.tim.2025.08.008)
* **Burki et al. (2021)** — *Diversity and ecology of protists revealed by metabarcoding* (Current Biology, DOI: 10.1016/j.cub.2021.07.066)

Both highlight that trait-based protist ecology is currently limited not by lack of data, but by inconsistent trait definitions, scattered data sources, and missing integrative frameworks.

Step 1 addresses this limitation by compiling existin datasets into a  machine-readable backbone for downstream ontology matching.

---

## Identification of Public Trait Databases

Trait databases were included based on the following criteria:

* availability via public repositories (supplementary materials, GitHub, Zenodo, SEANOE),
* explicit linkage between taxa and functional traits,
* relevance to trophic mode, morphology, size, habitat, or life history.

---

## Currently included Databases

### Overview table

| Dataset / Reference | Taxonomic Scope | Data Format / Repository |
|--------------------|----------------|-------------------------|
| Dumack et al. (2019) | Cercozoa & Endomyxa | tab-delimited text / [GitHub](https://github.com/Kenneth-Dumack/Functional-Traits-Cercozoa-Endomyxa) |
| Freundenthal et al. (2025) | Amoebozoa | tab-delimited text / [GitHub](https://github.com/JFreude/FunctionalTraitsAmoebozoa), [Zenodo](https://doi.org/10.5281/zenodo.15091355) |
| Ramond et al. (2018, 2019) | Marine protists | CSV / SEANOE 56963 |
| Schneider et al. (2020) | Protists | trait tables / DOI: [10.3897/BDJ.8.e56648](https://doi.org/10.3897/BDJ.8.e56648) |
| Giachello et al. (2023) | Soil protists | Excel / DOI: [10.1016/j.soilbio.2023.109207](https://doi.org/10.1016/j.soilbio.2023.109207) |
| Mitra et al. (2023) | Mixoplankton | Excel / Zenodo 7839780 |
| Bjørbækmo et al. (2019) | Protist interactions | CSV / [Zenodo](https://zenodo.org/records/1195514) |
| Põlme et al. (2020) | Fungi & fungus-like Stramenopiles | Google Sheets / DOI: [10.1007/s13225-020-00466-2](https://doi.org/10.1007/s13225-020-00466-2) |
| Lentendu et al. (2025) | Soil eukaryotes | Zenodo / GitHub / DOI: [10.1111/1755-0998.14118](https://doi.org/10.1111/1755-0998.14118) |
| Rimet et al. (2018) | Freshwater phytoplankton | CSV / [Zenodo](https://zenodo.org/records/1164834) |
| Laplace-Treyture et al. (2021) | French freshwater phytoplankton | CSV / [Figshare](https://doi.org/10.6084/m9.figshare.13416659) |

for more detailed information of public databases 
[:octicons-arrow-right-24: public-databases](./public-databases.md)


---

## Unified Long-Format Trait Schema

All datasets were converted into a shared long-format schema designed to:

* preserve original taxonomic resolution,
* separate trait meaning from source-specific column names,
* retain full citation metadata,
* support later ontology-based harmonisation.

### Core Fields

**Taxonomy**

* taxon_name
* taxon_rank
* genus, family, order, class, phylum, supergroup, domain

**Trait Information**

* trait_category
* trait_name
* trait_value
* trait_unit

**Context**

* habitat
* environment
* life_stage

**Provenance**

* source_db
* source_table
* reference_id
* reference_full

**Audit Metadata**

* original_column
* original_value
* notes

---

## Dataset-Specific Extraction Strategy

Each database was processed using a dedicated extraction function that:

1. Identified trait-relevant columns.
2. Pivoted the data into long format.
3. Assigned broad trait categories (e.g. trophic, morphology, size).
4. Preserved original values and column names.
5. Attached explicit provenance metadata.

No semantic harmonisation or value standardisation was applied at this stage.

---

## Output of Step 1

Step 1 produces a set of structurally aligned long-format trait tables, one per source database. Together, these form a comprehensive, provenance-aware corpus spanning marine, freshwater, soil, and host-associated protists.

This corpus serves as the sole input for subsequent workflow stages.

---

## Position in the Overall Workflow

* **Step 1 (this document):** Structural compilation and standardisation of public protist trait databases.
* **Step 2 (next):** Semantic harmonisation of trait categories, values, and vocabularies using a formal trait ontology.