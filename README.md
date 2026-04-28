# speciate_v5.4_cleanup

## Description

`speciate_v5.4_cleanup` is designed to clean the `SPECIATE v5.4` database up.
`SPECIATE` is a database maintained by the US EPA that contains speciation profiles for organic gases and particulate matter (PM) emitted from various air pollution sources.
More information is available at https://www.epa.gov/air-emissions-modeling/speciate.

## What does the script do

Main cleanup steps:

1. Check Name, CAS, CAS no hyphen, SPECIES_NAMES for odd characters and edit values.

2. Create weight_fraction column and populated it with values calculated based on WEIGHT_PERCENT column values.

3. Format CAS and ensure text format to avoid unwanted Excel conversion.

4. Save unique Name, CAS#, Smiles Notation, and DSSTox_ID set for PubChem InChIkeys and other useful data retrieval:

- Retrieve data using PubChem_Retriever (available at https://github.com/r3bryk/PubChem_Retriever).
- Update SPECIATE with the retrieved data using Data_Retriever (available at https://github.com/r3bryk/Data_Retriever).

5. Write filtered SPECIATE (intermediate) to CSV file if needed.

6. Load SPECIATE updated with PubChem InChIKeys and other data.

7. Remove compounds:

- With no InChIKey values.
- With specific InChIKey values (e.g., mixtures, inorganic compounds & inorganic mixtures, etc.).
- With unwanted keywords (e.g., mixtures, minerals, inorganic compounds & inorganic mixtures, etc.).

8. Sort and save filtered CPDat as CSV file.

## Prerequisites

1. The script is written in Python 3; https://www.python.org/downloads/windows/.
2. The script is run in JupyterLab Notebook; https://jupyter.org/.

## How to use the script

Run the script cell by cell in JupyterLab Notebook.

## License

[![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/license/mit)

Intended for academic and research use.
