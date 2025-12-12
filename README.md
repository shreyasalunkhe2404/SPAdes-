# SPAdes-

Assembling genomes using Spades

## Step 1- Acquiring SRA from the NCBI database

```bash
conda create -n sratoolkit
conda activate sratoolkit
conda install -c sratoolkit

# Downloading raw files

prefetch ncbi/link/to/the/SRAfile or SRR1111111

# convert the zip file into the common FASTQ format

fasteq-dump SRR1111111

# Splitting file into forward or reverse read files

fastq-dump -I --split-files SRR1111111
```

## Step 2- Assembling genome using Spades

```bash
conda create -n spades
conda activate spades
conda install -c spades

# Assembling forward and reverse reads

spades.py -t 45 -m 500 --isolate  -1 SRR1111111_1.fastq -2 SRR1111111_2.fastq -o Output_dir

# Assembling a merged reads

spades.py -t 45 -m 500 --isolate --12 DRR1111111_1.fastq -o  Output_dir     
