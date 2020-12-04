## Tutorial 4
## Detecting selection in molecular sequences

In this tutorial, we will investigate the mammalian C7 protein, which is part of the complement immunity pathway, for signatures of positive selection. The data was taken from Kosiol, Vinar, da Fonseca, Hubisz, Bustamante, Nielsen, and Siepel (2008) entitled *Patterns of positive selection in six mammalian genomes*. To place the problem in context, you will test the mammalian C7 protein for positive selection by comparing the nearly neutral model M7 against the selection model M8.

Sequence alignment: [&#8600;C7.fas](/assets/lectures/C7.fas)<br/>
Phylogeny: [&#8600;C7.tree](/assets/lectures/C7.tree)

We will use **codeml**, a part of the **PAML** package, through the [Phylemon 2](http://phylemon.bioinfo.cipf.es/?email=anonymous)  webserver. **codeml** includes several models of codon evolution; in this tutorial, we will be implementing site models to test for selection.

* Yang *PAML 4: phylogenetic analysis by maximum likelihood* Molecular Biology and Evolution 24 p1586-91 

1. In [Phylemon 2](http://phylemon.bioinfo.cipf.es/?email=anonymous), choose the bar `Evolutionary tests` and in the list of `Evolutionary test tools` select `Adaptation Tests`, then `PAML` and finally `CodeML`.

2. In the `codeml` input page, upload the mammalian C7 sequence alignment and tree. Alternatively, you can copy-paste the sequence alignment and trees into the respective text boxes.

3. Set the `Sequence type` to codons. In the `Model selection` section, set `Model` to `0: One omega for ALL branches`. This option specifies that we will be running a site model; `codeml` also allows for branch-specific tests of selection. In the option `NS sites`, choose either `7: Beta` or `8: Beta and w`. You will have to run `codeml` twice to obtain the likelihood of each model. Alternatively, one could test for selection by using the pair `1: Neutral Model` and `2: Selection Model`.

4. In `Other parameters`, set the `Number of categories for Gamma` to `4`, as we want to include site heterogeneity. Also, set the `Codon frequency `to `2: F3x4`. The `F3x4` option estimates individual nucleotide frequencies for the three codon positions. For example, the option `0: 1/61 each` assumes uniform codon frequencies (i.e., 1/61), which is typically not the case for real sequences (e.g., due to differential codon usage).

5. Give your job a name and press `Run`. On the lateral menu, you can check your analyses' progress; they are ready when your job name turns green. 

6. Once your job is finished, go to the `outfile` and press `view`. Alternatively, you could download this file and open it in a text reader software. The output file has information on the model likelihood and number of parameters (line starting with `lnL`). Use these values to perform a likelihood ratio test that compares the neutral model with the one with selection. Test the models using the [chi-square](https://people.smp.uq.edu.au/YoniNazarathy/stat_models_B_course_spring_07/distributions/chisqtab.pdf) distribution with degrees of freedom matching the difference in the number of parameters between the two models.

7. The estimated model parameter of the M7 and M8 models can be found near the `Parameters in M7` or `Parameters in M8` lines, respectively. These parameters defined the beta distribution of omega, including the proportion of sites under position selection.

Is there any evidence for positive selection in the mammalian C7 proteins? If this is the case, what is the proportion of positively selected sites and the dN/dS ratio intensity?
