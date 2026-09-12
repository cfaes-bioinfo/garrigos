# README for `garrigos`

- Author: Jelmer Poelstra
- Affiliation: CFAES Bioinformatics Core, The Ohio State University
- Contact: <poelstra.1@osu.edu>
- URL: <https://github.com/cfaes-bioinfo/garrigos>
- Created: 2024-01-20
- Last updated: 2026-09-12

This directory contains files associated with the paper
“Two avian _Plasmodium_ species trigger different transcriptional responses on
their vector _Culex pipiens_”
([Garrigós et al. 2025, Molecular Ecology](https://doi.org/10.1111/mec.17240)).
The files are intended for practice in coursework and other tutorials on omics /
RNA-Seq data analysis.
If you use these data beyond practice purposes, please cite the original paper and
obtain the full data from ENA (see the links above).

The rest of this README describes the files in this directory, by sub-directory.

## FASTQ files (in sub-directory `fastq`)

The FASTQ files are paired-end 75-bp Illumina RNA-Seq reads from
_Culex pipiens_ samples: 44 files for 22 samples, with `_R1` and `_R2`
in the file names denoting the forward and reverse reads, respectively.

These were downloaded from the European Nucleotide Archive (ENA)
under study accession `PRJEB41609`, using the tool
[`fastq-dl`](https://github.com/rpetit3/fastq-dl) v3.0.1 on 2024-01-20.

To simplify the dataset for practice purposes, the following modifications were made:

- Files for the following samples were **removed**:
  - 2 samples that were also excluded in the study itself
    (see the paper for details).
  - All samples at the 21-day (21 DAI) time point.

- Files were randomly "**subset**" to keep only 500,000 reads per file using
  the tool [`seqtk`](https://github.com/lh3/seqtk) v1.3-r106.

- Files were **renamed** by removing the shared ENA prefix `ERR108028` and
  replacing it with `S` (for "sample"), and by replacing the `_1` and `_2` suffixes
  by `_R1` or `_R2` to denote the forward and reverse reads.

## Metadata (in sub-directory `meta`)

Metadata from the study was downloaded from <https://doi.org/10.20350/digitalCSIC/15708>
and simplified to keep only:

- The sample ID, time point, and treatment columns
- The samples for which the FASTQ files were retained (see above)

## Reference annotation file (in sub-directory `ref`)

A reference genome GTF file with the RefSeq annotation of the
_Culex pipiens pallens_ genome assembly `TS_CPP_V2` (`GCF_016801865.2`)
was downloaded from NCBI using the
[NCBI Datasets tool](https://www.ncbi.nlm.nih.gov/datasets/docs/v2/download-and-install/)
v15.31.1 on 2024-01-20.
The GTF file was renamed to `annot.gtf.gz` and gzipped.

For the analysis of the data, the reference genome FASTA file is also needed.
This is not included here, but can be downloaded from NCBI using:

```bash
wget https://ftp.ncbi.nlm.nih.gov/genomes/all/GCF/016/801/865/GCF_016801865.2_TS_CPP_V2/GCF_016801865.2_TS_CPP_V2_genomic.fna.gz
```
