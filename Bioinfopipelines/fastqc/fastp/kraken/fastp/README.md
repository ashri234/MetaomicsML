Kraken 2: A Taxonomic Sequence Classification Tool
Overview
Kraken 2 is a highly accurate and ultrafast taxonomic classifier for metagenomic sequence data. It assigns taxonomic labels to DNA sequences (reads) by examining k-mers within the sequences and mapping them to a database of known genomes.
It is widely used in metagenomics, microbiome studies, and pathogen detection.

Key Features
Speed & Efficiency
Exact Alignment of k-mers
Low Memory Requirement
Custom Database Support
Classification at Multiple Taxonomic Levels
How Kraken 2 Works
Database Construction

Builds a reference database from known genomes.
Compresses k-mers into a more memory-efficient format.
Sequence Classification

Reads are split into k-mers.
Each k-mer is searched in the database.
Kraken assigns the lowest common ancestor (LCA) of all matched taxa to the read.
Output

Produces a classification report showing taxonomic breakdown of reads.
Can be used with Bracken (a companion tool) for more accurate abundance estimation.
Typical Workflow
1. Download or Build Database
Command 1: Downloading a Reference Library
kraken2-build --download-library bacteria --db kraken2_db
Breakdown:
kraken2-build : Utility used to build or manage Kraken 2 databases.
--download-library bacteria : Downloads the reference genome library for bacteria from NCBI RefSeq.
--db kraken2_db : Specifies the name/location of the database directory (kraken2_db) where the library files will be stored.
Command 2: Building the Database
kraken2-build --build --db kraken2_db
Breakdown:
kraken2-build : The same utility for database handling.
--build : Processes the downloaded reference sequences to construct the Kraken 2 database.
--db kraken2_db : Tells Kraken 2 which database directory to use (kraken2_db).
This command builds the actual searchable classification database from the downloaded bacterial genomes.

Command 3: Running the command
Command
kraken2 --db kraken2_db_uhgg_v2.0.2 --threads 32 \
        --report kraken2_output/ERR14218891.k2report \
        --classified-out kraken2_output/ERR14218891_classified.fastq \
        --unclassified-out kraken2_output/ERR14218891_unclassified.fastq \
        --output kraken2_output/ERR14218891.kraken2.out \
        bowtie2_output/ERR14218891_nonhuman.fastq.1.gz \
        bowtie2_output/ERR14218891_nonhuman.fastq.2.gz
Breakdown of Options
Option	Description
kraken2	Runs the Kraken 2 classifier for metagenomic sequence classification.
--db kraken2_db_uhgg_v2.0.2	Specifies the Kraken 2 database to use. Here, the UHGG v2.0.2 database (Unified Human Gastrointestinal Genome collection) is used.
--threads 32	Uses 32 CPU threads for faster parallel processing.
--report kraken2_output/ERR14218891.k2report	Generates a classification summary report with taxonomic breakdown of reads.
--classified-out kraken2_output/ERR14218891_classified.fastq	Stores all reads that were classified by Kraken 2 into this FASTQ file.
--unclassified-out kraken2_output/ERR14218891_unclassified.fastq	Stores all reads that were not classified into this FASTQ file.
--output kraken2_output/ERR14218891.kraken2.out	Produces a detailed classification result file with per-read taxonomic assignments.
bowtie2_output/ERR14218891_nonhuman.fastq.1.gz	Input file 1: First set of non-human paired-end reads (R1).
bowtie2_output/ERR14218891_nonhuman.fastq.2.gz	Input file 2: Second set of non-human paired-end reads (R2).
Summary
This command runs Kraken 2 on paired-end sequencing reads that have already been filtered to remove human sequences (using Bowtie2).

Database used: UHGG v2.0.2 (Unified Human Gastrointestinal Genome collection).
Outputs generated:
.k2report → Taxonomic summary report.
.classified.fastq → Reads assigned to taxa.
.unclassified.fastq → Reads not assigned to any taxa.
.kraken2.out → Detailed per-read classification.
Performance: Uses 32 threads for faster computation.
📦 Database Requirements
Kraken2 Database
Based on the Unified Human Gastrointestinal Genome (UHGG) v2.0.2
Download link
