# dsci-522_group-28
# Breast Cancer Predictor

  - author: Tiffany Timbers
  - contributors: Melissa Lee

Demo of a data analysis project for DSCI 522 (Data Science workflows); a
course in the Master of Data Science program at the University of
British Columbia.

## Introduction

For this project we are trying to answer the question: given tumour
image measurements is a newly discovered tumour benign or malignant?
Answering this question is important because traditional,
non-data-driven methods for tumour diagnosis are quite subjective and
can depend on the diagnosing physicians skill as well as experience
(Street, Wolberg, and Mangasarian 1993). Furthermore, benign tumours are
not normally dangerous; the cells stay in the same place and the tumour
stops growing before it gets very large. By contrast, in malignant
tumours, the cells invade the surrounding tissue and spread into nearby
organs where they can cause serious damage. Thus, it is important to
quickly and accurately diagnose the tumour type to guide patient
treatment.

The data set used in this project is of digitized breast cancer image
features created by Dr. William H. Wolberg, W. Nick Street, and Olvi L.
Mangasarian at the University of Wisconsin, Madison (Street, Wolberg,
and Mangasarian 1993). It was sourced from the UCI Machine Learning
Repository (Dua and Graff 2017) and can be found
[here](https://archive.ics.uci.edu/ml/datasets/Breast+Cancer+Wisconsin+\(Diagnostic\)),
specifically [this
file](http://mlr.cs.umass.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data).
Each row in the data set represents summary statistics from measurements
of an image of a tumour sample, including the diagnosis (benign or
malignant) and several other measurements (e.g., nucleus texture,
perimeter, area, etc.). Diagnosis for each image was conducted by
physicians.

To answer the predictive question posed above, we plan to build a
predictive classification model. Before building our model we will
partition the data into a training and test set (split 75%:25%) and
perform exploratory data analysis to assess whether there is a strong
class imbalance problem that we might need to address, as well as
explore whether there are any predictors whose distribution looks very
similar between the two classes, and thus we might omit from our
analyis. The class counts will be presented as a table and used to
inform whether we think there is a class imbalance problem. The
predictor distributions across classes will be plotted as facetted (by
predictor) ridge plots where the densities are coloured by class.

Given that all measurements are continous in nature, and the outcome we
are trying to predict is one of two classes, one suitable and simple
approach that we plan to first explore is using a k-nearest neighbours
classification algorithm. With this algorithm, we will have to choose K,
the number of nearest neighbours to use for prediction. We will choose K
via cross-validation using ~ 30 folds because this Wisconsin Breast
Cancer data set is not very large, having only 569 observations. We will
use overall accuracy to choose K. A line plot of overall accuracy versus
\(K\) will be included as part of the final report for this project.

After selecting our final model, we will re-fit the model on the entire
training data set, and then evaulate it’s performance on the test data
set. At this point we will look at overall accuracy as well as
misclassification errors (from the confusion matrix) to assess
prediction performance. These values will be reported as a table in the
final report.

Thus far we have performed some exploratory data analysis, and the
report for that can be found [here](src/breast_cancer_eda.md).

## Usage

To replicate the analysis, clone this GitHub repository, install the
[dependencies](#dependencies) listed below, and run the following
commands at the command line/terminal from the root directory of this
project:

    python src/download_data.py --out_type=feather --url=http://mlr.cs.umass.edu/ml/machine-learning-databases/breast-cancer-wisconsin/wdbc.data --out_file=data/raw/wdbc.feather
    Rscript -e "rmarkdown::render('src/breast_cancer_eda.Rmd')"

## Dependencies

  - Python 3.7.3 and Python packages:
      - docopt==0.6.2
      - requests==2.22.0
      - pandas==0.24.2
      - feather-format==0.4.0
  - R version 3.6.1 and R packages:
      - knitr==1.26
      - feather==0.3.5
      - tidyverse==1.2.1
      - caret==6.0-84
      - ggridges==0.5.1
      - ggthemes==4.2.0

## License

The Breast Cancer Predictor materials here are licensed under the
Creative Commons Attribution 2.5 Canada License (CC BY 2.5 CA). If
re-using/re-mixing please provide attribution and link to this webpage.

# References

<div id="refs" class="references">

<div id="ref-Dua2019">

Dua, Dheeru, and Casey Graff. 2017. “UCI Machine Learning Repository.”
University of California, Irvine, School of Information; Computer
Sciences. <http://archive.ics.uci.edu/ml>.

</div>

<div id="ref-Streetetal">

Street, W. Nick, W. H. Wolberg, and O. L. Mangasarian. 1993. “Nuclear
feature extraction for breast tumor diagnosis.” In *Biomedical Image
Processing and Biomedical Visualization*, edited by Raj S. Acharya and
Dmitry B. Goldgof, 1905:861–70. International Society for Optics;
Photonics; SPIE. <https://doi.org/10.1117/12.148698>.

</div>

</div>
