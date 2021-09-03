# SARS-CoV-2 Indel Finder

## Purpose:
This python script accomplishes the following:
- takes a set of sars-cov-2 sequences (either as a multi sequence fasta or a directory of single sequence fasta files) and aligns each to the reference genome (pairwise alignment)
- identifies all insertions and deletions within each sample sequence and generates an output table
- removes nucleotide insertions from sample sequences
- using the pair-wise alignments generates a MSA (multi sequence alignment) output alignment fasta

## Requirements:
- The python modules neccessary to run this script are contained in a conda environment; therefore so you must have Anaconda or miniconda installed.
- MAFFT seqeunce aligner (I used v7.471 on my machine)
-
# Preparing your environment:
This only needs to be performed the first time you run the script.
1. Clone the repository to your machine and change directories to the repository on your machine.

``git clone https://github.com/CDPHE/sars-cov-2_indel_finder``

`` cd sars-cov-2_indel_finder``

2. Create the conda environment using the ```environment.yml``` file. The environment's name should be ```indel_finder_env```

``conda env create -f environment.yml``

3. If the environment already exists then to update the environment
``conda env update -f environment.yml``

3. Check that the environment exists. The name of the enivornment should be `indel_finder_env`

``conda env list``

4. Activate the conda environment

``conda activate indel_finder_env``

## Inputs:
- Sample sequences either as:
  - a multi sequence fasta file
  - directory with single sequence fasta files
- Reference genome

## Running the script
1. Activate teh conda environment
``conda activate indel_finder_env``

2. Run the script usinig the followig flags:
  - ``-i``: either the path to the multi sequence fasta or the path to the directory wtih single sequence fasta files
  - ``-o`` : path to where you would like the outputs to go
  - ``ref_path``: path to the reference genome
  -``--prefix``: (optional) prefix used to save outputs, if not specified will default to today's date

  - note use complete paths!!

  3. Putting it all together:
  ``indel_finder.py -i <multi_sequence.fasta> -o . --ref_path <path_to_ref_genome> --prefix <prefix> ``

## Outputs:
1. ``<prefix>_indels.csv`` : table providing the sequence name, the nucleotide bps of the indel (either (+) for insertions or (-) for deletions), the start position of the indel, the length of the indel, and the 7 upstream and 7 downstream nucleotides surrounding the indel.
2. ``<prefix>.aligment.fasta`` : MSA
