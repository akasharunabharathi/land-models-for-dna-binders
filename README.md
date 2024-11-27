# CS 582 – ML for Bioinformatics
## Project Proposal – An Language-Modeling Approach to Design of DNA-binding Proteins

Names: Akash Arunabharathi, James Fang, Matthew Handzel

### Motivation
Genetic engineering induces permanent changes in an organism that do not adapt to changes in the environment, and additionally, faces significant regulatory hurdles. Instead, we propose to design and leverage de novo DNA-binding proteins (such as transcription factors) to regulate gene expression to enable finer, dynamic control of phenotypes. As such, developing de novo DNA-binding proteins that can target specific genes can have a significant impact in healthcare, agriculture, and other such fields.

### Problem Definition
There are several challenges with respect to design of DNA-binding proteins – mapping the structural couplings between DNA and proteins remains challenging, for example (Computational Design of DNA binders, Cameron J. G. et al 2023).
Here, we propose an inverse approach to investigating the feasibility of generating DNA-binding proteins. We propose leveraging two models: fine-tuning ESM2 to generate DNA-binding proteins using data from JASPAR, Transfac, and DNAproDB, and a second model that learns the mapping from DNA-binding protein to the corresponding sequence. 
Using these two models, we propose to investigate what DNA sequences the de novo DNA-binding proteins will bind to, and examine whether these DNA sequences are naturally occurring.

### Method
As outlined above, our intended method involves:
1. Fine-tuning ESM2 with protein binders to generate DNA-binding protein sequences

2.

  a. Training a second seq-to-seq model that predicts the DNA sequence (y) that a DNA-binding protein binds to (x)
  
  b. Alternatively, instead of training a model to predict the sequences we bind to, what we can do is do MSA on our de novo proteins, and do homology analysis using MSA.

3. Investigate the structure of these de novo proteins using AlphaFold 2, and also investigate whether these DNA sequences are naturally occurring using tools such as BLAST

  a. BLAST is api
  
  b. Alphafold2 can be used as a Colab Notebook through ColabFold (AlphaFold3 can also be used now)
  
  c. https://colab.research.google.com/github/sokrypton/ColabFold/blob/main/AlphaFold2.ipynb#scrollTo=mbaIO9pWjaN0 

4. Compute DNA binding affinity, interaction using AlphaFold 3

  a. AlphaFold3 Webserver
  
  b. Computational design of DNA binders paper
  
  c. Geometric deep learning of protein–DNA binding specificity paper

5. Determine the viability of a language-modeling approach to generating DNA-binding proteins that does not explicitly account for structural challenges.

  a. Interpretation of the results.

### Related Work
Computational Design of DNA binders, Cameron J. G. et al 2023
Mitra, R., Li, J., Sagendorf, J.M. et al. Geometric deep learning of protein–DNA binding specificity. Nat Methods 21, 1674–1683 (2024). https://doi.org/10.1038/s41592-024-02372-w, https://github.com/timkartar/DeepPBS
Zrimec, J., Fu, X., Muhammad, A.S. et al. Controlling gene expression with deep generative design of regulatory DNA. Nat Commun 13, 5099 (2022). https://doi.org/10.1038/s41467-022-32818-8

Chapter Eight - Designing synthetic transcription factors: A structural perspective, Rossen Donev, Advances in Protein Chemistry and Structural Biology, publisher = Academic Press, vol. 130, 245-287, 2022,Protein Design and Structure

### Evaluation and Goals
To evaluate our protein design pipeline, we will use DeepPBS to evaluate the binding specificity of the generated transcription factors, in addition to metrics such as ipTM, PAE, etc. using AlphaFold 2 and AlphaFold 3.
