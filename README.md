# MuSiC
MuSiC: Identifying mutational significance in cancer genomes

## Introduction
The Mutational Significance In Cancer (MuSiC) consists of downstream analysis tools that can:

1. Apply statistical methods to identify significantly mutated genes<br>
2. Highlight significantly altered pathways<br>
3. Investigate the proximity of amino acid mutations in the same gene<br>
4. Search for gene-based or site-based correlations to mutations and relationships between mutations themselves<br>
5. Correlate mutations to clinical features, using typical correlation measures, and generalized linear models<br>
6. Cross-reference findings with relevant databases such as Pfam, COSMIC, and OMIM<br>
7. Generate typical visualizations like Kaplan-Meier survival estimates, and mutation status matrices<br>

## Usage
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
    
## Install

### 1. Build from source code

Install some packaged prerequisites, and their nested dependencies:

        sudo apt-get install gcc \
        make \
        git \
        cmake \
        curl \
        cpanminus 
        libbz2-dev \
        r-base-core \
        libexpat1-dev \
        zlib1g-dev 


Install samtools ( Download the samtools-0.1.19 from SOURCEFORGE )

```
wget https://sourceforge.net/projects/samtools/files/samtools/0.1.19/samtools-0.1.19.tar.bz2
tar jxf samtools-0.1.19.tar.bz2
cd samtools-0.1.19 
make
export PATH=/path/to/samtools-0.1.19:$PATH
source ~/.bashrc 
```

Download the latest joinx stable release, solve some build dependencies, and then build and install it:

```
git clone https://github.com/genome/joinx.git
cd joinx
mkdir build
cd build
cmake /path/to/joinx/ -DBOOST_BUILD_OPTS="-j 8" -DCMAKE_INSTALL_PREFIX=/path/to/build
make deps 
make
ctest 
make install 
export PATH=/path/to/joinx/bin:$PATH
source ~/.bashrc
```

Note: A problem occurs during the execution of the above `make` command. Fix joinx bugs:

```
Line 9 in the /joinx/src/lib/io/StreamLineSource.cpp
bool StreamLineSource::getline(std::string& line) {
	std::getline(_in, line);
   	return true;
}
```
```
Line 1178 in the /vendor/src/gtest160/include/gtest/internal/gtest-internal.h
if (const ::testing::AssertionResult gtest_ar_ = \
	::testing::AssertionResult(bool(expression))) \
	; \
```
Install some prerequisite Perl modules:

```
sudo cpanm Bit::Vector
sudo cpanm Text::CSV_XS
sudo cpanm Statistics::Distributions
sudo cpanm Statistics::Descriptive
sudo cpanm PDL::Stats::Basic
sudo cpanm Mouse
sudo cpanm YAML::Syck
sudo cpanm Set::Scalar
sudo cpanm Scope::Guard
sudo cpanm Regexp::Common
```

Note: If other perl modules are missing during installation, simply install them using the `sudo cpanm XXX`

Clone the genome master branch:

```
git clone https://github.com/genome/genome.git
sudo apt install libgenome-perl
cd genome/lib/perl/
genome music --help
```





