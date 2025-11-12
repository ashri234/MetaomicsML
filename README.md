# Bracken Tool

## Overview
**Bracken (Bayesian Reestimation of Abundance with Kraken)** is a statistical tool designed to improve species- and genus-level abundance estimates from **Kraken2** classification outputs.

Kraken classifies reads using exact k-mer matches, but it often assigns reads to higher taxonomic ranks (genus or family) if multiple species share similar k-mers. Bracken refines these results by **redistributing reads from higher taxonomic levels down to species or genus levels**, providing a more accurate abundance estimation.

## Key Features
- Works on top of **Kraken2 outputs**.
- Provides more accurate **relative abundance** of species/genus.
- Uses **Bayesian inference** to re-estimate abundances.
- Handles cases where reads are ambiguously classified by Kraken.

## Workflow
1. Run Kraken2 to classify your sequencing reads.
2. Use Bracken to refine abundance estimates.
3. Analyze output files for species-level data.

## Files in This Folder
- `ERR14218664_bracken_species...`: Bracken output for sample ERR14218664
- `combine_bracken_outuput.py`: Python script to combine multiple Bracken outputs
- `combined_otu_data.tsv`: Combined OTU abundance table

## Requirements
- Kraken2 installed and configured
- Bracken installed
- Reference database for Kraken2/Bracken

## Usage

