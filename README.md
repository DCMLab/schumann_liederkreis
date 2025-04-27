![Version](https://img.shields.io/github/v/release/DCMLab/schumann_liederkreis?display_name=tag)
[![DOI](https://zenodo.org/badge/388184940.svg)](https://doi.org/10.5281/zenodo.14997104)
![GitHub repo size](https://img.shields.io/github/repo-size/DCMLab/schumann_liederkreis)
![License](https://img.shields.io/badge/license-CC%20BY--NC--SA%204.0-9cf)


This is a README file for a data repository originating from the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora)
and serves as welcome page for both 

* the GitHub repo [https://github.com/DCMLab/schumann_liederkreis](https://github.com/DCMLab/schumann_liederkreis) and the corresponding
* documentation page [https://dcmlab.github.io/schumann_liederkreis](https://dcmlab.github.io/schumann_liederkreis)

For information on how to obtain and use the dataset, please refer to [this documentation page](https://dcmlab.github.io/schumann_liederkreis/introduction).

When you use (parts of) this dataset in your work, please read and cite the accompanying data report:

_Hentschel, J., Rammos, Y., Neuwirth, M., & Rohrmeier, M. (2025). A corpus and a modular infrastructure for the 
empirical study of (an)notated music. Scientific Data, 12(1), 685. https://doi.org/10.1038/s41597-025-04976-z_

# Robert Schumann – Liederkreis (A corpus of annotated scores)

This corpus of annotated [MuseScore](https://musescore.org) files has been created within  
the [DCML corpus initiative](https://github.com/DCMLab/dcml_corpora) and employs  
the [DCML harmony annotation standard](https://github.com/DCMLab/standards).  

Robert Schumann's op. 39 Liederkreis is one of two works bearing that same title, both of  
which Schumann wrote during his 1840 "Liederjahr" (Year of Song); incidentally, 1840 was  
the same year of Schumann's marriage to Clara Wieck. Other vocal works from  
Schumann's "Liederjahr" include the famous Dichterliebe and Frauenliebe und Leben.  
Incidentally, these works are Schumann's first published works not for solo piano, his only  
known chamber work prior to 1840 being the posthumously published C minor Piano Quartet  
of 1829. It was, in fact, Clara who encouraged Robert to branch out beyond solo-piano genres,  
and the height of emotion showcased in these 1840 songs speaks to a primed sensitivity  
already latent in Robert's practice.  
  
Op. 39, the "Eichendorff Liederkreis," sets excerpts from Joseph von Eichendorff's collection  
Intermezzo. Unlike most other song cycles in Schumann's oeuvre, these poems do not directly  
convey a narrative, instead portraying a series of landscapes and nature images shot through  
with intense and abrupt emotional outbursts. Schumann's piano writing is tightly conjoined  
with melodic figuration, showcasing a logical early extension of his solo-piano technique in  
a vocal context. Our annotations reveal the harmonic framework that supports the rich polyphonic  
details present in this voice-and-piano texture.  

## Getting the data

* download repository as a [ZIP file](https://github.com/DCMLab/schumann_liederkreis/archive/main.zip)
* download a [Frictionless Datapackage](https://specs.frictionlessdata.io/data-package/) that includes concatenations
  of the TSV files in the four folders (`measures`, `notes`, `chords`, and `harmonies`) and a JSON descriptor:
  * [schumann_liederkreis.zip](https://github.com/DCMLab/schumann_liederkreis/releases/latest/download/schumann_liederkreis.zip)
  * [schumann_liederkreis.datapackage.json](https://github.com/DCMLab/schumann_liederkreis/releases/latest/download/schumann_liederkreis.datapackage.json)
* clone the repo: `git clone https://github.com/DCMLab/schumann_liederkreis.git` 


## Data Formats

Each piece in this corpus is represented by five files with identical name prefixes, each in its own folder. 
For example, the first song, *In der Fremde*, has the following files:

* `MS3/op39n01.mscx`: Uncompressed MuseScore 3.6.2 file including the music and annotation labels.
* `notes/op39n01.notes.tsv`: A table of all note heads contained in the score and their relevant features (not each of them represents an onset, some are tied together)
* `measures/op39n01.measures.tsv`: A table with relevant information about the measures in the score.
* `chords/op39n01.chords.tsv`: A table containing layer-wise unique onset positions with the musical markup (such as dynamics, articulation, lyrics, figured bass, etc.).
* `harmonies/op39n01.harmonies.tsv`: A table of the included harmony labels (including cadences and phrases) with their positions in the score.

Each TSV file comes with its own JSON descriptor that describes the meanings and datatypes of the columns ("fields") it contains,
follows the [Frictionless specification](https://specs.frictionlessdata.io/tabular-data-resource/),
and can be used to validate and correctly load the described file. 

### Opening Scores

After navigating to your local copy, you can open the scores in the folder `MS3` with the free and open source score
editor [MuseScore](https://musescore.org). Please note that the scores have been edited, annotated and tested with
[MuseScore 3.6.2](https://github.com/musescore/MuseScore/releases/tag/v3.6.2). 
MuseScore 4 has since been released which renders them correctly but cannot store them back in the same format.

### Opening TSV files in a spreadsheet

Tab-separated value (TSV) files are like Comma-separated value (CSV) files and can be opened with most modern text
editors. However, for correctly displaying the columns, you might want to use a spreadsheet or an addon for your
favourite text editor. When you use a spreadsheet such as Excel, it might annoy you by interpreting fractions as
dates. This can be circumvented by using `Data --> From Text/CSV` or the free alternative
[LibreOffice Calc](https://www.libreoffice.org/download/download/). Other than that, TSV data can be loaded with
every modern programming language.

### Loading TSV files in Python

Since the TSV files contain null values, lists, fractions, and numbers that are to be treated as strings, you may want
to use this code to load any TSV files related to this repository (provided you're doing it in Python). After a quick
`pip install -U ms3` (requires Python 3.10 or later) you'll be able to load any TSV like this:

```python
import ms3

labels = ms3.load_tsv("harmonies/op39n01.harmonies.tsv")
notes = ms3.load_tsv("notes/op39n01.notes.tsv")
```


## Version history

See the [GitHub releases](https://github.com/DCMLab/schumann_liederkreis/releases).

## Questions, Suggestions, Corrections, Bug Reports

Please [create an issue](https://github.com/DCMLab/schumann_liederkreis/issues) and/or feel free to fork and submit pull requests.

## Cite as

> Hentschel, J., Rammos, Y., Neuwirth, M., & Rohrmeier, M. (2025). A corpus and a modular infrastructure for the empirical study of (an)notated music. Scientific Data, 12(1), 685. https://doi.org/10.1038/s41597-025-04976-z

## License

Creative Commons Attribution-NonCommercial-ShareAlike 4.0 International License ([CC BY-NC-SA 4.0](https://creativecommons.org/licenses/by-nc-sa/4.0/)).

![cc-by-nc-sa-image](https://licensebuttons.net/l/by-nc-sa/4.0/88x31.png)

## Overview
|file_name|measures|labels|standard|annotators | reviewers  |
|---------|-------:|-----:|--------|-----------|------------|
|op39n01  |      28|    47|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n02  |      30|    66|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n03  |      72|   106|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n04  |      39|    53|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n05  |      68|    83|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n06  |      30|    68|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n07  |      39|    66|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n08  |      39|    88|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n09  |      28|    86|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n10  |      41|   108|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n11  |      50|    67|2.1.0   |Uli Kneisel|Adrian Nagel|
|op39n12  |      31|    54|2.1.0   |Uli Kneisel|Adrian Nagel|


*Overview table automatically updated using [ms3](https://ms3.readthedocs.io/).*
