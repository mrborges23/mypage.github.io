## Tutorial 4
## Testing the molecular clock hypothesis

In this tutorial, we will test the molecular clock hypothesis in a set of concatenated mitochondrial proteins. To place the problem in context, you will test the clock behavior of these sequences by comparing the clock model against the non-clock model.

* Sequence alignment: [&#8600;cmp.phy](/assets/lectures/cmp.phy)
* Unrooted phylogeny: [&#8600;cmp.tree](/assets/lectures/cmp.tree)
* Control file: [&#8600;codeml.ctl](/assets/lectures/codeml2.ctl)

We will use **codeml**, a part of the **PAML** package. **codeml** includes several models of codon and protein evolution; in this tutorial, we will be implementing site models to test the molecular clock hypothesis and estimate divergence times.

* Yang *PAML 4: phylogenetic analysis by maximum likelihood* Molecular Biology and Evolution 24 p1586-91 

In `CODEML`, rather than specifying the options with which the program should be executed through an interactive menu, these options are specified in a so-called control file.

This control file specifies, amongst other things, parameters describing:
* the name of the sequence input file;
* the name of the file containing one or more phylogenetic trees for the data set under investigation;
* the name of the output file where the results of the computation will be written
* other control variables are used to choose among different types of analysis

To test the clock hypothesis using `CODEML`, you will need to execute the program twice. The first time, you will run the analysis using a model where all branches in the tree are allowed to evolve at different rates (i.e., the model that assumes no clock). The second time, you will run the analysis using the global clock model, where all the branches in the tree evolve at the same rate. These two models can be set using the `clock` option in the control file.

```
clock = 0 * 0: no clock, unrooted tree, 1: clock, rooted tree
```

To test the molecular clock hypothesis, we need a rooted and unrooted tree. Note that an unrooted tree is provided `((((Human,Gorilla),Orangutan),Monkey),(Horse,(Whale,Cow)),(Dog,Bear));`. 

To test the clock model, we have to input a rooted tree. Considering the evolution of mammals, how should we root the previous phylogeny? 

We will be using an empirical model of evolution. First make sure `seqtype` is set for amino acids, then set an empirical amino acid model within `model` (you can find this option within the list of amino acid models). Finally, choose an appropriate empirical matrix in `aaRatefile`. Which rate matrix shoud we choose for these mitochondrial proteins?

Using `CODEML` you will need to calculate for yourself the difference in the likelihood statistic between the two models, which is twice the difference in log likelihoods as estimated under the two models, i.e., LRT=2(lnL1-lnL0). Significant likelihood ratios are obtained using a chi-square distribution where the degrees of freedom are the difference in the number of parameters between the two models. A chi-square table can be found [here](https://people.smp.uq.edu.au/YoniNazarathy/stat_models_B_course_spring_07/distributions/chisqtab.pdf).

Is there any evidence that the mammalian mitochondrial genes evolve according to the molecular clock? 

According to the clock model, what is the amino acid substitution rate is per MY? What is the age of the Carnivora divergence? Can you trust these values? Why? To answer this question, use a calibration point at 8.60 million years (MY) for the human–gorilla common ancestor, which corresponds to their median divergence (taken from [TimeTree](http://www.timetree.org/)). 