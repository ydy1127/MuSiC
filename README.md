# MuSiC
MuSiC: Identifying mutational significance in cancer genomes

## Introduction
The Mutational Significance In Cancer (MuSiC) consists of downstream analysis tools that can:

1. Apply statistical methods to identify significantly mutated genes;<br>
2. Highlight significantly altered pathways;<br>
3. Investigate the proximity of amino acid mutations in the same gene;<br>
4. Search for gene-based or site-based correlations to mutations and relationships between mutations themselves;<br>
5. Correlate mutations to clinical features, using typical correlation measures, and generalized linear models;<br>
6. Cross-reference findings with relevant databases such as Pfam, COSMIC, and OMIM;<br>
7. Generate typical visualizations like Kaplan-Meier survival estimates, and mutation status matrices;<br>

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

There are three ways to install and deploy MuSiC:

- Build from *genome* source code
- Download and build the GMS and run MuSiC from it
- Download the GMS image file and use GMS quickly

#### 1. Build from source code

Install some packaged prerequisites, and their nested dependencies:
```
sudo apt-get install gcc \
make \
git \
cmake \
curl \
cpanminus \
libbz2-dev \
r-base-core \
libexpat1-dev \
zlib1g-dev \
build-essential \
libgtest-dev
```

Install samtools ( Download the samtools-0.1.19 from SOURCEFORGE )

```
wget https://sourceforge.net/projects/samtools/files/samtools/0.1.19/samtools-0.1.19.tar.bz2
tar jxf samtools-0.1.19.tar.bz2
cd samtools-0.1.19 
make
export PATH=/path/to/samtools-0.1.19:$PATH
source ~/.bashrc 
```

Download the latest joinx stable release, and then build and install it:

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

Note: If other perl modules are missing during installation, simply install them using the `sudo cpanm XXX`.

Clone the genome master branch:

```
git clone https://github.com/genome/genome.git
sudo apt install libgenome-perl
cd genome/lib/perl/
genome music --help
```

Note: When running `genome music`, if you are prompted with error messages that some  parameters cannot be located, you need to add an environment variable:

```
export XGENOME_CONFIG_SNAP=/path/to/genome/etc
```

#### 2. Download and build the GMS

Note: To install the GMS you will need root/sudo access and a fast internet connection to download all packages and demonstration data sets .It only runs on Ubuntu 12.04 Precise operating system.

For a standard, standalone, configuration on Ubuntu 12.04 run:

```
sudo apt-get install git ssh make
git clone https://github.com/genome/gms.git
cd gms
make
gmt music --help
```

Installation on another platform (Mac OS X, Linux distributions other than Ubuntu 12.04) requires a virtual machine (VM). See the https://github.com/genome/gms/wiki/Install for detailed operation process.

#### 3. Quick VM Tour

#### Introduction

The simplest way to get a quick sense of what the GMS is all about is to try loading a virtual machine where the GMS has already been installed and configured. When the GMS virtual machine loads you will be logged in as the user `genome` (with a password that is also `genome`). All installation and configuration steps will be complete and demonstration data will be in place. 

#### Steps

Step 1. Install VirtualBox:

Download the latest version Virtualbox from https://www.virtualbox.org/wiki/Downloads.

Step 2. Download a Pre-configured GMS VirtualMachine Image:

Download the GMS_VM_V1.tar.gz from https://xfer.genome.wustl.edu/gxfer1/project/gms/vms/ .

Note: The size of this file is about 50G. It will take some time to download.

Step 3. Unpack the Image:

Use your favorite decompression software to unpack the virtual machine.

Step 4. Import the Image:

Import the gms_vm_v1.vdi image file into the Virtualbox virtual machine.

Step 5. Start the GMS system:

Open the terminal and input `gmt music --help` to check the help information after entering the system.

Note: See the https://github.com/genome/gms/wiki/Quick-VM-Tour for detailed operation process.

### Compare the above three methods:

1. Build genome source code using MuSiC, the installation process is complex due to the large number of dependencies.MuSiC is encapsulated in genome. Once the source code of genome is changed by the developers, there may be problems running MuSiC.However, this method occupies less memory and is compatible with various systems.

2. Download and build GMS, which requires Ubuntu 12.04 as the system is very limited.But the installation process is simple.

3. Directly download the mirror file of GMS, although the installation and deployment is the simplest, it takes up a lot of memory space.

Several approaches have advantages and disadvantages.You can choose your own installation method according to your own requirements and hardware resources.
