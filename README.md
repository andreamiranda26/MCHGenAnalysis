# MCHGenAnalysis
---
Mulchatna caribou project analysis
author: 
    - Andrea Miranda
    - Gabriel Silva
    - Janna Willoughby
date: 07/31/24
---

## Introduction

This is a project to analyze the caribou population in Alaska. The data was collected by Andrea Miranda Paez and her team. The data is stored in the `data/` directory. The analysis is stored in the `analysis/` directory.

## Data

### Raw data

Raw fastq files are located in the `data/raw/` directory as symbolic links to the original files.

### Filtered data

Quality control files are located in the `data/fastp/` directory.

### Reference genome

Genome assembly **mRanTar1.h1.1** of _Rangifer tarandus_ (GenBank GCA_949782905.1) was used as the reference genome. It is stored in the `data/reference/` directory.

## Analysis

All the programs run in this analysis are stored in the `run/` directory, and further divided into `VariantCalling/` and `PopulationGenetics/`.

The analysis is divided into the following steps:

1. Variant calling and filtering
    1. Quality control
        1. runMe_fastp.sh

    2. Read mapping
        1. sbatchMe_bwa2_idx.sh
        2. runMe_bwa2_mem.sh
        3. sbatchMe_samtools_merge.sh

    3. Variant calling
        1. sbatchMe_samtools-faidx.sh
        2. sbatchMe_samtools-idx.sh
        3. sbatchMe_freebayes.sh

    4. Filtering
        1. sbatchMe_bcftools.sh

2. Population genetics analysis
    1. Adegenet
    2. Admixture
        1. sbatchMe_Plink.sh / sbatchMe_Plink_ntg.sh
        2. runMe_admixture.sh / runMe_admixture_ntg.sh
        3. runMe_plot_admixture.sh
    3. STRUCTURE
        1. sbatchMe_PGDSpdier.sh / sbatchMe_PGDSpdier.ntg.sh
        2. runMe_Structure.sh / runMe_Structure.ntg.sh
        3. runMe_plot_structure.sh NOTE: This is not yet implemented


List of programs used and their versions:

* Fastp - 0.23.4
* BWA-MEM2 - 2.2.1
* Samtools - 1.19.2
* BCFTools - 1.19
* Freebayes - 1.3.7
