MuSiC
===========
MuSiC: Identifying mutational significance in cancer genomes

Introduction
-----
The Mutational Significance In Cancer (MuSiC) consists of downstream analysis tools that can:

1.Apply statistical methods to identify significantly mutated genes<br>
2.Highlight significantly altered pathways<br>
3.Investigate the proximity of amino acid mutations in the same gene<br>
4.Search for gene-based or site-based correlations to mutations and relationships between mutations themselves<br>
5.Correlate mutations to clinical features, using typical correlation measures, and generalized linear models<br>
6.Cross-reference findings with relevant databases such as Pfam, COSMIC, and OMIM<br>
7.Generate typical visualizations like Kaplan-Meier survival estimates, and mutation status matrices<br>

Usage
-----
Key commands:

    bmr                    ...  Calculate gene coverages and background mutation rates.
    smg                         Identify significantly mutated genes.
    long-gene-filter            Find conditions for which significance status is no longer related to gene size. 
    survival                    Create survival plots and P-values for clinical and mutational phenotypes.  
    clinical-correlation        Correlate phenotypic traits against mutated genes, or against individual variants.
    cosmic                      Match a list of variants to those in COSMIC, and highlight druggable targets.
    cosmic-omim                 Compare the amino acid changes of supplied mutations to COSMIC and OMIM databases.
    dendrix                     Discovery of mutated driver pathways in cancer using only mutation data. 
    dendri-permutation     ...  Run the permutation test for Dendrix. 
    mutation-relation           Identify relationships of mutation concurrency or mutual exclusivity in genes across cases.
    path-scan                   Find signifcantly mutated pathways in a cohort given a list of somatic mutations.
    pfam                        Add Pfam annotation to a MAF file.
    proximity                   Perform a proximity analysis on a list of mutations.
    proximity-window            Perform a sliding window proximity analysis on a list of mutations.
    
    help      this message
    
Install
-----
