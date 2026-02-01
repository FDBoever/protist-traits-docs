# taxonomic data integration

- GBIF
- IRMNG
- ZooBank
- WorMS
- Catalogue of Life

## WoRMS - World Register of Marine Species

https://www.marinespecies.org/

we used custom python scripts to query WoRMS API, json files were converted in tabular tsv files.

## GBIF - Global Biodiversity Information Facility 

https://www.gbif.org/

downloaded for integration on 01-feb-2026 latest release 2023-08-28 15:18
from https://hosted-datasets.gbif.org/datasets/backbone/

```sh
curl -o downloaded_datafiles/gbif/backbone.zip https://hosted-datasets.gbif.org/datasets/backbone/current/backbone.zip
unzip downloaded_datafiles/gbif/backbone.zip -d downloaded_datafiles/gbif/
```

data extraction is currently implemented in `./scripts/scripts/extracextract_from_gbif_backbone.py`

```sh
python scripts/extract_from_gbif_backbone.py
```


## IRMNG - Interim Register of Marine and Nonmarine Genera

https://www.irmng.org/

IRMNG export in Darwin Core Archive (DwC-A) format 
downloaded for integration on 01-feb-2026 latest release 2025-07-11 10:48 (89M)
from https://www.irmng.org/export/IRMNG_genera_DwCA.zip

zip file contains taxon.txt and reference.txt
within taxon.txt, column "kingdom" (11th column) was used to filter taxa records that are putative protists "Chromista|Protozoa|Protista" 
The retrieved TaxonIDs are used to filter the reference.txt to only include references to the filtered taxon set.


currently implemented in `./scripts/scripts/extract_from_irmng.py`

```sh
python scripts/extract_from_irmng.py
```

the below bash code reflects how we used to do it in the past

```sh
# obtain data release
curl -o downloaded_datafiles/irmng/IRMNG_genera_DwCA.zip https://www.irmng.org/export/IRMNG_genera_DwCA.zip

#unzip
unzip downloaded_datafiles/irmng/IRMNG_genera_DwCA.zip -d downloaded_datafiles/irmng/

#show columns that exist
 cat /Users/frederikdeboever/DATA/protist-traits/downloaded_datafiles/irmng/IRMNG_genera_DwCA/taxon.txt | head -n 1 | tr '\t' '\n'                                       

#show unique entries for column 11
 cut -f11 /Users/frederikdeboever/DATA/protist-traits/downloaded_datafiles/irmng/IRMNG_genera_DwCA/taxon.txt | tail -n +2 | sort | uniq -c | sort -nr

#extract protist candidates based on kingdom
cat /Users/frederikdeboever/DATA/protist-traits/downloaded_datafiles/irmng/IRMNG_genera_DwCA/taxon.txt | awk -F'\t' 'NR==1 || $11=="Chromista" || $11=="Protozoa || $11=="Protista""' > irmng_protist_candidates.tsv

#inspect what was colleted
cut -f12 irmng_protist_candidates.tsv | tail -n +2 | sort | uniq -c | sort -nr
cut -f13 irmng_protist_candidates.tsv | tail -n +2 | sort | uniq -c | sort -nr

# extract taxon ids
cut -f1 ./irmng_protist_candidates.tsv | tail -n +2 | sort -u > irmng_protist_taxonIDs.txt

# use taxon ids to filter references
awk -F'\t' '
NR==FNR { ids[$1]=1; next }
FNR==1 || ($1 in ids)
' irmng_protist_taxonIDs.txt \
  /Users/frederikdeboever/DATA/protist-traits/downloaded_datafiles/irmng/IRMNG_genera_DwCA/reference.txt \
> irmng_protist_references.tsv
```


## Catalogue of Life

Catalogue of Life Data Package (CoLDP) and the Darwin Core Archive (DwC-A)

downloaded CoLDP format for integration on 01-feb-2026 latest release 2026-01-13 19:34 (1.0G)
from https://download.checklistbank.org/col/latest_coldp.zip


