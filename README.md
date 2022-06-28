# BLASTp for SelB Protein
# 2022-06-28
1. Go to NCBI Protein Database. Search for E. Coli SelB protein. Download first result in fasta format. Accession number CAD5999244.1

2. Install BlastP using miniconda
```
conda install -c bioconda blast
```
check version
```
blastp -version
```
To get blastp version 2.12.0, may need to use 
```
conda install -c bioconda blast=2.12.0 -y
```
4. Run BLASTp:
```
blastp -query ecoli_selb.fasta -db nr -out selb_hit1.csv -outfmt '10 qstart qend sstart send sacc ssciname stitle evalue qlen sseq' -evalue 0.00000001 -max_target_seqs 50 -remote
```
5. Convert csv file into FASTA file
```
while read -r line; do id=`echo $line | cut -d',' -f5`; seq=`echo $line | cut -d',' -f10`;echo '>'$id"\n"$seq; done < selb_hit1.csv > selb_hit2.fasta
```
error from copy pasting, delete single quotes and add again
