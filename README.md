# use-circulaline
Use of circulaline software

Use of the repository: https://github.com/deprekate/circulaline


1. git clone https://github.com/deprekate/circulaline

2. Make a folder with the phage genomes on individual fasta files

3. Make sure they don't have strange characters

4. Make sure they have a new line at the end of each sequence, when you do 

cat genomes/* | grep '>' 

each genome name should be in a single line

5. Make sure you have a gene where you want the sequences to begin, in this case is the terminase (file terminase.faa)

6. convert the files from microsoft formatted to linux (there were weird hidden characters in the sequences)

$ ls achromo_genomes/ | xargs -i dos2unix achromo_genomes/{}

7. change the space in the fasta header line to underscores

$ perl -p -i -e 's/ /_/g' achromo_genomes/*

8. blastx the genomes against the terminase, then pipe to my script to get the begin location and direction

$ cat achromo/*.fna | blastx -subject terminase2.faa -outfmt 6 -max_hsps 1 | python3 get_location.py > locations.tsv

9. use the locations to cut the nucleotide sequences and shift them around

$ python3 circulaline.py achromo locations.tsv > sorta_lined_up.fasta 


##Example for Achromophages

perl -p -i -e 's/ /_/g' AchromophagesLiterature/*


cat AchromophagesLiterature/*.fasta | blastx -subject terminase.faa -outfmt 6 -max_hsps 1 | python3 get_location.py > AchromophagesLiterature/locations.tsv

python3 circulaline.py AchromophagesLiterature/ AchromophagesLiterature/locations.tsv > AchromophagesLiterature/sorta_lined_up.fasta

