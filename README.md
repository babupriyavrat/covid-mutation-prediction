# Covid-mutation-prediction
This repository is focussed on developing a method to predict next dominant mutant strain of covid-19, thus generating mRNA code of possible virus for vaccine generation.

# Files
There are two files.The data is extracted from NCBI site. It is present in FASTA format.

- Nucleotides - It represents virus nucleic acid code sequenced.
- Proteins - It represents virus amino acid code sequenced.

To know the details about code, please visit the following link
https://en.wikipedia.org/wiki/FASTA_format#Sequence%20representation

# understanding various protein
There are different kinds of proteins.
Please refer to the following article to understand various kind of proteins.

https://virologyj.biomedcentral.com/articles/10.1186/s12985-019-1182-0

# plotting propensity of PANGO lineage
As these virus is fastly mutating, different populations is susceptible to different kind of mutations. Each region have susceptibility to different kind of mutations. This might be due to genetic diversity of humans. As our data is partial and doesn't contain north american and australian data, please correlate the cases in Asia identified in each country with 1 month moving window of PANG0 Lineage discovered. 
For example, for given country, if three PANGO lineage, A, B and C are discovered between  1-Mar-2021 and 31-Mar-2021 are in ratio 20:30:50 and  number of identified cases from 20-Feb-2021 to 20-Mar-2021 are 100k, then A corresponded to 20k cases, B corresponded to 30k cases and C corresponded to 50k cases. The 10-day lag is assumed as incubation period. However, this might not be true for some mutations.

Your result should map to frequency of each PANGO lineage as plotted by nextStrain.

https://nextstrain.org/ncov/asia?c=pango_lineage&d=map,frequencies&l=unrooted&p=full&transmissions=show



# Dividing the data

THe current dominant PANGO Lineage are :B.1.117, B.1.617.1 and B.1.351 in last week of May. As data is available since December, it is suggested to split the  data from January 2020 to January 2021 as training data and February 2020 to May 2021 as testing data.

# Predicting the next major mutation

The idea is simplistic in nature: The nucleic acid sequence and protein sequence is passed to neural network to predict next few variants. The challenge lies in identifying not in predicting the next mutant strain but identifying the next dominant one. It's better to focus on protein sequence which is used to bind the virus to human ACE receptors. One hint can be found that dominant strains have mutations at similar spots. Thus, if any mutation generated  matches with dominant strain at present, then we can consider it as success.

A person or team generating all the three major mutations, i.e.,B.1.117, B.1.617.1 and B.1.351  using training data will be considered winner.
A person or team generating any two major mutations, i.e.,B.1.117, B.1.617.1 and B.1.351  using training data will be 1st runner up.
A person or team generating any one major mutations,i.e, B.1.117, B.1.617.1 and B.1.351  using training data will be considered 2nd runner up.
