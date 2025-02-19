Clustering benchmark data: 13-dimensional data set from Levine et al. (2015)
============================================================================

This repository contains R code to prepare benchmark data set `Levine_13dim`, which can be used to test clustering algorithms.

The data set is a 13-dimensional mass cytometry (CyTOF) data set, consisting of protein expression levels for `n = 167,044` cells, `p = 13` protein markers (dimensions), and `k = 24` manually gated cell populations (clusters), from one individual. Cluster labels are available for 49% (81,747) of the cells.

This is a companion repository to [benchmark-data-Levine-32-dim](https://github.com/lmweber/benchmark-data-Levine-32-dim), which contains R code to prepare a similar benchmark data set with higher dimensionality (32 dimensions). For more details, including background information and additional details on the data sets, see the other repository.

The data set is sourced from the following paper:

- Levine et al. (2015). *Data-Driven Phenotypic Dissection of AML Reveals Progenitor-like Cells that Correlate with Prognosis.* Cell, 162, pp. 184-197. [http://www.sciencedirect.com/science/article/pii/S0092867415006376](http://www.sciencedirect.com/science/article/pii/S0092867415006376)

Raw data can be accessed through Cytobank:

- 32-dimensional benchmark data set: [https://www.cytobank.org/cytobank/experiments/46102](https://www.cytobank.org/cytobank/experiments/46102)
- 13-dimensional benchmark data set: [https://www.cytobank.org/cytobank/experiments/46259](https://www.cytobank.org/cytobank/experiments/46259)

If you use these data sets, please reference the paper by Levine et al. (2015).




## Background

For background information on mass cytometry (CyTOF), and additional details on the Levine et al. (2015) paper and the benchmark data sets, see the other repository [benchmark-data-Levine-32-dim](https://github.com/lmweber/benchmark-data-Levine-32-dim).




## 13-dimensional benchmark data set

Levine et al. (2015) used two benchmark mass cytometry (CyTOF) data sets from healthy samples to demonstrate the performance of the PhenoGraph algorithm.

The 13-dimensional benchmark data set consists of protein expression levels from healthy human bone marrow mononuclear cells (BMMCs), from one healthy individual. (This data set is referred to as "benchmark data set 1" in Levine et al. 2015).

The data set contains `n = 167,044` cells, with a dimensionality of `p = 13` surface marker proteins. Manually gated cell population (cluster) labels are provided for `k = 24` major immune cell populations. Cluster labels are available for 49% (81,747) of the cells, with the remaining 51% (85,297) labeled as "unassigned". All cells are from a single individual.

The 13 surface markers are: CD45, CD45RA, CD19, CD11b, CD4, CD8, CD34, CD20, CD33, CD123, CD38, CD90, and CD3. All 13 surface markers were used for manual gating. An additional "DNA * cell length" gating step was also applied to remove platelets. See Levine et al. (2015), Supplemental Experimental Procedures, for more details.




## This repository

This repository contains an R script to pre-process and export the 13-dimensional benchmark data set in standard formats, in order to make it easier for researchers from other fields to access the data set to test clustering algorithms. This consists of the following steps:

- Load the FCS files
- Extract cell population names and protein marker names
- Extract cluster labels (one cluster per FCS file; "unassigned" cells are labeled "NA")
- Apply arcsinh transform (scale factor 5 for CyTOF data; see Bendall et al. 2011, Supplementary Figure S2)
- Export data in FCS and tab-delimited TXT format (separate files with/without arcsinh transform)

For more details, see the repository for the 32-dimensional benchmark data set [benchmark-data-Levine-32-dim](https://github.com/lmweber/benchmark-data-Levine-32-dim).




## Contents

The files in this repository are:

- [prepare_data_Levine_13dim.R](prepare_data_Levine_13dim.R): R script to load, pre-process, and export data files for the 13-dimensional benchmark data set ("Levine_13dim")

- [population_names_Levine_13dim.txt](data/population_names_Levine_13dim.txt): cell population names for each of the 24 manually gated populations

- FCS files in folder [data](data/): exported data files in FCS format
    - [Levine_13dim.fcs](data/Levine_13dim.fcs): main data file (transformed data, with cluster labels)
    - [Levine_13dim_notransform.fcs](data/Levine_13dim_notransform.fcs): without arcsinh transform

- TXT files in folder [data](data/): exported data files in tab-delimited TXT format. There are two files, with the same filenames and containing the same data as the FCS files described above. These files may be easier to access if you are unfamiliar with the FCS format.




## References and links

The benchmark data sets are sourced from the paper by Levine et al. (2015):

- Levine et al. (2015). *Data-Driven Phenotypic Dissection of AML Reveals Progenitor-like Cells that Correlate with Prognosis.* Cell, 162, pp. 184-197. [http://www.sciencedirect.com/science/article/pii/S0092867415006376](http://www.sciencedirect.com/science/article/pii/S0092867415006376)


Data from Levine et al. (2015) are publicly available through Cytobank at the following links. Note that a (free) Cytobank account is required.

- Project page (all data from Levine et al. 2015): [https://www.cytobank.org/cytobank/experiments?project=750](https://www.cytobank.org/cytobank/experiments?project=750)

- Experiment page for 32-dimensional benchmark data set: [https://www.cytobank.org/cytobank/experiments/46102](https://www.cytobank.org/cytobank/experiments/46102)

- Experiment page for 13-dimensional benchmark data set: [https://www.cytobank.org/cytobank/experiments/46259](https://www.cytobank.org/cytobank/experiments/46259)


Additional information can also be found on the Dana Pe'er lab web page, at: [http://www.c2b2.columbia.edu/danapeerlab/html/phenograph.html](http://www.c2b2.columbia.edu/danapeerlab/html/phenograph.html)


The 13-dimensional benchmark data set was originally published by Bendall et al. (2011):

- Bendall et al. (2011). *Single-cell mass cytometry of differential immune and drug responses across a human hematopoietic continuum.* Science, 332, pp. 687-696. [http://www.ncbi.nlm.nih.gov/pubmed/21551058](http://www.ncbi.nlm.nih.gov/pubmed/21551058) (data available through Cytobank at [http://reports.cytobank.org/1/v1](http://reports.cytobank.org/1/v1) or [https://www.cytobank.org/cytobank/experiments/6033/](https://www.cytobank.org/cytobank/experiments/6033/)).


