# MCSKL

[![CC BY-NC-SA 4.0][cc-by-nc-sa-shield]][cc-by-nc-sa]

- [MCSKL](#mcskl)
  - [Repository organization](#repository-organization)
  - [Metadata](#metadata)
  - [Verticalized content](#verticalized-content)
  - [How to cite](#how-to-cite)
  - [References](#references)
  - [Changelog](#changelog)

The [Multimedia Corpus of Spoken Kazakh Language](https://research.nu.edu.kz/en/projects/multimedia-corpus-of-modern-spoken-kazakh-language/)
is compiled at the Languages, Linguistics, and Literature department of Nazarbayev University,
funded through the Nazarbayev University Collaborative Research Project fund grant 021220CRP1422.

In this repository, the first module of the corpus is released. The first module consists of approximately
12 hours of spoken data collected across different regions of Kazakhstan.
The 33 speech events, recorded between 2021 and 2023, involve 78 participants from various regions
of Kazakhstan and Xinjiang (China). All the files include naturally occurring conversation according to
the definition proposed by [Troiani and colleagues (2024)](https://ricl.aelinco.es/index.php/ricl/article/view/332).

Audio files and transcriptions have been anonymized.

## Repository organization

This repository contains:

* metadata for both speakers and conversations (see [metadata](#metadata) section below)
* descriptions of the set of transcription conventions used for this module ([Transcription conventions](./DFT-notation.md))

For each conversation you will find:

* `.wav` file in [`audio/`](./audio/) folder
* `.eaf` file in [`eaf/`](./eaf/) folder: time-aligned Discourse Functional Transcription-style transcriptions (open with [ELAN](https://archive.mpi.nl/tla/elan)).
* `.tsv` file in [`tsv/`](./tsv/) folder: verticalized version of the transcription, with DFT-style information decoupled from the text as features See [verticalized-content](#verticalized-content) for more information.
* `.txt` file in [`linear/`](./linear/) folder: linearized DFT-style transcription with translations

## Metadata

Each participant and each conversation are associated to a series of metadata, that can be found in the
[`metadata/participants.csv`](metadata/participants.csv) and [`metadata/speech_events.csv`](metadata/speech_events.csv) files.
Metadata is to be interpreted as follows:

1. Participants metadata:
    - `Participant ID`: unique anonymized 4-num identifier for each participant.
    - `Gender`: either `M` for masculine or `F` for feminine.
    - `Age`: age at the time of recording.
    - `Birthplace`: Kazakh region where participants were born and first acquired Kazakh language.
    - Additionally, the [`metadata/participants.tsv`](metadata/participants.tsv) also contains a `conversations` colum that summarizes

2. Conversations metadata:
   - `File`: unique identifier for conversation.
   - `Year`: year of collection.
   - `Speaker`: the conversations in which the participant appears.
   - `Event description` : summary of conversation; in case of mention of potentially sensitive topics, these are noted here.
   - `Date` : date of collection.
   - `Genre` : type of interaction, either `conversation` or `interview` or `task-directed talk`.
   - `Place` : regional area of collection.
   - `Setting`: either face-to-face in a `city`or in a `village`, or `online`.
   - `Running time`: duration of the conversation, expressed in `hh:mm:ss` format.


## Verticalized content

Conversations are also available in a vertical, pseudo-tokenized version in [`tsv/`](./tsv/).
Tokenization is obtained by validating the DFT transcription using custom tools and splitting on token boundaries (whitespaces). Each transcription-derived token is then documented on one row.

Each token is represented as 10 columns, as follows:

1. `token_id`: unique token identifier within the conversation
2. `speaker`: speaker `code` as it can be found in [`metadata/participants.csv`](metadata/participants.csv)
3. `iu_type`: intonation contour of the iu according to the DFT conventions found in [`DFT-notations.md`](DFT-notations.md)
4. `tu_id`: progressive identifier assigned to translation units
5. `iu_id`: progressive identifier assigned to intonation units
6. `span`: portion of the original DFT-style transcription containing the token
7. `form`: orthographic form of the token. This differs from the `span` as special symbols are stripped out.
8. `type`: one of
   - `linguistic`: everything that is considered to be a content linguistic token
   - `paraverbal:` used for transcribed non verbal behaviors, such as laughing or sighing
   - `unknown` that identify unintelligible spans in transcription
9. `features`: the column collects a list of word-level features derived from the transcription in DFT format. More specifically:
10. `align`: alignment features for the first and last token of each TU, through `AlignBegin` and `AlignEnd` features expressed in seconds

## How to cite

If you use the Multimedia Corpus of Spoken Kazakh Language in your research, please reference this repository (commit/tag) in your data statement or appendix.

## References

Troiani, Giorgia, John W. Du Bois, and Andrey Filchenko. 2024. “Corpus as a Slice of Life: Representing Naturally Occurring Language and Its Speakers.” Research in Corpus Linguistics 12 (2): 2. https://doi.org/10.32714/ricl.12.02.08.

```
@article{troiani2024corpus,
  author  = {Troiani, Giorgia and Du Bois, John W. and Filchenko, Andrey},
  title   = {Corpus as a Slice of Life: Representing Naturally Occurring Language and Its Speakers},
  journal = {Research in Corpus Linguistics},
  year    = {2024},
  volume  = {12},
  number  = {2},
  pages   = {2},
  doi     = {10.32714/ricl.12.02.08},
  url     = {https://doi.org/10.32714/ricl.12.02.08}
}
```

## Changelog

* 2026-02-17 v1.0.0
  * First release

-----

This work is licensed under a
[Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License][cc-by-nc-sa].

<!-- [![CC BY-NC-SA 4.0][cc-by-nc-sa-image]][cc-by-nc-sa] -->

[cc-by-nc-sa]: http://creativecommons.org/licenses/by-nc-sa/4.0/
[cc-by-nc-sa-image]: https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png
[cc-by-nc-sa-shield]: https://img.shields.io/badge/License-CC%20BY--NC--SA%204.0-lightgrey.svg
