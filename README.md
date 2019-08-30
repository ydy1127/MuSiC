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
7. Generate typical visualizations like Kaplan-Meier survival estimates, and mutation status matrices.<br>

## Usage

```
Program:  MuSiC - Mutational Significance in Cancer
Version:  V0.1

# for the Method 1
Usage:  genome music <command> [options]
# for the Method 2 & Method 3
Usage:  gmt music <command> [options]
```

Key commands:

```
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
```

## Install

There are three methods to install and deploy MuSiC:

- Method 1: Build from source code(https://github.com/genome/genome)
- Method 2: Download and build the GMS (https://github.com/genome/gms)
- Method 3: Import the GMS image file into the VM(https://github.com/genome/gms/wiki/Quick-VM-Tour)

#### Comparison of three methods:

- Method 1: The installation process by the Method 1 is complex due to the large number of dependencies. However, this method occupies less memory (about 1G) and is compatible with multiple versions of the Linux operating system;

- Method 2: Download and build the GMS, which only runs on Ubuntu 12.04, so the application environment is very limited. But the installation process is simple;

- Method 3: Directly download the image file of GMS, although the installation and deployment is the simplest, it takes up a lot of memory space (at least 50G).

Several approaches have advantages and disadvantages. You can choose the appropriate installation method based on your requirements and hardware resources.

#### 1. Build from source code

Prerequisites for OS: Existing Ubuntu distributions

Install some prerequisites, and their nested dependencies:

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

Note: When running `genome music`, if you are prompted with error messages that some parameters cannot be located, you need to add an environment variable:

```
export XGENOME_CONFIG_SNAP=/path/to/genome/etc
```

#### 2. Download and build the GMS

GMS(Genome Modeling System) is a knowledge management platform for genomics. GMS provides many tools for genome modeling, such as MuSiC.

Note: To install the GMS you will need root/sudo access and a fast internet connection to download all packages and demonstration data sets. It only runs on Ubuntu 12.04 Precise operating system.

For a standard, standalone, configuration on Ubuntu 12.04 run:

```
sudo apt-get install git ssh make
git clone https://github.com/genome/gms.git
cd gms
make
gmt music --help
```

Installation on another platform (Mac OS X, Linux distributions other than Ubuntu 12.04) requires a virtual machine (VM). See the https://github.com/genome/gms/wiki/Install for detailed operation process.

#### 3. Import the GMS image file into the VM


The easiest way to quickly use the tools in the GMS is to try to load a virtual machine that has been installed and configured with the GMS. When you launch the GMS system, you will login with the username "genome" (password is also "genome"). Specific installation steps are as follows:

**Step 1. Install VirtualBox:**

Download the latest version Virtualbox from https://www.virtualbox.org/wiki/Downloads.

**Step 2. Download a Pre-configured GMS VirtualMachine Image:**

Download the GMS_VM_V1.tar.gz from https://xfer.genome.wustl.edu/gxfer1/project/gms/vms/.

Note: The size of this file is about 50G. It will take some time to download.

**Step 3. Unpack the Image:**

Use your favorite decompression software to unpack the virtual machine.

**Step 4. Import the Image:**

Import the gms_vm_v1.vdi image file into the Virtualbox virtual machine.

**Step 5. Start the GMS system:**

Open the terminal and input `gmt music --help` to check the help information after entering the system.

Note: See the https://github.com/genome/gms/wiki/Quick-VM-Tour for detailed operation process.

## Example

 Count covered bases per-gene for each given tumor-normal pair of BAMs:

```
genome music bmr calc-covg --roi-file example.roi_file --bam-list example.bam_list_test --reference-sequence fetch_chr_ucsc.hg19.fasta --output-dir ./
```
or
```
gmt music bmr calc-covg --roi-file example.roi_file --bam-list example.bam_list_test --reference-sequence fetch_chr_ucsc.hg19.fasta --output-dir ./
```

```
REQUIRED INPUTS
  roi-file
    Tab delimited list of ROIs [chr start stop gene_name] (See Description) 
  reference-sequence
    Path to reference sequence in FASTA format 
  bam-list
    Tab delimited list of BAM files [sample_name normal_bam tumor_bam] (See Description) 
  output-dir
    Directory where output files and subdirectories will be writte
```

## Output

Running the above example generates three files in the current directory. The details of the generated file are as follows:

roi_covg/CNIC-00-21-0001.covg:

| Gene    | ROI              | Length | Covered | ATs_Covered | CpGs_Covered | CGs_Covered |
| ------- | ---------------- | ------ | ------- | ----------- | ------------ | ----------- |
| DDX11L1 | chr1:11867-12229 | 363    | 0       | 0           | 0            | 0           |
| DDX11L1 | chr1:12611-12723 | 113    | 0       | 0           | 0            | 0           |

gene_covg/CNIC-00-21-0001.covg:

| Gene | Length | Covered | AT_covd | CG_covd | CpG_covd |
| :--: | :----: | :-----: | :-----: | :-----: | :------: |
| A1BG |  1534  |  1534   |   559   |   190   |   785    |
| A1CF |  2263  |  2110   |  1148   |   68    |   894    |

total_covgs:

|     Sample      | Covered_Bases | AT_Bases_Covered | CG_Bases_Covered | CpG_Bases_Covered |
| :-------------: | :-----------: | :--------------: | :--------------: | :---------------: |
| CNIC-00-21-0001 |   35440510    |     17281313     |     2066127      |     16093070      |

