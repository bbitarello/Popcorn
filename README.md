Popcorn
======

Popcorn is a program for estimaing the correlation of causal variant effect
sizes across populations in GWAS. Estimation involves two steps:

1. Compute mode: computing cross-population scores from a reference panel,
these roughly correspond to the similarity of the LD at each SNP across the populations
2. Fit mode: fitting the heritability and transethnic genetic correlation of
a pair of summary statistics files to the scores

There is no need to install Popcorn. Simply clone the git repository to a folder
called popcorn and run with python -m popcorn {compute,fit} <arguments> outfile. Please see the examples
below and the argument documentations for details.

Example usage:  
'python -m popcorn compute -v 1 --bfile1 /path/to/EUR_refpanel --bfile2 /path/to/EAS_refpanel scores.txt'  
'python -m popcorn fit -v 1 --cfile scores.txt --sfile1 /path/to/EUR_sumstats.txt --sfile2 /path/to/EAS_sumstats.txt EUR_EAS_corr.txt'  

For a full list of arguments and documentations type:  
'python -m popcorn compute -h'  
'python -m popcorn fit -h'  

Output:  
Popcorn reports the common-SNP observed scale (Val (Obs)) heritability (h^2) for both populations (h1^2 and h2^2),
the genetic effect or genetic impact correlation (pge or pgi), and the standard error of
these estimates (SE). If a transormation to the underlying liability scale is requested,
it also outputs the value on the liability scale (Val (Lia)). Popcorn also computes Z-scores
and p-values corresponding to these Z-scores. In the case of heritability, the p-value
reported is for a test that the heritability is *greater than 0*: P(h^2 > 0.0). In the
case of genetic correlation the p-value reported is for a test that the genetic correlation
is *less than 1.0*: P(pg < 1.0).

Dependences:  
Popcorn was developed using the following external python libraries.
If you experience problems running Popcorn, try updating your libraries,
epecially less stable ones like Pandas, Pysnptools and Statsmodels,
to the versions listed here.  
numpy 1.9.2  
scipy 0.16.1  
statsmodels 0.6.1  
pandas 0.17.1  
pysnptools 0.3.9  
bottleneck 1.0.0  

Do not hesitate to contact me with questions as this is early stage software!

For more details of the method please see: http://biorxiv.org/content/early/2016/02/23/036657 or http://www.cell.com/ajhg/abstract/S0002-9297(16)30135-5