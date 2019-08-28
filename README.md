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
    clinical-correlation        Correlate phenotypic traits against mutated genes, or against individual variants.
    cosmic                      Match a list of variants to those in COSMIC, and highlight druggable targets.
    cosmic-omim                 Compare the amino acid changes of supplied mutations to COSMIC and OMIM databases.
    create-visualizations       no description!!!: define 'doc' in the class definition for                   
                                Genome::Model::Tools::Music::CreateVisualizations
    data                   ...  Parse, standardize, and index various third-party datasets used by the tools in MuSiC.
    mutation-relation           Identify relationships of mutation concurrency or mutual exclusivity in genes across cases.
    path-scan                   Find signifcantly mutated pathways in a cohort given a list of somatic mutations.
    pfam                        Add Pfam annotation to a MAF file.
    play                        Run the full suite of MuSiC tools sequentially.             
    plot                   ...  Generate relevant plots and visualizations for MuSiC.
    proximity                   Perform a proximity analysis on a list of mutations.
    smg                         Identify significantly mutated genes.
    survival                    Create survival plots and P-values for clinical and mutational phenotypes.
    
    help                        this message
    
Install(Ubuntu)
-----
