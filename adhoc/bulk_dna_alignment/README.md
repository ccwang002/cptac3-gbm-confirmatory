# Bulk DNA-Seq (WXS\[WES\] and WGS) alignment


## Installation

    conda create -n gbm_gdc_dna \
        python=3.9 \
        snakemake-minimal=6.10.0 \
        samtools=1.10 htslib=1.10 \
        biobambam=2.0.87 \
        bwa=0.7.17 \
        picard=2.19.0


## Pipeline execution

    # Set the temp folder to store BAM intermidate files
    mkdir $PWD/tmp
    export TMPDIR=$PWD/tmp

    # Run DNA alignment and Generate output manifest
    snakemake \
        --configfile=snakemake_config.json \
        -s /diskmnt/Projects/Users/lwang/CPTAC3_GBM_confirmatory/adhoc/bulk_dna_alignment/Snakefile \
        -j 50 --restart-times 2 \
        --resources io_heavy=4 \
        -- \
        make_washu_output_manifest

    # Clean up the FASTQs
    rm -rf bam_to_fastqs/*

The manifest containing all output files is available at `washu_dnaseq_alignment_summary.tsv`.