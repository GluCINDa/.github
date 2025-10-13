
<a href="url"><img src="https://github.com/GluCINDa/.github/blob/main/GluCINDa_logo_Schriftzug_V3.png" align="center" height="143" width="304" ></a>



# What is GluCINDa?
GluCINDa (Glucose: Coherent Import. Neat Data.) is a Python-based application developed to improve the data quality in research involving Continuous Glucose Monitoring (CGM). The fact that there are several CGM manufacturers, various device types and generations and different methods of exporting the data (aside from different languages, units and file formats) leads to a significant heterogeneity in file and table structures, especially when working with user-generated CGM exports. Moreover, data exports are not always machine-readable (i.e. formally structured), the worst case we encountered being a change in table structure within the same document. Until now, importing and harmonizing CGM data for statistical analysis required a lot of manual coding and checking which took up an undue share of the respective overall project time and has also lead to data loss. GluCINDa was created to handle such a complicated database with efficiency, accuracy and transparency and, thus, improve the quality of diabetes research as a whole. 

## Is GluCINDa a medical device?
No! GluCINDa is a research tool, not a medical device, and therefore must not be used in any clincal capacity whatsoever. 

# How does GluCINDa work?
GluCINDa employs an algorithmic approach (rather than rely on AI) to extract glucose values and corresponding timestamp from a multitude of different CGM exports. GluCINDa analyzes each file row-by-row and identifies potential CGM values if a header above the respective cell contains a glucose-related keyword (like "gluc" or "CGM") and the actual value is a number with a maximum of three digits or a string (like "high" or "low"). A potential CGM value is confirmed and stored if a corresponding complete timestamp (date and time) is found. If available, GluCINDa stores additional information (device ID, sequence information other than a timestamp). In any case, the name of the glucose-related header and the file name is saved with each extracted CGM value.

## What CGM files can GluCINDa process?

- can process anything, will skip files/imports
- needs date, time, CGM value in aptly named column
- tested with: LibreView, Clarity, CareLink, iCan app, Glooko

# (How) do I need to prepare the input files?
One manufacturer per file!!!!!

GluCINDa extracts the participant ID from the file name (the first characters followed by an underscore). This means that if you do pseudonymization, you do not have to open the CGM files and manually change participants' real names there (manually changing anything in a datafile is never a good look, after all). You or the person doing the pseudonymization only has to change the file name accordingly. Here is an example: 

> pid0001_CGMdownload.csv

Because GluCINDa also stores the source file name with each extracted CGM value, you can use the filename to convey other information that you need for your analysis. For example, if you have multiple study phases per participant stored in separate files, you can indicate that in the file name followed by another underscore for easy separation later:

> pid0001_phase1_CGMdownload.csv
> 
> pid0001_phase2_CGMdownload.csv

Similarly, you could convey parallel sensors (of different manufacturers):

> pid0001_phase1_sensor1_Libre3_CGMdownload.csv
> 
> pid0001_phase1_sensor2_Libre3_CGMdownload.csv
> 
> pid0001_phase1_sensor3_G7_CGMdownload.csv


# How do I use GluCINDa?
## Requirements
1. Python
2. additional modules: chardet, csv, datetime, glob, openpyxl, multiprocessing, os, pandas, pathlib, pyarrow, pybtex, PySide6, setuptools, statistics, sys, time, traceback, unittest, xlrd
3. `git` needs to be installed on your system for the installation of GluCINDa


## Installation
1.  Install missing requirements
    ```bash
    pip3 install chardet csv datetime glob openpyxl multiprocessing os pandas pathlib pyarrow pybtex PySide6 setuptools statistics sys time traceback unittest xlrd
    ```

2.  Install the GluCINDa repository
   *   `cd` into the directory where you want to install GluCINDa (example: `/glucinda_app/`)
        ```bash
        cd /glucinda_app/
        ```
        
   *   Clone the GUI repository , then `cd` into it and install the submodules *generalparser* and *cgm_extractor*
        ```bash
        git clone https://github.com/GluCINDa/GluCINDa_GUI.git GluCINDa/
        cd GluCINDa
        git submodule init generalparser/
        git submodule init cgm_extractor/
        git submodule update --remote
        ```


## Running GluCINDa
1. Open a terminal and type the following to start GluCINDa's Graphical User Interface (GUI)

  ```bash
    cd /glucinda_app/GluCINDa
    python3 glucinda.py
  ```

2. Provide the filepath to your input folder
3. GluCINDa automatically suggests an output folder path, but you can choose your own. GluCINDa warns you if the output folder is not empty as it will get overwritten. You have to empty the folder manually to prevent accidentally overwriting files.
4. In advanced mode, choose:
   * The format of the combined output file (CSV, XLSX). Deselect both if you only want individual files.
   * If you want individual file outputs (in addition to the combined output file)
   * In case you want individual outputs, if you want individual file documentation and in in what format (TXT, HTML). Keep in mind, that HTML files take up much more space than TXT files (they look prettier, however).


# What is the output of GluCINDa?

## Imported and harmonized data
- **parsed_all.csv**: 
- **parsed_all_just_cgm.csv**: GluCINDa identifies columns with a median time interval of either 5 or 15 minutes, which are typical for CGM data, and stores the respective values in a separate file. If you only want the regular CGM data stream without any scanned or calibration values, you can directly use this file. However, we recommend to do plausibility checks on this file before using it in analyses.
- **parsedNNNN.csv**: If preferred you can (also) get separate imports for each input file. 

## Reports
- **parsing_report.csv**: For each input file, the parsing report lists the extracted participant ID, the number of lines in the input file, the number of extracted lines and the earliest and latest date in the data.
- **skipped_files.csv**: The files GluCINDa ignored in your input folder. 
- **skipped_imports.csv**: CSV and XLSX files that were handled by GluCINDa, but did not yield CGM data. Check this to see if something you expected to have CGM data could not be handled by GluCINDa.

## Documentation of individual files
- If you choose to get individual imports as well, you can also get documentation (as TXT and/or HTML) for each and every step GluCINDa took to import and harmonize the respective file. You can then trace each extracted value and do some more fine-grained debugging and checking. 


# What else?
- We'd appreciate if you would reference GluCINDa if you use her for a publication: 
> Hier könnte ihre bib-Citation stehen :D

- If you find a bug, please let us know (start an issue on Github).

- Open source use => *[legal department will advise]*


**Thank you for using GluCINDa!**
