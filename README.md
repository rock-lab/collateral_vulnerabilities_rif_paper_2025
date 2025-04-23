# collateral_vulnerabilities_rif_paper_2025
Repository containing the code and methods for Eckartt et al. 2025

## Code 
Below is a short legend describing the main files, followed by examples running the code:

#### vulnerability_modeling_tools.R
R code with functions useful for running the vulnerability analysis.

#### vulnerability_plotting_tools.R
R code with functions useful for plotting vulnerability results

#### gene_vulnerability_analysis.R
R code for running vulnerability analysis.

#### model_negbinom_2line_logistic_w_guide_lambda_betamin_zero.stan
Stan code for the vulnerability model.

#### gene_vulnerability_plots.R
R code for creating plots of vulnerability results in parallel.



#### process_reads.py
Python code to process fastq files with reads

#### subread\.py
Tools useful to interact with the subread aligner. Must install via your OS package manager (e.g. sudo apt install subread)

#### counting_tools.py
Tools useful for counting the aligned reads


## Data

Included in the repository is two, small example files that can be used to test running the code.


## Example
Examples to show how to to run the code.

### Analysis
To run the actual analysis with example parameters simply run:

`Rscript gene_vulnerability_analysis.R --data <COUNTPATH> --strain <STRAIN> --label <LABEL>  --output <RESULTSPATH> --cores <WORKERS>`

where:

- COUNTPATH is a path to a dataframe containing counts for each of the sgRNAs at different passages.
- STRAIN is the strain being analyzed, which use used when distinguishing results.
- LABEL is general label to distinguish results
- RESULTSPATH is a path were you want results to be stored
- WORKERS is the number of workers to be used when running in parallel.

For example:

`Rscript gene_vulnerability_analysis.R --data data/example_counts_H37Rv_biotinRR.txt --strain H37Rv --label biotinRR  --output ./results/ --cores 20`


This will create a local folder "results", which will have two sub-folders containing the data passed to the model ("./results/model_data/"), and the samples obtained from the model (./results/model_data/).


### Plotting

Similarly, users can create plots of the results by running the following command:

`Rscript gene_vulnerability_plots.R --data <DATAPATH> --strain <STRAIN> --exp <EXP> --date <DATE> --label <LABEL> --plot_dir <PLOTDIR> --dir <RESULTSPATH> --cores <WORKERS>`

where:

- COUNTPATH is a path to a dataframe containing counts for each of the sgRNAs at different passages.
- STRAIN is the strain being analyzed, which use used when distinguishing results.
- EXP is a label for the experiment being analyzed, which use used when distinguishing results.
- DATE is a date for the experiment being analyzed, which use used when distinguishing results.
- LABEL is general label to distinguish results
- RESULTSPATH is a path where the results from the vulnerability analysis were stored.
- PLOTDIR is a path where you want plots to be outputed to.
- WORKERS is the number of workers to be used when running in parallel.


`Rscript gene_vulnerability_plots.R --data data/example_counts_H37Rv_biotinRR.txt --strain H37Rv --label biotinRR  --dir ./results/ --cores 20 --exp biotinRR --date 08_10_2023 --plot_dir ./results/plots/`


