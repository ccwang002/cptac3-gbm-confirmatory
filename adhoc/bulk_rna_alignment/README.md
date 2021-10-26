# Bulk RNA-Seq alignment


## Installation

    conda create -n gbm_gdc_rna \
        python=3.9 \
        snakemake-minimal=6.10.0 \
        samtools=1.10 htslib=1.10 \
        star=2.6.1d



## Pipeline execution

    # Set the temp folder to store BAM intermidate files
    export TMPDIR=$PWD

    snakemake \
        --configfile=snakemake_config.json \
        -s /diskmnt/Projects/Users/lwang/CPTAC3_GBM_confirmatory/adhoc/bulk_rna_alignment/Snakefile \
        -n -- star_align_all_samples

    # Link all RNA-seq FASTQs
    snakemake link_gdc_rna_fastqs

    # Run STAR alignment
    snakemake star_align_all_samples
    snakemake -j 32 --resources io_heavy=4 -- star_align_all_samples

    # Generate BAM manifests under tracked_results
    snakemake gen_washu_bam_map
