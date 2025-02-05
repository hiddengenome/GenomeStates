# GenomeNet-responseViewer <img src="www/Logo.png" width="131px" height="140px" align="right" style="padding-left:10px;background-color:white;" />

## Introduction

GenomeNet-responseViewer is an open-source interactive web app for visualising hidden states of LSTM networks trained on genomical dataset such as bacteria. The goal of the GenomeNet-responseViewer is to screen hidden states for unkown but common structural properties. The hidden states behind GenomeNet-responseViewer are generated by the R library [deepG](https://github.com/hiddengenome/deepG). In [deepG](https://github.com/hiddengenome/deepG) a [minimal version](https://github.com/hiddengenome/GenomeNet-responseViewer/tree/minimal_viewer) of the Response Viewer is implemented.

## Installation

The R library [deepG](https://github.com/hiddengenome/deepG) with the minimal version from the [branch](https://github.com/hiddengenome/GenomeNet-responseViewer/tree/minimal_viewer) needs to be installed as it provides the main function of hidden states extraction. To install [deepG](https://github.com/hiddengenome/deepG) use (for more information see the [Wiki](https://github.com/hiddengenome/deepG/wiki)):

```bash
devtools::install_github("hiddengenome/deepG")
```

For the installation of the complete GenomeNet-responseViewer with correlation and examples download the Zip-File and extract the files (In the future, the full functionality will also be available in [deepG](https://github.com/hiddengenome/deepG)). Choose the directory and enter:  

```bash
source("app.R")
```

## Running GenomeNet-responseViewer

```bash
visualizePrediction()
```

## Examples

There are three examples available: The hidden states to "Bacteroides fragilis_CRISPR_example" are calculated with the newest model on CPU. The position of the repeats are colored in grey and you can zoom in and out the graphic.

**CRISPR Sample from Bacteroides fragilis** from [CRISPRs Database](https://crispr.i2bc.paris-saclay.fr/crispr/)
![Web app](www/CRISPR_example.png)

![Web app](www/figure1.png)
![Web app](www/figure2.png)

**CRISPR Sample from Lactobacillus acidophilus** from [CRISPRs Database](https://crispr.i2bc.paris-saclay.fr/crispr/)
![Web app](www/Lacto_CRISPR_example.png)

![Web app](www/figure3.png)

### Usage

To use a fasta files use the `fasta.path` and to load generated states with the package [deepG](https://github.com/hiddengenome/deepG) use `states.path` and put `states` to TRUE. You can also calculated the hidden states with your own genomic examples with `sample`.

```bash
### The GenomeNet-responseviewer in deepG:

library(deepG)
# Example for own sequence
visualizePrediction(sample = "Your Genomsequence", model.path = model.path, vocabulary = vocabulary)

# To load states written with writeStatesToH5() or writeStatesByFastaEntries() in .h5
visualizePrediction(states.path = states.path, states = TRUE)

# To use fasta files
visualizePrediction(fasta.path = fasta.path, model.path = model.path , vocabulary = vocabulary)
```
```bash
### The complete GenomeNet-responeviewer:

visualizePrediction(sample = strrep("ATGCGTACGTCAGTA", 100), model.path = "data/models/cpu_model.hdf5", vocabulary = c("l","a","g","c","t"), cell_number = 6, start_position = 300, end_position = 900)
```
![Web app](www/figure4.png)

## License and Copyright
Copyright 2020 Philipp Münch
