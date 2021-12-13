## Tutorial 3
## Detecting positive selection in molecular sequences

In this tutorial, we will investigate the mammalian C7 protein, which is part of the complement immunity pathway, for signatures of positive selection. The data was taken from Kosiol, Vinar, da Fonseca, Hubisz, Bustamante, Nielsen, and Siepel (2008) entitled *Patterns of positive selection in six mammalian genomes*. To place the problem in context, you will test the mammalian C7 protein for positive selection by comparing the nearly neutral model M7 against the selection model M8.

Sequence alignment: [&#8600;C7.fas](/assets/lectures/C7.fas)<br/>
Phylogeny: [&#8600;C7.tree](/assets/lectures/C7.tree)

We will use **codeml**, a part of the **PAML** package. **codeml** includes several models of codon and protein evolution.

* Yang *PAML 4: phylogenetic analysis by maximum likelihood* Molecular Biology and Evolution 24 p1586-91 

`CODEML` operates similarly to `BASEML`. Rather than specifying the options with which the program should be executed through an interactive menu, these options are specified in a so-called control file.

This control file specifies, amongst other things, parameters describing:
* the name of the sequence input file;
* the name of the file containing one or more phylogenetic trees for the data set under investigation;
* the name of the output file where the results of the computation will be written
* other control variables are used to choose among different types of analysis

To set the name of the alignment file and tree file needed by the analysis you would include the following two lines in the control file:

```
seqfile  = C7.phy   * name of sequence data file
treefile = C7.tree  * name of tree structure file

```

To test the positive selection hypothesis using  `CODEML`, you will need to execute the program twice. The first time, you will run the analysis using a model with two classes of sites for purifying selection and neutral evolution (model 1). The second time, you will run the analysis using a selection model (model 2) with three classes of sites including the additional class of sites with positive selection. 

These models can be set using the `NSsites` line.

```
      NSsites = 1   * 0:one w;1:neutral;2:selection; 3:discrete;4:freqs;
                    * 5:gamma;6:2gamma;7:beta;8:beta&w;9:beta&gamma;
```

In the option `NS sites`, choose either `7: Beta` or `8: Beta and w`. You will have to run `codeml` twice to obtain the likelihood of each model. Alternatively, one could test for selection by using the pair `1: Neutral Model` and `2: Selection Model`. To run the `CODEML`  program, type `./codeml` at the command line. 

Is there any evidence for positive selection in the mammalian C7 proteins? If this is the case, what is the proportion of positively selected sites and the dN/dS ratio intensity?

