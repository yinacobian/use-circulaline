# use-circulaline
Use of circulaline software

Use of the repository: https://github.com/deprekate/circulaline


1. git clone https://github.com/deprekate/circulaline

2. Make a folder with the phage genomes on individual fasta files

3. Make sure they don't have strange characters

4. Make sure they have a new line at the end of each sequence, when you do 

cat genomes/* | grep '>' 

each genome name should be in a single line

>83-24
>Axy06
>Axy14
>Axy16
>JWAlpha
>JWDelta
>JWF
>JWX
>phiAxp-1
>phiAxp-2
>phiAxp-3


5. Make sure you have a gene where you want the sequences to begin, in this case is the terminase. 

6. 

