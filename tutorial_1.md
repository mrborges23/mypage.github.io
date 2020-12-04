## Tutorial 1
## Selecting models of nucleotide sequence evolution

In this tutorial, we will determine the best fitting model of a set of mitochondrial sequences taken from Brown, Prager, Wang, and Wilson (1982). The study is entitled *Mitochondrial DNA sequences of primates: tempo and mode of evolution* and was published in the *Journal of Molecular Evolution* 18 (4): 225-239. 

Sequence alignment: [&#8600;brown.fas](/assets/lectures/brown.fas)

We will use the [IQ-Tree](http://iqtree.cibiv.univie.ac.at/) webserver, and we will have to run it several times in order to obtain the log-likelihood for the tested models of evolution. We will be running the primate mitochondrial sequences with the JC, K2P, F81, TN93, HKY85, and GTR models. 

1. Go to your browser and open the [IQ-Tree webserver](http://iqtree.cibiv.univie.ac.at/).

2. In `Input data` upload your sequence alignment and set the `Sequence type` to DNA.

3. In `Substitution model options` select the model of evolution that you wish to test. We will be testing the JC, K2P, F81, TN93, HKY85, and GTR models. Notice that for the models F81, TN93, HKY85, and GTR, the `State frequency` has to be set to `ML-optimized`.

4. Recheck all your options and press `Submit job`. You will be automatically sent to the `Analysis results` page. You might need to wait a bit for the final results. When finished, your status bar should read `Success`. If you get the message `ERROR` please make sure you followed the previous steps correctly.

5. Once the runs are finished, look for the `Log-likelihood of the tree:` and `Number of free parameters` on the `Full Result` bar. Save those values for each model. We will be testing six models, so by the end of the exercise, you should have six log-likelihoods (with the corresponding number of parameters).

6. Perform a hierarchical likelihood ratio test and determine the best fitting model for these sequences. First, calculate the likelihood ratio test statistic for each mode comparison. This is twice the difference in log-likelihoods, i.e., LRT=2(lnL1-lnL0). Then, test the the models using the [chi-square](https://people.smp.uq.edu.au/YoniNazarathy/stat_models_B_course_spring_07/distributions/chisqtab.pdf) distribution with degrees of fredoom matching the difference in the number of parameters between the two models. 

What is the best fitting model telling us about the way the primate mitochondrial sequences evolve? Are the base frequencies equal? Is there a transition/transversion bias? Are all the transition rates equal?


# Molecular dating