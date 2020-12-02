## Tutorial 2
**Maximum likelihood and Bayesian phylogenetic inference**

In this tutorial, we will perform phylogenetic analysis with the [Metzker et al. (2002)](https://www.pnas.org/content/99/22/14292) dataset, which includes HIV env/gp120 sequences. This data was used as evidence in a Louisiana gastroenterologist's trial accused of deliberately infecting someone (the victim) with HIV-infected blood from one of the gastroenterologist's patients. The jury was charged with addressing whether it was beyond a reasonable doubt that the victim was infected as a result of the gastroenterologist's actions.

In this exercise, we want to determine if there is evidence that the victim (whose sequences all begin with a V) was directly infected by blood taken from the patient (whose sequences all begin with a P). Therefore, the phylogenetic problem is to establish whether the virus samples in the victim and the patient were closely related. HIV-infected individuals from the local metropolitan area (tagged as LA) were also included as controls. Two more divergent reference sequences were also added: `M62320_HIVU455` and `K03454_HIVELI`. Notice that the sequences used in this tutorial are only a small subset (30 sequences) of the evidence they considered when trying to answer this question.

Sequence alignment: [&#8600;HIV_env_gp120.fas](/assets/lectures/HIV_env_gp120.fas)

We will be performing phylogenetic inference using the [NGPhylogeny](https://ngphylogeny.fr/) webserver, which is dedicated to reconstructing and analyzing phylogenetic relationships between molecular sequences. It included the software used for maximum likelihood (**PhyML**) and Bayesian (**MrBayes**) phylogenetic inference.

References for these methods:
* Guindon, Dufayard, Lefort, Anisimova, Hordijk, and Gascuel *New Algorithms and Methods to Estimate Maximum-Likelihood Phylogenies: Assessing the Performance of PhyML 3.0* Systematic Biology, 59:307–321
* Huelsenbeck and Ronquist *MRBAYES: Bayesian inference of phylogenetic trees* Bioinformatics, 17:754-755


**Maximum likelihood tree**

1. In the [NGPhylogeny](https://ngphylogeny.fr/) webserver go to the `Tools` bar and select the `PhyML` method of tree inference.

2. Upload the sequence alignment in `alignment file` and set `Data type` to `Nucleic acids`.

3. We want to set a GTR substitution model with site heterogeneity. Make the appropriate options in the `Evolutionary model` section. Set up the gamma model using the options `Number of categories for the discrete gamma model` and `Parameter of the gamma model`.

4. Regarding the `Tree topology search`, you can leave the default option: i.e., SPR (Subtree Pruning and Regraphing). Like the NNI (Nearest Neighbor Interchange), the SPR is another tree rearrangement method.

5. In the `Statistical test for branch support` choose the `Bootstrap` option and set it to 10 bootstraps. Typically, one should use around 100 bootstraps, but we will use a smaller number to avoid taking too much of the webserver's load. There are alternative methods of branch support that are faster than bootstrapping. SH-like is one of such methods. Strongly supported clades show SH-like values closer to 1.0.

6. Press `Submit`. You will be redirected to a webpage where you can see the progression of the run. Wait until all the steps are concluded.

7. Once the analyses are finished, open the `PhyML Newick tree` using the `iTol` viewer. You can alternatively download the Newick file to your computer and open it in `Seaview`. In `iTol` go to the `Advanced` bar and display the bootstraps. By default, bootstraps are represented graphically, but we want to see the actual bootstraps values. For that, choose the option `text` instead.

According to the maximum likelihood phylogeny, do we have evidence that the gastroenterologist deliberately infected the victim with HIV-infected blood from one of their patients? Support your conclusions using the obtained branch support values.


**Bayesian tree**

1. In the [NGPhylogeny webserver](https://ngphylogeny.fr/) go to the `Tools` bar and select the `MrBayes` method of tree inference.

2. Upload the sequence alignment in `input file`.

3. As we perform Bayesian inference, we will be using the MCMC algorithm. Please set the MCMC to run for 50 000 generations using a single chain. In proper phylogenetic analyses, one has to run several chains, so the posterior space is properly explored. Here, we set the MCMC to one chain is to avoid taking too much of the webserver's load. 

4. Set the outgroup to one of the sequences: `M62320_HIVU455` or `K03454_HIVELI`.

5. Regarding the model of evolution, we will use the GTR substitution model with site heterogeneity. The gamma model can be set in the `Choose rates` option.

6. Within the Bayesian inference, the samples of the posterior are summarized. MrBayes included several parameters that do that for us. The `sample frequency` is the frequency with which the MCMC samples will be written to file: set it 50. How many samples will we have at the end of the MCMC run? The `burn-in fraction` corresponds to the fraction of MCMC samples that will be discarded from summarization: set it to 0.25. Regarding the summarize parameters, leave them all `true`.

7. Press `Submit`. You will be redirected to a webpage where you can see the progression of the run. Wait until all the steps are concluded.

8. Once the analyses are finished, open the `Mr Bayes Consensus tree` using the `iTol` viewer. You can alternatively download the Newick file to your computer and open it in `Seaview`. In `iTol` go to the `Advanced` bar and display the bootstraps. By default, bootstraps are represented graphically, but we want to see the actual bootstraps values. For that, choose the option `text` instead.

9. Download the file `Mr Bayes All Runs Outputs`, where you can find the `align.nx.p` and the `align.nx.t` outputs. These include the MCMC sampled parameters (exchangeabilities and base composition) and trees, respectively. Open the first file in a spreadsheet and analyze the convergence of the MCMC chains for some of the parameters via scatter plots. Was 0.25 a good choice for a burn-in fraction?

According to the Bayesian phylogeny, do we have evidence that the gastroenterologist deliberately infected the victim with HIV-infected blood from one of their patients? Support your conclusions using the obtained branch support values. 

A more general question: are the Bayesian and maximum likelihood trees considerably different in terms of topology and branch support values?
