## Assignment 1
## Fitting models of nucleotide sequence evolution


In this assignment, you will determine the best fitting model of evolution for the multiple sequence alignment assigned to you by employing a hierarchical likelihood ratio test (hLRT).

1. Test the following models JC, K80, F81, HKY, and GTR, and indicate the best fitting model. Please provide a table including the model likelihoods, number of parameters, model comparisons and corresponding degrees of freedom, the resulting LRT values, and critical value that you use to assess statistical significance. Perform the hLRT using a significance level of 0.05.

2. Based on the best fitting model obtained previously, do your sequences have a heterogeneous base composition? Is one exchangeability rate enough to describe the evolution of your sequences? Justify your answers.

3. Now that you know the best fitting model of evolution for your sequences, you will now test for the need for site heterogeneity. Again you will need to perform an LRT test; perform this LRT using a significance level of 0.05. To include the gamma rate in your analyses, open your `baseml.ctl` file, set the best fitting model, and change the options of `fix_alpha` and `ncatG` accordingly. You can use four gamma categories, which is typically a good approximation for the gamma distribution. Is there evidence for site heterogeneity? Based on the estimated value of alpha, is there evidence for strong or weak site rate heterogeneity over sites? Justify all your answers. 

Some notes:
* Partial grading will be given to answers that, despite being incorrect, show a good understanding of phylogenetic concepts and technical procedures. Thus, do not forget to justify all your answers and show the steps leading you to the final solution.
* Do not submit any output files that you will obtain by running the required software. Instead, validate your answers by summarizing the information contained in these files in the form of tables or plots. Translating complex information into sentences, tables, or plots is an important skill that will be evaluated in your answers.
* Every assignment should be appropriately identified using the following name: `RB_AssignmentNumber_YourStudentNumber`. Upload each assignment as an independent PDF file into the GCA cloud.