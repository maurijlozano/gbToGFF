# gbToGFF: A script to extract features from NCBI genbank files to GFF file


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

# Testing for Roary
S. meliloti genomes from strains 2011, AK83 and SM11 were used. `./gbToGFF.py -g *.gb -e` (Extraction size = 210, default)

```
OUTPUT
Extraction of features of less than 210 nucleotides.
Processing 2011.gb...
A total of 185 smORFs were extracted...
Processing AK83.gb...
A total of 314 smORFs were extracted...
Processing SM11.gb...
A total of 309 smORFs were extracted...
```
Roary was run with the following command: `roary -f roary_results *.gff `
For SM2011, only 180 genes were assigned to groups.
For SINME, 306 genes were assigned to groups.
For SM11, 305 genes were assigned to groups.
Missing 17 genes...
Of the 185 genes for S. meliloti, some were annotated as partial, with only 161 having a translation field in features qualifiers.

### Correction of the script
Only the features with translation will be extracted.
```
OUTPUT
Extraction of features of less than 210 nucleotides.
Processing 2011.gb...
A total of 161 smORFs were extracted...
Processing AK83.gb...
A total of 261 smORFs were extracted...
Processing SM11.gb...
A total of 272 smORFs were extracted...
```
Roary was run with the following command: `roary -f roary_results *.gff `
For SM2011, 161 genes were assigned to groups.
For SINME, 261 genes were assigned to groups.
For SM11, 272 genes were assigned to groups.
Great!!!!