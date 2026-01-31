# SQL storage infrastructure

Given the inherent complexity of protist biology (for example, traits can vary across life stages, environments, or strains) the choice to use SQL might seem counterintuitive: why impose a tabular structure on data that resist tidy rows and columns? In EukTrait, SQL is used to provide a **stable backbone** for taxa, sources, and material references, while relational links and JSON fields let traits, measurements, qualifiers, and contextual information coexist.  

In short, SQL supports storage, indexing, and querying, but the **design preserves the richness, variability, and “messiness” of protist biology**.

---

## Core Tables

- **taxa** – stores taxonomic information, including scientific name, rank, authorship (`authority`), parent taxa (JSON array), etymology, type material, and type locality. Links to the source table via `authority_source_id`.

- **sources** – stores references and citations, structured bibliographic info, identifiers (DOI, ISBN, internal IDs), type, language, access, and curatorial metadata.

- **materials** – captures specimens or cultures, including type status, preservation, culture collection, and origin.

- **assertions** – the heart of our database. Each observation links a taxon, a source, and optionally a material. Traits and context are stored as JSON to retain richness, e.g., numeric ranges, life stage, evidence type, or other qualifiers. The `domain` field links each assertion to an ontology domain (morphology, nutrition, ecology, etc.).

> Each table has indexes on key fields to support fast queries, e.g., searching by `taxon_id`, `source_id`, or DOI.

---

## Design Principles

1. **Tables first, but not purely tabular**  
   - Taxonomy, sources, and specimens are naturally tabular.  
   - Traits and qualifiers are stored in JSON fields to accommodate flexible, context-dependent observations.

2. **Every observation is linked**  
   - `assertions` connect taxa, sources, and materials.  
   - `domain` allows filtering by ontology (morphology, nutrition, ecology, etc.).  
   - JSON ensures flexibility for unusual or new traits without changing the schema.

3. **Versioning and maintenance**  
   - Timestamps `created_at` and `updated_at` track changes.  
   - Foreign keys maintain relational integrity, but JSON allows evolving content.  
   - Database can be rebuilt or migrated via `build_db.py`, preserving internal IDs.

---

## Example Observation

A morphological measurement:

- `taxon_id`: TAX_000001  
- `source_id`: SRC_000001  
- `feature`: cell_body  
- `trait`: length  
- `value`: {"mean":6.8,"min":5.2,"max":8.7,"unit":"µm"}  
- `qualifiers`: {"life_stage":["active"],"evidence":["light_microscopy"]}

> Numeric ranges and categorical descriptors are preserved, along with context for life stage, method, or experimental conditions.

---

This design allows **scalable growth**, **easy versioning**, and future **integration with web interfaces, validators, and analysis pipelines**.
