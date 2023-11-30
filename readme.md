# gbToGFF: A script to extract features from NCBI genbank files to GFF file
This script can be sued to convert gb files to GFF3, and to extract a list of features to GFF3. It can extract using a list of locus_tags or by size.
The extraction by size will only extract features with _translation_ qualifier in the genbank file. Extracts proteins smaller than the specified value (-s --size).

### Requirements
BCBio and Biopython

#### Installation of the required modules
pip install bcbio-gff  
pip install biopython  

## Running the script

```
./gbToGFF.py 
usage: gbToGFF.py [-h] -g GENOMES [GENOMES ...] [-e] [-s SIZE] [-l LT_FILE]
gbToGFF.py: error: the following arguments are required: -g/--genomes
```

```
usage: gbToGFF.py [-h] -g GENOMES [GENOMES ...] [-e] [-s SIZE] [-l LT_FILE]

Converts gb files to GFF3. Extracts a list of features to GFF3.

options:
  -h, --help            show this help message and exit
  -g GENOMES [GENOMES ...], --genomes GENOMES [GENOMES ...]
                        Genomes to convert in Genbank format. <Space separated
                        list of genbank files. Also accepts *.gb >
  -e, --extract         Set on for feature extraction. <boolean>
  -s SIZE, --size SIZE  Size cutoff <INT>
  -l LT_FILE, --locus_tags LT_FILE
                        A file containing a list of locus_tags to extract. <File,
                        one locus tag on each line>
```

```
OUTPUT
Extraction of features of less than 210 nucleotides.
Processing genome.gb...
A total of 161 smORFs were extracted...
```
For testing roary was run with the following command: `roary -f output_folder *.gff`
