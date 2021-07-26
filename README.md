### rRNA ITS2 Sequence-Structure analysis

#### Detection and extraction of ITS2 from ribosomal sequences using itsx software (https://doi.org/10.1111/2041-210X.12073)
install itsx using conda:
```
conda install itsx
```

Extract ITS2 sequence regions using:

```
ITSx -i 18S_seqs4ITS.fas -o ITSx_out --date F -t all --cpu 12 --preserve F --save_regions 'ITS2' --anchor 0 --only_full T --concat T
```

#### Perform multiple sequence alignment using MAFFT:
install mafft using conda:
```
conda install mafft
```
Align ITS2 sequences using mafft:
```
ginsi ITSx_out.ITS2.fasta > ITS2_aln.fas
```

#### Create consensus secondary structure in Stockholm format using RNAalifold
install ViennaRNA package including RNAalifold using conda:
```
conda install viennarna
```
calculate secondary structure for aligned ITS2 sequences using rnaalifold:
```
rnaalifold --input-format F -p -r -d2 --noLP --color --aln < ITS2_aln.fas > ITS2_alifold.out 
```
