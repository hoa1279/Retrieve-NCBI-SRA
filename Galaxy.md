# Use galaxy to access NCBI project data
### 1. Find project PRJNA923804 and SRA info
- Search for sequence project in [NCBI](https://www.ncbi.nlm.nih.gov/bioproject/)
- Click to SRA Experiment link
- In result window, Click "Send Results to Run Selector"

The SRA Run Selector will open with a list of all items in the project.

### 2. Link data to Galaxy
Click Select All then Click "Galaxy" in Computing column

A dataset name "SRA" will be load to a Galaxy history (may sign in Galaxy to manage history)

### 3. Download fastq linked files: 
In Tools, click Get Data | Faster Dowload and Extract Reads in FASTQ format from NCBI SRA

In the Tool Parameters window:
- select input type: List of SRA accession, one per line
- sra accession list: select file: 1.SRA (or upload a file)
- Click Run Tool
Output fastq datasets produced will be saved in Galaxy's history as a collection.

Download the collection for local use or continue data analysis in Galaxy.

For more information [fasterq_dump](https://usegalaxy.org/root?tool_id=toolshed.g2.bx.psu.edu/repos/iuc/sra_tools/fasterq_dump/3.0.5+galaxy3)
