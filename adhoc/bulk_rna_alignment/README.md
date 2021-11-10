# Bulk RNA-Seq alignment


## Installation

    conda create -n gbm_gdc_rna \
        python=3.9 \
        snakemake-minimal=6.10.0 \
        samtools=1.10 htslib=1.10 \
        star=2.6.1d


## Pipeline execution

    # Set the temp folder to store BAM intermidate files
    mkdir $PWD/tmp
    export TMPDIR=$PWD/tmp

    # Run STAR alignment and Generate output manifest
    snakemake \
        --configfile=snakemake_config.json \
        -s /diskmnt/Projects/Users/lwang/CPTAC3_GBM_confirmatory/adhoc/bulk_rna_alignment/Snakefile \
        -j 32 --restart-times 2 \
        --resources io_heavy=2 \
        -- \
        make_washu_output_manifest

The manifest containing all output files is available at `washu_rnaseq_alignment_summary.tsv`.