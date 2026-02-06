# API guided literature searches

we are usinga set of target journals, where protist species are likely to be described.

Exhaustively harvest candidate taxonomic description papers from target journals



```sh
TARGET_JOURNALS = [
    "Protist",
    "European Journal of Protistology",
    "Journal of Eukaryotic Microbiology",
    "Acta Protozoologica",
    "Journal of Phycology",
    "European Journal of Phycology",
    "Phycologia",
    "Cryptogamie Algologie",
    "Nova Hedwigia",
    "Phytotaxa",
    "Phycological Research",
    "Diatom Research",
    "Harmful Algae",
    "PLoS ONE",
    "Current Biology",
    "The Journal of Protozoology",
    "British Phycological Journal",
    "Nature",
    "The ISME Journal",
    "Scientific	Reports",
    "Protoplasma",
    "Proceedings of the National Academy of Sciences",
    "Botanica Marina",
    "Journal of Foramineferal Research",
    "Polar Biology",
    "ALGAE",
    "Antonie van Leeuwenhoek",
    "Frontiers in Microbiology"
]
```

titles are filterd using `TITLE_KEYWORDS` to enable detection of probable description papers.

```sh
TITLE_KEYWORDS = [
    "sp. nov",
    "gen. nov",
    "new species",
    "novel species",
    "description",
    "taxonomy",
    "taxonomic",
]
```