## Tutorial 2
**Maximum likelihood and Bayesian phylogenetic inference**

In this tutorial, we will investigate the mammalian C7 protein, which is part of the complement immunity pathway, for signatures of positive selection. The data was taken from Kosiol, Vinar, da Fonseca, Hubisz, Bustamante, Nielsen and Siepel (2008) entitled *Patterns of positive selection in six mammalian genomes*. To place the problem in context, you will test the mamalian C7 protein for positive selection by comparing the nearly neutral model M1a against the selection model M2a.

Sequence alignment: [&#8600;HIV_env_gp120.fas](/assets/lectures/HIV_env_gp120.fas)
Phylogeny: 

We will use \texttt{CODEML} (part of the  \texttt{PAML} package) because it requires a good understanding of the procedure involved in the hypothesis test. Additionally, this introduces you to a general procedure that is used by \texttt{CODEML}  (and other software in the  \texttt{PAML} package) to test many other evolutionary hypotheses in a similar fashion.


1. This control file specifies, amongst other things, parameters describing:
\begin{itemize}
\item the name of the sequence input file;
\item the name of the file containing one or more phylogenetic trees for the data set under investigation;
\item the name of the output file where the results of the computation will be written
\item other control variables are used to choose among different types of analysis
\end{itemize}

To set the name of the alignment file and tree file needed by the analysis you would include the following two lines in the control file:

\begin{verbatim}
seqfile  = C7.phy   * name of sequence data file
treefile = C7.tree  * name of tree structure file
\end{verbatim}

2. To test the positive selection hypothesis using `codeml`, you will need to execute the program twice. The first time, you will run the analysis using a model with two classes of sites for purifying selection and neutral evolution (model M1a). The second time, you will run the analysis using a selection model (model M2a) with three classes of sites including the additional class of sites with positive selection. 

These models can be set using the \texttt{NSsites} line.

\begin{verbatim}
      NSsites = 1   * 0:one w;1:neutral;2:selection; 3:discrete;4:freqs;
                    * 5:gamma;6:2gamma;7:beta;8:beta&w;9:beta&gamma;
\end{verbatim}



3. Note that the number of free parameters for the M1a (nearly neutral) model is 3 and while that of the M2a (positive selection) model is 5. 

