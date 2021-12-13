

## Tutorial 4
## Testing the molecular clock hypothesis

In this tutorial, we will test the molecular clock hypothesis in a set of concatenated mitochondrial proteins. To place the problem in context, you will test the clock behavior of these sequences by comparing the clock model against the non-clock model.

Sequence alignment: [&#8600;cmp.phy](/assets/lectures/cmp.phy)<br/>
Unrooted phylogeny: [&#8600;cmp.tree](/assets/lectures/cmp.tree)

We will use **codeml**, a part of the **PAML** package. **codeml** includes several models of codon and protein evolution; in this tutorial, we will be implementing site models to test the molecular clock hypothesis and estimate divergence times.

* Yang *PAML 4: phylogenetic analysis by maximum likelihood* Molecular Biology and Evolution 24 p1586-91 

`CODEML` operates similarly to `BASEML`. Rather than specifying the options with which the program should be executed through an interactive menu, these options are specified in a so-called control file.

This control file specifies, amongst other things, parameters describing:
* the name of the sequence input file;
* the name of the file containing one or more phylogenetic trees for the data set under investigation;
* the name of the output file where the results of the computation will be written
* other control variables are used to choose among different types of analysis

To test the molecular clock hypothesis, we need a rooted and unrooted tree. Note that an unrooted tree is provided `((((Human,Gorilla),Orangutan),Monkey),(Horse,(Whale,Cow)),(Dog,Bear));`. 

To test the clock hypothesis using `CODEML`, you will need to execute the program twice. The first time, you will run the analysis using a model where all branches in the tree are allowed to evolve at different rates (i.e. the model that assumes no clock). The second time, you will run the analysis using the global clock model, where all the branches in the tree evolve at the same rate. These two models can be set using the `clock` option in the control file.

```
clock = 0 * 0: no clock, unrooted tree, 1: clock, rooted tree
```

To test the clock model, we have to input a rooted tree. Considering the evolution of mammals, how should we root the previous phylogeny? In addition to rooting the tree, we will perform time divergence estimation by calibrating the molecular clock. We will use a calibration point at 8.60 million years (MY) for the human–gorilla common ancestor, which corresponds to their median divergence (taken from [TimeTree](http://www.timetree.org/)). Because `codeml` only accepts calibration dates within the range of 0.00001-10, we will set the date at 0.0086 (i.e., in units of 10^3 MY). The calibration can be done by placing `'@0.0086'` at the relevant node in the inputted newick tree. Note that multiple calibration points can be specified in this way.


We will be using an empirical model of evolution. 

e to aminoacids. In the `Model selection` section, set `Model` to `2: Empirical` (you can find this option within the list of amino acid models). When this option is selected, a new option `aaRatefile` appears in the `Sequence related parameters` field. Select the option `mtmam.dat`, which corresponds to the MtMam empirical amino acid model of evolution.

5. In the option `Clock` (inside the `Other parameters` field) choose either `0: No clock` or `1: Clock`. You will have to run `codeml` twice to obtain the likelihood of each model. Do not forget that the calibrated rooted tree should be used for estimating the likelihood of the clock hypothesis, while its unrooted version should be used with the non-clock model.


7. Once your job is finished, go to the `outfile` and press `view`. Alternatively, you could download this file and open it in a text reader software. The output file has information on the model likelihood and number of parameters (line starting with `lnL`). Use these values to perform a likelihood ratio test that compares the neutral model with the one with selection. Test the models using the [chi-square](https://people.smp.uq.edu.au/YoniNazarathy/
stat_models_B_course_spring_07/distributions/chisqtab.pdf) distribution with degrees of freedom matching the difference in the number of parameters between the two models.

8. Two important parameters estimated under the clock model are the substitution rate and the time tree; both can be found at the end of the output file. 

Is there any evidence that the mammalian mitochondrial genes evolve according to the molecular clock? 

According to the clock model, what is the amino acid substitution rate is per MY? What is the age of the Carnivora divergence? Can you trust these values? Why? 
