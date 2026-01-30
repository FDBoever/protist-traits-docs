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

| Dataset / Reference | Taxonomic Scope | Trait Domains | Data Format | Repository / DOI |
|--------------------|----------------|---------------|------------|----------------|
| Dumack et al. (2019) — Cercozoa and Endomyxa | Cercozoa and Endomyxa | nutrition, morphology, locomotion, habitat, size | tab-delimited text | [GitHub](https://github.com/Kenneth-Dumack/Functional-Traits-Cercozoa-Endomyxa), DOI: [10.1111/1755-0998.13112](https://doi.org/10.1111/1755-0998.13112) |
| Freundenthal et al. (2025) — Amoebozoa Trait Database | Amoebozoa | nutrition, morphology, morphotype, locomotion, size, habitat, life history | tab-delimited text | [GitHub](https://github.com/JFreude/FunctionalTraitsAmoebozoa), [Zenodo](https://doi.org/10.5281/zenodo.15091355), DOI: [10.1111/1755-0998.70064](https://doi.org/10.1111/1755-0998.70064) |
| Ramond et al. (2018, 2019) — Marine Protist Functional Traits | Marine protists | morphology, trophic strategy, habitat, life history | semicolon-separated CSV | SEANOE dataset 56963, DOI: [10.1111/1462-2920.14537](https://doi.org/10.1111/1462-2920.14537) |
| Schneider et al. (2020) — Trophic Modes of Aquatic Protists | Protists | trophic mode, mixotrophy | main + citation tables | DOI: [10.3897/BDJ.8.e56648](https://doi.org/10.3897/BDJ.8.e56648) |
| Giachello et al. (2023) — Functional Traits of Soil Protists | Soil protists | trophic mode, feeding strategy, morphology, locomotion, size, habitat, life history | Excel workbook | DOI: [10.1016/j.soilbio.2023.109207](https://doi.org/10.1016/j.soilbio.2023.109207) |
| Mitra et al. (2023) — The Mixoplankton Database (MDB) | Photo-phago-trophic plankton | host-related traits only | Excel workbook | Zenodo 7839780, DOI: [10.1111/jeu.12972](https://doi.org/10.1111/jeu.12972) |
| Bjørbækmo et al. (2019) — Protist Interaction Database (PIDA) | Protists | host traits | CSV | Zenodo [1195514](https://zenodo.org/records/1195514), DOI: [10.1038/s41396-019-0542-5](https://doi.org/10.1038/s41396-019-0542-5) |
| Põlme et al. (2020) — FungalTraits Database | Fungi, fungus-like Stramenopiles | ecological and functional traits | Google Sheets | DOI: [10.1007/s13225-020-00466-2](https://doi.org/10.1007/s13225-020-00466-2) |
| Lentendu et al. (2025) — EukFunc | Fungi, nematodes, protists (soil) | functional classes | Zenodo / GitHub | [Zenodo](https://zenodo.org/records/15243078), [GitHub](https://github.com/lentendu/EukFunc), DOI: [10.1111/1755-0998.14118](https://doi.org/10.1111/1755-0998.14118) |
| Rimet et al. (2018) — Phytoplankton Trait Database | Freshwater phytoplankton | morphology, size, life form, colony formation, motility, ecological strategy | CSV | [Zenodo](https://zenodo.org/records/1164834), DOI: [10.1051/limn/20180090](https://doi.org/10.1051/limn/20180090) |
| Laplace-Treyture et al. (2021) — French Phytoplankton Traits | Freshwater phytoplankton | morphology, size, motility, colony formation, ecological strategy | CSV | DOI: [10.1038/s41597-021-00814-0](https://doi.org/10.1038/s41597-021-00814-0), [Figshare](https://doi.org/10.6084/m9.figshare.13416659) |


### Dumack et al. (2019) — Cercozoa and Endomyxa

* Reference: Dumack et al. 2019, *Molecular Ecology Resources* (DOI: [10.1111/1755-0998.13112](https://doi.org/ 10.1111/1755-0998.13112))
* Repository: GitHub [Kenneth-Dumack/Functional-Traits-Cercozoa-Endomyxa](https://github.com/Kenneth-Dumack/Functional-Traits-Cercozoa-Endomyxa)
* Taxonomic scope: Cercozoa and Endomyxa
* Trait domains: nutrition, morphology, locomotion, habitat, size
* Data format: tab-delimited text

This dataset was ingested using `read.delim()` and served as a core reference for morpho-trophic traits in Rhizaria-related lineages.

---

### Freundenthal et al. (2025) — Amoebozoa Trait Database

* Reference: Freundenthal et al. (2025), Molecular Ecology Resources  (DOI: [10.1111/1755-0998.70064](https://doi.org/10.1111/1755-0998.70064))
* Source: Dumack laboratory
* Repository: GitHub (FunctionalTraitsAmoebozoa) Github ([https://github.com/JFreude/FunctionalTraitsAmoebozoa](https://github.com/JFreude/FunctionalTraitsAmoebozoa)) and Zenodo (DOI: [https://doi.org/10.5281/zenodo.15091355](https://doi.org/10.5281/zenodo.15091355))
* Taxonomic scope: Amoebozoa
* Trait domains: nutrition, morphology, morphotype, locomotion, size, habitat, life history
* Data format: tab-delimited text

This dataset complements Dumack et al. (2019) by extending trait coverage to Amoebozoa using a structurally comparable framework.

---

### Ramond et al. (2018, 2019) — Marine Protist Functional Traits

* Reference: Ramond et al. 2019, *Environmental Microbiology* (DOI: [10.1111/1462-2920.14537](https://doi.org/10.1111/1462-2920.14537))
* Data repository: SEANOE (dataset 56963)
* Trait domains: morphology, trophic strategy, habitat, life history
* Data format: semicolon-separated CSV

Traits in this dataset were manually curated from the literature, resulting in high interpretative value but heterogeneous terminology.

---

### Schneider et al. (2020) — Trophic Modes of Aquatic Protists

* Reference: Schneider et al. 2020, *Biodiversity Data Journal* (DOI: [10.3897/BDJ.8.e56648](https://doi.org/10.3897/BDJ.8.e56648))
* Focus: trophic mode classification, including mixotrophy
* Structure: main trait table plus a separate citation table

Both tables were ingested to enable explicit linkage between trait assertions and their bibliographic sources.

---

### Giachello et al. (2023) — Functional Traits of Soil Protists

* Reference: Giachello et al. 2023, *Soil Biology & Biochemistry* (DOI: [10.1016/j.soilbio.2023.109207](https://doi.org/10.1016/j.soilbio.2023.109207))
* Trait domains: trophic mode, feeding strategy, morphology, locomotion, size, habitat, life history
* Data format: Excel workbook with multiple sheets

Two sheets were used:

* the complete trait dataset,
* the reference table documenting literature sources for trait assignments.

---

### Mitra et al. (2023) — The Mixoplankton Database (MDB)

* Reference: Mitra et al. 2023, *Journal of Eukaryotic Microbiology* (DOI: [10.1111/jeu.12972](https://doi.org/10.1111/jeu.12972))
* Database: Zenodo record 7839780
* Scope: photo-phago-trophic plankton across the global ocean
* Data format: Excel workbook

For Step 1, only **host-related trait columns** were retained. Occurrence data and prey-related columns were explicitly excluded to avoid conflating organismal traits with interaction networks.

---

### Bjørbækmo et al. (2019) — Protist Interaction DAtabase (PIDA)

* Reference: Bjørbækmo et al. (2019) ISMEj (DOI: [10.1038/s41396-019-0542-5](https://doi.org/10.1038/s41396-019-0542-5))
* Repository: Zenodo [https://zenodo.org/records/1195514](https://zenodo.org/records/1195514)
* Focus: protist–protist and protist–bacteria interactions

Authors examined the available scientific literature spanning the last ~150 years, and recorded ~2500 ecological interactions from ~500 publications going back to the late 1800s.

Only host-side trait and taxonomic information was retained. Prey taxonomy columns were removed to maintain consistency with a host-centric trait framework.

---

### Põlme et al. (2020) — FungalTraits Database

* Reference: Põlme et al. 2020, Fungal diveristy (DOI: [10.1007/s13225-020-00466-2](https://doi.org/10.1007/s13225-020-00466-2))
* Database: FungalTraits (Google Sheets)
* Taxonomic scope: Fungi and fungus-like Stramenopiles

This dataset provides a comprehensive, genus-level compilation of ecological and functional traits for fungi, including lifestyle classifications (e.g. saprotrophic, symbiotic, pathogenic), morpho-anatomical features, substrate associations, and ectomycorrhizal characteristics.

---

### Lentendu et al. (2025) — EukFunc: A Holistic Eukaryotic Functional Reference for Automated Profiling of Soil Eukaryotes

* Reference: Lentendu et al. 2025 (DOI: [10.1111/1755-0998.14118](https://doi.org/10.1111/1755-0998.14118))
* Database: EukFunc (Zenodo: [https://zenodo.org/records/15243078](https://zenodo.org/records/15243078), GitHub: [https://github.com/lentendu/EukFunc](https://github.com/lentendu/EukFunc))
* Taxonomic scope: Fungi, nematodes and protists from soil

This dataset provides comprehensive functional classes and aims to combine functional information across the entire soil eukaryome as compared to focusing on fungi, protists or nematodes individually.

despite enourmous taxonomic coverage, there are very little references that couple the assertions directly to publication sources, making it a little bit troublesome for our framework. exploration of what could be mined is still ongoing.

---


### Rimet et al. (2018) — Trait Database for Phytoplankton of Temperate Lakes

* Reference: Rimet et al. 2018, Annales de Limnologie – International Journal of Limnology (DOI: [10.1051/limn/2018009](https://doi.org/10.1051/limn/20180090))
* Data repository: (Zenodo: [https://zenodo.org/records/1164834](https://zenodo.org/records/1164834))
* Taxonomic scope: Freshwater phytoplankton (primarily algae) from temperate lakes
* Taxonomic backbone: Expert-curated taxonomy, largely consistent with contemporary algal systematics
* Trait domains: morphology, size, life form, colony formation, motility, ecological strategy
* Data format: CSV (open access)

This database represents a long-term, expert-maintained compilation of phytoplankton functional traits, originally developed for ecological assessment and bioindication in temperate lake ecosystems. Trait definitions are largely categorical and morpho-functional, reflecting classical phytoplankton functional ecology.

---

### Laplace-Treyture et al. (2021) — Phytoplankton Morpho-Functional Trait Dataset from French Water Bodies

Reference: Laplace-Treyture et al. 2021, Scientific Data (DOI: [10.1038/s41597-021-00814-0](https://doi.org/10.1038/s41597-021-00814-0))

* Data file: FRENCH_PHYTOPLANKTON_TRAITS.csv (DOI: [10.15454/GJGIAH](https://doi.org/10.6084/m9.figshare.13416659))
* Taxonomic scope: Freshwater phytoplankton from French rivers, lakes, and reservoirs
* Taxonomic backbone: AlgaeBase
* Trait domains: morphology, size, motility, colony formation, ecological strategy
* Data format: CSV

This dataset provides a harmonized morpho-functional trait table for phytoplankton taxa occurring in French water bodies, with taxonomy explicitly aligned to AlgaeBase. Traits are predominantly categorical and focus on structural and ecological characteristics commonly used in biomonitoring and functional classification schemes.

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