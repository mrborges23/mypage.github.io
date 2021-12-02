## Tutorial 1
## Selecting models of nucleotide sequence evolution

In this tutorial, we will determine the best fitting model of a set of mitochondrial sequences taken from Brown, Prager, Wang, and Wilson (1982). The study is entitled *Mitochondrial DNA sequences of primates: tempo and mode of evolution* and was published in the *Journal of Molecular Evolution* 18 (4): 225-239. 

* Sequence alignment: [&#8600;brown.fas](/assets/lectures/brown.fas)
* Phylogeny: [&#8600;brown.nwk](/assets/lectures/brown.nwk)
* Control file: [&#8600;baseml.ctl](/assets/lectures/baseml.ctl)

We will use `BASEML` (part of the `PAML` package by Ziheng Yang) because it requires a good understanding of the procedure involved in hypotheses testing. Additionally, this tutorial introduces you to a general procedure that is used in the `PAML` package to test many other evolutionary hypotheses in a similar fashion.

`BASEML` operates differently from the other programs you have experienced so far. Rather than specifying the options with which the program should be executed through an interactive menu, these options are specified in a so-called control file. Please have at hand the baseml control file, the tree and the alignment file.

The control file specifies, amongst other things, parameters describing:
* the name of the sequence input file;
* the name of the file containing one or more phylogenetic trees for the data set under investigation;
* the name of the output file where the results of the computation will be written
* other control variables are used to choose among different types of analysis

To set the name of the alignment file and tree file needed by the analysis you would include the following two lines in the control file:
```
seqfile  = brown.nuc    * name of sequence data file
treefile = tree.nwk     * name of tree structure file
```

For hypothesis using `BASEML`, you will need to execute the program several times. For example the first time, you will run the analysis using a JC model, the second time, you will run the analysis using a K2P model. To run the`BASEML` program, type `./baseml` at the command line (UNIX). You will then need to examine the output file to determine the log likelihood score of the tree under these models. 

Several models can be set by changing the `model` line.
```
model = 0 * 0:JC69, 1:K80, 2:F81, 3:F84, 4:HKY85
          * 5:T92, 6:TN93, 7:REV, 8:UNREST, 9:REVu; 10:UNRESTu
```
We will be testing the JC, K2P, F81, TN93, HKY85 and GTR models hierarchically. Notice that for the models F81, TN93, HKY85 and GTR the `nhomo` parameter has to be set to `1`.

Using `BASEML` you will need to calculate for yourself the difference in the likelihood statistic between the two models, which is twice the difference in log likelihoods as estimated under the two models, i.e., LRT=2(lnL1-lnL0). Significant likelihood ratios are obtained using a $\chi^2$ distribution where the degrees of freedom is 1 for the JC versus K2P comparison, where 1 is the difference in the number of parameters between the two models. A chi-square table can be found [here](https://people.smp.uq.edu.au/YoniNazarathy/stat_models_B_course_spring_07/distributions/chisqtab.pdf). 

What is the best fitting model telling us about the way the primate mitochondrial sequences evolve? Are the base frequencies equal? Is there a transition/transversion bias? Are all the transition rates equal?
