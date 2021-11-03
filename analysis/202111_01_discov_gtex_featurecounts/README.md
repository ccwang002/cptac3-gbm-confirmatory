## Generate FPKM and FPKM-UQ values for CPTAC3 GBM discovery GTEx normal samples
Source: stranded featureCounts output on katmai at `/diskmnt/Projects/cptac_scratch_4/cptac3-gbm-analysis/201908_gene_quantification/processed_data` ([link]). It takes the WashU aligned BAMs (already removed) but the alignment should be nearly identical to GDC's BAMs.

[link]: https://github.com/ccwang002/cptac3-gbm-analysis/tree/master/201908_gene_quantification


Commands:

    conda activate cptac_expression
    parallel -j4 --bar \
        python /diskmnt/Projects/cptac_scratch/CPTAC_expression/pipeline_workflow/gen_fpkm.py \
        /diskmnt/Datasets/Reference/GDC/gencode.gene.info.v22.tsv \
        '{}' \
        'readcount_and_fpkm/{/}' \
        ::: washu_bam_featurecounts_output/*.tsv.gz
