# Cattle_SV_Catalog
Structural variants (SVs) are large genomic alterations of 50 bp or more. Previous trials were made to develop catalogs of bovine SVs. However, these trials are limited by the low precision of short-read variant callers or the prohibitive cost of long-read sequencing. The Great Genotyper (GG) provides unpreceded opportunity to genotype SVs in thousands of SRA publicly available datasets with high precision. With such large population, we can identify common variants that are likely in associations with key agricultural traits.
          In this work, GG was used to construct an efficient index of 1,103 SRA samples from ~ 80 bovine breeds. The index can genotype millions of variants in few hours. As a proof of principle, we used the index to genotype 1.4 million SVs from multiple sources as well as 84M SNVs from Ensemble. We successfully identified 175k common SVs with a minor allele frequency (MAF) greater than 0.05. These SVs intersect with 15K genes and 26K transcripts, with approximately 4.6K of these variants potentially having a significant impact on gene function.  Our work is not only providing a catalog that outperforms previous attempts but also includes sharing the GG index to enable rapid and accurate calculation of population allele frequencies for any new list of variants.  


## Data Download
The final annotated catalog can be downloaded from 
```
https://farm.cse.ucdavis.edu/~mshokrof/cattle_sv_catalog/annotated_catalog.vcf.gz
```


## The Great Genotyper
The great genotyper index to genotype any list of variants in 1103 SRA samples can be downloaded from the following link. 
```
https://farm.cse.ucdavis.edu/~mshokrof/cattle_sv_catalog/GG_INDEX/
```

Please note that the index is partitioned into smaller indices. To run on all the indices, download the content of folders from the previous link into separate folders. and create a description file containing a list of downloaded folders like the following example.

```
/PATH/cattle/cluster.taurus.1/
/PATH/cattle/cluster.taurus.2/
/PATH/cattle/cluster.taurus.3/
/PATH/cattle/cluster.taurus.4/
/PATH/cattle/cluster.taurus.5/
/PATH/cattle/indicus/
```

To run the great genotyper. First download and compile [the code](https://github.com/dib-lab/TheGreatGenotyper)

```
build/pangenie/src/TheGreatGenotyper  -a -g  -i index_folder_list.txt  -j 32 -t 32 -r ARS-UCD1.2_Btau5.0.1Y.fa  -y  emissions -v input.vcf -o output.vcf
```
