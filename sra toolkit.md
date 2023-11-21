# Use NCBI [SRA toolkit](https://github.com/ncbi/sra-tools)
Instruction to download multiple SRA runs at a time.

## 1. Download and instal SRA toolkit
Follow the instruction in [sra installing page](https://github.com/ncbi/sra-tools/wiki/02.-Installing-SRA-Toolkit) for dowload and install SRA toolkit.

The following instruction is to install sra toolit in a conda environment using Terminal (Mac).

First, create and activate a new conda environment name sra
```conda
conda create -n sra
conda activate sra
```
Second, download and extract the tar file in to the conda environment folder
```bash
sraPATH="your-conda-environment-path" #set the path of the environment, usually "/Users/<user-name>/anaconda3/envs/sra"
curl --output $sraPATH/sratoolkit.tar.gz https://ftp-trace.ncbi.nlm.nih.gov/sra/sdk/current/sratoolkit.current-mac64.tar.gz
tar -vxzf $sraPATH/sratoolkit.tar.gz -C $sraPATH
ls $sraPATH #check the name of extract file
```
Third, append the sratoolkit path to the PATH of the current environment 
```bash
export PATH=$PATH:$sraPATH/sratoolkit.3.0.7-mac64/bin  #change the directory name to the actual folder name in $sraPATH
```
Run test
```bash
fastq-dump --stdout -X 2 SRR390728
```

## 2. Finding SRA accession
Find Project in NCBI then navigate to the [SRA Run Selector](https://www.ncbi.nlm.nih.gov/Traces/study/?query_key=8&WebEnv=MCID_654a4f1ed3f9893f5e1bd6fa&o=acc_s%3Aa)
Download the Accession List to current working directory of Terminal.
```bash
pwd #to check the current working directory
cd <directory-path> #change working directory
```

Alternatively, you can make a SRR_Acc_List.txt with the list of accession numbers that you want to download. 
## 3. Download fastq files of each SRA run
```bash
prefetch $(<SRR_Acc_List.txt)  #~1min per 1 sra
cat SRR_Acc_List.txt | xargs fasterq-dump --outdir fastq
```
Check [fasterq-dump](https://github.com/ncbi/sra-tools/wiki/08.-prefetch-and-fasterq-dump) for more options.

