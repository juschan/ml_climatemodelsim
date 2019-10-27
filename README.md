# Climate Model Simulation Failure Prediction

### Goals

The goal of this project is to determine if the various variables used in a climate model simulation can be used to predict whether a particular simulation will crash.

### Dataset

The dataset can be found [here](https://archive.ics.uci.edu/ml/datasets/Climate+Model+Simulation+Crashes)

It is based out of climate model research by the Lawrence Livermore National Laboratory, Livermore 
and Department of Astronomy, Univesity of California, Berkeley. 18 parameters from the CCSM4 parallel ocean model are provided.

A reference paper from that research, "Failure analysis of parameter-induced simulation crashes in climate models" can be found [here](https://pdfs.semanticscholar.org/e29a/a9962e398308f5c1aee889912c130552ec05.pdf)
    
### Results

The data is unusual in that it used 'latin hypercubes' when sampling the input space. As such, the problems of collinearity is removed (if you are performing regression). The pairplot easily highlights the individual contributions. 

We use the following models:

* SVM (radial basis function)

* KBest + SVM (radial basis function)

* Bagging with SVM (linear function)

In comparing the "SVM", "KBest+SVM" and "Bagging with SVM", we observe from the confusion matrix that all models misclassified 11 cases (ie not necessarily the same cases), which resulted in the same weighted F1 score.

"KBest+SVM" is a more parsimonious model, where kbest identified the 'best' 4 features (which have been earlier identified in the pairplot). These were also mentioned in the reference paper. It also had the best ROC curve amongst the models (ie. largest AUC), which points to a better trade-off between true positive and false positive rate.