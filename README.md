# Ideological scaling of political text across different contexts with contextualized word embeddings
> Code repository for the corresponding master's thesis


## Installation

Make sure to have over 10 GB of disk space in your environment. This is not given with the default gesis-notebooks account.

Launch this repository in binder:
[![Binder](https://notebooks.gesis.org/binder/badge_logo.svg)](https://notebooks.gesis.org/binder/v2/gh/coded33/thesis_code/main)

or install it by creating an Anaconda environment:
> conda env create -f binder/environment.yml --name thesis

The necessary data we work with will be downloaded automatically by the notebooks that include the methods and work with that data.

## General Information

In total we have 10 jupyter-notebooks:
- 4 working with a **news articles dataset (NELA-GT-2018) by Horne et al.** (*Jeppe Nørregaard, Benjamin D. Horne, and Sibel Adalı.  Nela-gt-2018:A large multi-labelled news dataset for the study of misinformation in news articles. Proceedings of the International AAAI Conference on Web and Social Media, 13(01):630–638, Jul. 2019.*)
- 4 working with a **European Parliament speeches dataset (EuroParl) by Nanni et al. (improved version, see thesis)** (*Goran Glavaš, Federico Nanni, and Simone Paolo Ponzetto.  Computational analysis of political texts:  Bridging research efforts across communities.  In Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics: Tutorial Abstracts, pages 18–23, 2019.*)



Each notebook describes different approaches to the datasets. 

Excluding one notebook that aims at replicating the SemScale paper results (**europarl_paper_replication.ipynb**) and the two notebooks listed below, we all apply the same list of methods inside each notebook, *what differs is the part of the datasets we look at.*

These notebooks do not contain methods:
- **overview.ipynb**: A notebook providing an overview over the results
- **misc_plots.ipynb**: A notebook used to extract metrics and creating some of the plots for the thesis


## Repository Structure
In the root of the repository we have the notebooks and an **outlets.csv** file which is part of the NELA-GT-2018 dataset (it contains information about the news outlets which we access in the notebooks).
- __Folders__:
    - **SemScale-master**: Contains a clone of the SemScale repository (https://github.com/umanlp/SemScale)
    - **binder**: Contains an Anaconda *environment.yml* and a postBuild file for binder
    - **figs**: Contains all the figures produced by the methods inside the notebooks
    - **overview_img**: Contains images for the overview notebook (*overview.ipynb*)
    - **results**: Contains the metrics of the methods
    - **semscale_outputs**: Contains the outputs of SemScale, i.e. files which contain the scores of the individual documents. Because SemScale takes a long time to run, we provide these pre-computed results
    - **txts**: Contains just a .gitkeep. This folder will be filled with documents when running SemScale on one's own machine, in order to correctly match SemScale's scores with the respective documents
    
## Methods

Except for the three already mentioned notebooks (*overview.ipynb*, *misc_plots.ipynb*, and *europarl_paper_replication.ipynb*), all notebooks use all methods. Please note that if there exists normalized and unnormalized outputs of methods, we calculate both of them in the same notebook.

Following is a list of the methods in the same order as they are applied inside the notebooks:



- **Wordscores**
(*Michael Laver, Kenneth Benoit, and John Garry.  Extracting policy positions from political texts using words as data. American Political Science Review, 97(2):311–331, 2003.*)

- Wordscores (Normalized Output)


- **Wordfish (There only exists normalized output)**
(*Sven-Oliver Proksch and Jonathan B Slapin. Wordfish: Scaling software for estimating political positions from texts. Version, 1:323–344, 2008*)


- **SemScale (There only exists normalized output)**
(*Goran Glavaš, Federico Nanni, and Simone Paolo Ponzetto. Computational analysis of political texts: Bridging research efforts across communities.  In Proceedings of the 57th Annual Meeting of the Association for Computational Linguistics: Tutorial Abstracts, pages 18–23, 2019*)


- **BERT**
(*Jacob  Devlin,  Ming-Wei  Chang,  Kenton  Lee,  and  Kristina  Toutanova. BERT: Pre-training of deep bidirectional transformers for language understanding.  In Proceedings of the 2019 Conference of the North American Chapter of the Association for Computational Linguistics:  Human Language Technologies,  Volume  1  (Long  and  Short  Papers),  pages  4171–4186,  Minneapolis, Minnesota, June 2019. Association for Computational Linguistics.*)
- BERT (Normalized Output)


- **Linear Regression with Token Counts**

- Linear Regression with Token Counts (Normalized Output)


- **Feed Forward Neural Network with Token Counts**

- Feed Forward Neural Network with Token Counts (Normalized Output)



- **Linear Regression with Embeddings**

- Linear Regression with Embeddings (Normalized Output)



- **Feed Forward Neural Network with Embeddings**

- Feed Forward Neural Network with Embeddings (Normalized Output)

## The Notebooks

The error metrics are:
- **MSE**
- **Pearson correlation**
- **Spearman Correlation**

And they are used for every notebook.

### Working with the NELA-GT-2018 Dataset (Horne et al.)

The news articles dataset is analyzed in the following four notebooks:

- **horne_l_r.ipynb**: Far-left \& far-right articles 
    - *Methods*: All
    - *Error metrics*: All

- **horne_l_c_r.ipynb**: Far-left \& center \& far-right articles
    - *Methods*: All
    - *Error metrics*: All

- **horne_continous.ipynb**: Far-left \& left \& center \& right \& far-right articles 
    - *Methods*: All
    - *Error metrics*: All

- **horne_random.ipynb**: Randomly generated articles (randomly concatenated words from far-left & far-right articles with random far-left or far-right labels)
    - *Methods*: All
    - *Error metrics*: All


### Working with the EuroParl Dataset (Nanni et al.)
The European Parliament speeches dataset is analyzed in the following four notebooks:

- **europarl_fifth.ipynb**: 5th legislation speeches
    - *Methods*: All
    - *Error metrics*: All

- **europarl_sixth.ipynb**: 6th legislation speeches
    - *Methods*: All
    - *Error metrics*: All

- **europarl_combined.ipynb**: 5th \& 6th legislation combined speeches
    - *Methods*: All
    - *Error metrics*: All

- **europarl_paper_replication.ipynb**:  Recreation of the SemScale paper results by Nanni et al.
    - *Methods*: Wordfish, Semscale
    - *Error metrics*: All
    

### Other Notebooks
- **overview.ipynb** is an overview notebook which gives a brief introduction to some of the essential results of this thesis

- **misc_plots.ipynb** is a notebook used to extract metrics and creating some of the plots for the thesis


## Tips
- Having a good GPU is highly recommended. Especially training BERT models on CPU is possibly a matter of days and using the pre-trained models is still a matter of some hours. With a GPU it is only a matter of a few minutes

- If you run out of memory using BERT, decrease the value for *train_batch_size* in the cell for BERT

- Unless having a very, very powerful system, we do not recommend to run two Horne/NELA-GT-notebooks in parallel. It however works well running the EuroParl notebooks in parallel as there is a lot less data
