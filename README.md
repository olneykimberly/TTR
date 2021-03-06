# TTR
widespread TTR, Ttr expression in human and mouse data sets
### Parsing GTEx data to find samples with and without TTR expression
- Script: `parse_gtex.py`
1. Subset samples from the GTEx TPM count file:
- Example using liver where one specifies the samples to be subsetted via the config file
```
python scripts/parse_gtex.py --data rna --config GTEx_configs/Liver_config.json --gtex_file data/GTEx_Analysis_2017-06-05_v8_RNASeQCv1.1.9_gene_tpm_clean.gct --subset_samples_outfile Liver_counts.tsv
```
GTEx count files are located here: /data/CEM/shared/controlled_access/GTEX/version8/counts/GTEx_Analysis_2017-06-05_v8_RNASeQCv1.1.9_gene_tpm.gct.gz

- Instead of providing the samples to be subsetted via the config file, you can also provide a sample via `--sample` or a file with each sample on a row via `--samples_file`

2. For each tissue_counts.tsv, percentile rank (aka bin) the expression for each gene for each sample. Every gene will have a rank expression from 0-100. Zero being no expression, and 100 being the highest expressed genes for that sample. 

3. Subset the counts to get TTR TPM expression and TTR rank expression

4. Violin jitter plots showing rank values of TTR expression for each tissue. 
