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

Two recent syntheses provide the conceptual backdrop for this workflow:

* **Burki et al. (2021)** — *Diversity and ecology of protists revealed by metabarcoding* (Current Biology, DOI: 10.1016/j.cub.2021.07.066)
* **Jamy et al. (2025)** — *Towards a trait-based framework for protist ecology and evolution* (Trends in Microbiology, DOI: 10.1016/j.tim.2025.08.008)

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

### Dumack et al. (2019) — Cercozoa and Endomyxa

* Reference: Dumack et al. 2019, *Molecular Ecology* (DOI: 10.1111/1755-0998.13112)
* Taxonomic scope: Cercozoa and Endomyxa
* Trait domains: nutrition, morphology, locomotion, habitat, size
* Data format: tab-delimited text

This dataset was ingested using `read.delim()` and served as a core reference for morpho-trophic traits in Rhizaria-related lineages.

---

### Freundenthal et al. (2026) — Amoebozoa Trait Database

* Source: Dumack laboratory
* Repository: GitHub (FunctionalTraitsAmoebozoa)
* Taxonomic scope: Amoebozoa
* Trait domains: nutrition, morphology, morphotype, locomotion, size, habitat, life history
* Data format: tab-delimited text

This dataset complements Dumack et al. (2019) by extending trait coverage to Amoebozoa using a structurally comparable framework.

---

### Ramond et al. (2018, 2019) — Marine Protist Functional Traits

* Reference: Ramond et al. 2019, *Environmental Microbiology* (DOI: 10.1111/1462-2920.14537)
* Data repository: SEANOE (dataset 56963)
* Trait domains: morphology, trophic strategy, habitat, life history
* Data format: semicolon-separated CSV

Traits in this dataset were manually curated from the literature, resulting in high interpretative value but heterogeneous terminology.

---

### Schneider et al. (2020) — Trophic Modes of Aquatic Protists

* Reference: Schneider et al. 2020, *Biodiversity Data Journal* (DOI: 10.3897/BDJ.8.e56648)
* Focus: trophic mode classification, including mixotrophy
* Structure: main trait table plus a separate citation table

Both tables were ingested to enable explicit linkage between trait assertions and their bibliographic sources.

---

### Giachello et al. (2023) — Functional Traits of Soil Protists

* Reference: Giachello et al. 2023, *Soil Biology & Biochemistry* (DOI: 10.1016/j.soilbio.2023.109207)
* Trait domains: trophic mode, feeding strategy, morphology, locomotion, size, habitat, life history
* Data format: Excel workbook with multiple sheets

Two sheets were used:

* the complete trait dataset,
* the reference table documenting literature sources for trait assignments.

---

### Mitra et al. (2023) — The Mixoplankton Database (MDB)

* Reference: Mitra et al. 2023, *Journal of Eukaryotic Microbiology* (DOI: 10.1111/jeu.12972)
* Database: Zenodo record 7839780
* Scope: photo-phago-trophic plankton across the global ocean
* Data format: Excel workbook

For Step 1, only **host-related trait columns** were retained. Occurrence data and prey-related columns were explicitly excluded to avoid conflating organismal traits with interaction networks.

---

### Bjørbækmo et al. (2019) — Protist Interaction Database (PIDA)

* Database: MicroEcoSystems Interaction Database v1.0.8
* Repository: Zenodo record 1195514
* Focus: protist–protist and protist–bacteria interactions

Only host-side trait and taxonomic information was retained. Prey taxonomy columns were removed to maintain consistency with a host-centric trait framework.

---

### Põlme et al. (2020) — FungalTraits Database

* Reference: Põlme et al. 2020, Fungal diveristy (DOI: 10.1007/s13225-020-00466-2)
* Database: FungalTraits (Google Sheets)
* Taxonomic scope: Fungi and fungus-like Stramenopiles

This dataset provides a comprehensive, genus-level compilation of ecological and functional traits for fungi, including lifestyle classifications (e.g. saprotrophic, symbiotic, pathogenic), morpho-anatomical features, substrate associations, and ectomycorrhizal characteristics.

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