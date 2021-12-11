## Assignment 2
## Inferring Bayesian trees


In this assignment, you will infer the Bayesian tree for your sequences.

1. You will have to select one of the sequences in your multiple sequence alignment to serve as an outgroup for the Bayesian tree inference. Indicate and explain your choice.

2. Set the model of evolution that you have obtained in the last task into MrBayes. Justify your options for the `nst` and `rates`. Remember that you obtain more information about the available models and rates by typig `help lset` on the MrBayes terminal. Run your MCMC by setting two runs and 100 000 generations. Use a sample frequency `samplefreq` that will allow you to sample 1000 generations, and to summarise the runs with `sump` and `sumt`, set a `burnin` that discards 20% of the initial samples. Justify your choices for the `samplefreq` and `burnin`.

2. We now assess convergence. Analyze your MCMC `.run1.p` and `.run2.p` output files using Tracer. We will focus only on two parameters: the base composition of A and the exchangeability AC. According to their trace plots, are the two runs reaching a plateau, and are the two runs converging to the same regions? Complement your visual analyses of the trace plots with the ESS value: is it acceptable? Justify. According to your convergence analysis, do you think you need to run your MCMC for an additional number of generations, or the current samples are enough to summarize the posterior? 

3. We had discarded 20% of the samples when we summarized the model parameters. Based again on the trace plots of the base composition of A and the exchangeability AC, do you think that a 20% burn-in was an appropriate choice or too conservative/relaxed? Justify your answer.

4. What is the posterior clade probability of the great ape's clade? Is it well or poorly supported? Justify your answer by plotting the Bayesian tree with the respective support values. Indicate clearly which support values you are referring to.

Some notes:
* Partial grading will be given to answers that, despite being incorrect, show a good understanding of phylogenetic concepts and technical procedures. Thus, do not forget to justify all your answers and show the steps leading you to the final solution.
* Do not submit any output files that you will obtain by running the required software. Instead, validate your answers by summarizing the information contained in these files in the form of tables or plots. Translating complex information into sentences, tables, or plots is an important skill that will be evaluated in your answers.
* Every assignment should be appropriately identified using the following name: `RB_AssignmentNumber_YourStudentNumber`. Upload each assignment as an independent PDF file into my vetcloud (link sent by email).