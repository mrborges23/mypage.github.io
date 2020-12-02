## Tutorial 4
**Detecting selection in molecular sequences**

In this tutorial, we will investigate the mammalian C7 protein, which is part of the complement immunity pathway, for signatures of positive selection. The data was taken from Kosiol, Vinar, da Fonseca, Hubisz, Bustamante, Nielsen, and Siepel (2008) entitled *Patterns of positive selection in six mammalian genomes*. To place the problem in context, you will test the mammalian C7 protein for positive selection by comparing the nearly neutral model M1a against the selection model M2a.

Sequence alignment: [&#8600;C7.fas](/assets/lectures/C7.fas)<br/>
Phylogeny: [&#8600;C7.tree](/assets/lectures/C7.tree)

We will use **codeml**, which is a part of the **PAML** package, throught the [Phylemon 2](http://phylemon.bioinfo.cipf.es/?email=anonymous)  webserver. **codeml** includes several models of codon evolution; in this tutorial we will be implementing site models to test for selection.

Reference for PAML:
* Yang *PAML 4: phylogenetic analysis by maximum likelihood* Molecular Biolohy and Evolution 24 p1586-91 

1. In [Phylemon 2](http://phylemon.bioinfo.cipf.es/?email=anonymous), select the bar `Evolutionary tests`, in the list of evolutionary test tools select `Adaptation Tests`, then `PAML` and finally `Codeml`.

2. In the `codeml` page input the sequences and tree. You can upload these file, or simply copy past their content into the text boxes.


3. Set the `Sequence type` to codons. Regarding the model we will chose the option `0: One omega for ALL branches` and NS sites to `1: Neutral Model` or `2: Selection Model`. You will have to run `codeml` twice in order to obtain the likelihood of each model. Alternatively, one could test for selection by using the pair `7: Beta` and `8: Beta and w`.

4. In `Other parameters`, set the `Number of categories for Gamma` to `4`, as we want to include sites heterogeneity, and set the `Codon frequency `to `2: F3x4`. The `F3x4` option estimates individual nucleotide frequencies for the three codon positions. The option `0: 1/61 each` assumes uniform codon frequencies (i.e., 1/61) which is typically not the case for real sequences (e.g., due to codon differentiated usage).

5. Give your job an name and press `Run`. On the lateral menu, you can check the progress of your analyses; they are ready when the your job name turns green. 

6. Once your job is finished, go to the outfile and press `view`. Alternatively, you could download this file and open it in a text reader. The output file has information on the likelihood of the model and the corresponding number of parameters (line starting with `lnL`). Use these values to perform a likelihood ratio test that compares the neutral model with the one with selection. Test the models using the [chi-square](https://people.smp.uq.edu.au/YoniNazarathy/stat_models_B_course_spring_07/distributions/chisqtab.pdf) distribution with degrees of freedom matching the difference in the number of parameters between the two models.

7. The estimated parameters under the models M7 and M2 can be obtained near the `Parameters in M7` or `Parameters in M` lines, respectively. These parameters defined the beta distribution for the negatively selection and nearly neutral sites, plus the proportion of sites under position selection.


Is there any statitical evidence for positive selection in the mammalian C7 proteins? In that case, what is the intensity and frequency of positive selection in these sequences.
