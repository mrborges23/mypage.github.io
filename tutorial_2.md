## Tutorial 2
## Bayesian phylogenetic inference

In this tutorial, we will perform phylogenetic analysis with the [Metzker et al. (2002)](https://www.pnas.org/content/99/22/14292) dataset, which includes HIV env/gp120 sequences. This data was used as evidence in a Louisiana gastroenterologist's trial accused of deliberately infecting someone (the victim) with HIV-infected blood from one of the gastroenterologist's patients. The jury was charged with addressing whether it was beyond a reasonable doubt that the victim was infected as a result of the gastroenterologist's actions.

In this exercise, we want to determine if there is evidence that the victim (whose sequences all begin with a V) was directly infected by blood taken from the patient (whose sequences all begin with a P). Therefore, the phylogenetic problem is to establish whether the virus samples in the victim and the patient were closely related. HIV-infected individuals from the local metropolitan area (tagged as LA) were also included as controls. Two more divergent reference sequences were also added: `M62320_HIVU455` and `K03454_HIVELI`. Notice that the sequences used in this tutorial are only a small subset (30 sequences) of the evidence they considered when trying to answer this question.

Sequence alignment: [&#8600;HIV_env_gp120.fas](/assets/lectures/HIV_env_gp120.fas)

We will be performing phylogenetic inference using the **MrBayes**, which is a software dedicated to reconstructing phylogenetic relationships (among other analyses) between molecular sequences using Bayesian inference. Reference to this method: Huelsenbeck and Ronquist *MRBAYES: Bayesian inference of phylogenetic trees* Bioinformatics, 17:754-755.

MrBayes can be executed by simply typing `mb` in the command line. The first thing to do is to upload the alignment file and setting the outgroup taxa. You can set the outgroup by either writting the sequence name (either `M62320_HIVU455` or `K03454_HIVELI`) or its position on the multiple sequence alignment. 

```
execute HIV_env_g120.nxs
outgroup 30
```

Next, we define the substitution model. We will use the GTR substitution model with site heterogeneity (following the results in the paper). The models of evolution available in MrBayes are defined under the option `nst` while the  gamma rates can be set in the `rates` option.

```
lset nst=6 rates=gamma
```

As we perform Bayesian inference, we will be running the MCMC algorithm. Please set the MCMC to run for 50 000 generations using two simultaneous, completely independent analyses. In proper phylogenetic analyses, one has to run **several runs** and *more generations*, so the posterior distribtuion is properly explored. Here, we run the MCMC with few runs and generations only to avoid taking too much of our humble cluster. The `samplefreq` is the frequency with which the MCMC samples will be written to file: set it 100. Considering that we run 50000 generations and sample evey 100th, how many samples of the posterior will we have sampled by the end of the MCMC run?

```
mcmc ngen=50000 nruns=2 samplefreq=100
```

After the MCMC is finished, we need to summarize the posterior distribution: the sampled parameters and trees are respectively kept in the `.log` and `tree` files. For this we need to run the `sump` and `sumt` commands, which summarize the parameters and trees that have been visited by the MCMC. Remember that MCMC samples are only representative of the posterior distribution if they are converging. Therefore, we should discard some of the initial iterates that represen the burn-in phase. Read the `.log` output file Using [Tracer](https://beast.community/tracer), plot the trace plots for several parameter and determine an appropriate `burnin` parameter.

```
sump burnin=10
sumt burnin=10
```

Once these commands are run, the maximum a posterior tree is produced. You can open the resulting tree (`.con` file) in [Seaview](http://doua.prabi.fr/software/seaview). According to the Bayesian phylogeny, do we have evidence that the gastroenterologist deliberately infected the victim with HIV-infected blood from one of their patients? Support your conclusions using the obtained branch support values. 