Bayesian-based LCA taxonomic classification method
--------------------------------------------------
Bayesian LCA-based Taxonomic Classification Method (BLCA) is a Bayesian-based method that provides a solid probabilistic basis for evaluating the taxonomic assignments for the query sequences with bootstrap confidence scores, which is based on Bayesian posterior probability that quantitatively weigh each database hit sequence according to its similarity to the query sequence - the more similar database hit sequence to the query, the more its contribution to the taxonomic assignment of the query. We implemented the above algorithm as a python3 package at https://github.com/qunfengdong/BLCA.

## System Requirements
* Python (version 3 or above)
* Linux
* libyaml

## Python packages
* python3-dev
* setuptools
* Biopython
* pyyaml

## Additional executable files (required)
* BLAST binary (ftp://ftp.ncbi.nlm.nih.gov/blast/executables/blast+/2.3.0/)
* MUSCLE (http://www.drive5.com/muscle/downloads.htm)

## Database (required)
* 16S Microbial database (ftp://ftp.ncbi.nlm.nih.gov/blast/db/16SMicrobial.tar.gz)

## Alternate database
* If you intend to use customized

## Install
Checkout the source code: https://github.com/qunfengdong/BLCA
```python
$ git clone https://github.com/qunfengdong/BLCA.git
$ cd BLCA
$ python3 setup.py install
```

## Getting started
* Go to any directory or folder
```shell
[current_directory]$ pwd
/path/to/current_directory
```
* Download and save the example input FASTA file (https://raw.githubusercontent.com/qunfengdong/BLCA/master/example/example_input_file.fasta) in the working directory.
```shell
[current_directory]$ wget https://raw.githubusercontent.com/qunfengdong/BLCA/master/example/example_input_file.fasta
```
* Download and save the example config.py file (https://raw.githubusercontent.com/qunfengdong/BLCA/master/example/config.py) in the same folder.
```shell
[current_directory]$ https://raw.githubusercontent.com/qunfengdong/BLCA/master/example/config.py
```

## Config file
Description of the parameters in the config file "config.py"
```python
[current_directory]$ cat config.py
##-----------------------------------------------------------
## Input file in FASTA format
FILENAME = 'example_input_file.fasta'

## Output file
OUTFILE = 'annotation_output.txt'

## BLAST parameters
BLAST_BINARY = 'path/to/dir/ncbi-blast-2.3.0+/bin'
## Path to the actual indexed BLAST database with 16SMicrobial.n* files
BLAST_DATABASE = 'path/to/file/16SMicrobial'
## MUSCLE executable file
MUSCLE_BINARY = '/path/to/bin/muscle'

## BLAST output filtering options
## Select hits with at least a score 100
BLAST_CUTOFF_SCORE = 100
## Select hits within less then 10% score of the top hit
BLAST_CUTOFF_PERCENT = 10
## Select hits with at least 95% coverage
BLAST_COVERAGE = 95
## Select hits with at least 95% percentage identity
BLAST_PERCENTAGE_IDENTITY = 95

## Mutiple sequence alignment parameters
## Select 10 base pairs of hit sequences
## upstream and downstream of the alignment
HIT_SEQUENCE_BPS = 10

## Alignment scoring values
ALIGNMENT_GAP = -2.5
ALIGNMENT_MISMATCH = -2
ALIGNMENT_MATCH = 1

## Bootstrap
BOOTSTRAP = 100
##-----------------------------------------------------------
```

## Running BLCA
### Run BLCA on command line
```python
[current_directory]$ python3
>>> import blca
>>> import config
>>> blca.execute()
```

### Run BLCA in a file called analysis.py.
```python
import blca
import config
blca.execute()
```

Execute the file 'analysis.py' at the terminal
```python
[current_directory]$ python3 analysis.py
```

## Output

## Recommendations
* Make sure the sequence headers in the FASTA file DO NOT have "|" (pipe) characters in them. Please change them to "_" (underscore)

## Version
* Version 0.6
first public release

## Authors
* Dr. Xiang Gao, theoretical conception and algorithm development
* Dr. Qunfeng Dong, algorithm development
* Kashi Revanna, program coding and package development
* Huaiying Lin, program coding and testing

## License
GNU

## Acknowledgements
* BLAST program: Camacho C., Coulouris G., Avagyan V., Ma N., Papadopoulos J., Bealer K., & Madden T.L. (2008) "BLAST+: architecture and applications." BMC Bioinformatics 10:421.
* MUSCLE: Edgar, R.C. (2004) MUSCLE: multiple sequence alignment with high accuracy and high throughput.Nucleic Acids Res. 32(5):1792-1797. doi:10.1093/nar/gkh340
* Biopython: Cock PA, Antao T, Chang JT, Bradman BA, Cox CJ, Dalke A, Friedberg I, Hamelryck T, Kauff F, Wilczynski B and de Hoon MJL (2009) Biopython: freely available Python tools for computational molecular biology and bioinformatics. Bioinformatics, 25, 1422-1423

