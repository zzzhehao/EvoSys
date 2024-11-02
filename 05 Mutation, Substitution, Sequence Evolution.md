## Mutation

- Genome mutation
- Chromosome mutation
- Indel = Insertion and/or Deletion 
- Inversion
- Transition
- Transversion

**Suppressor mutation**: a second mutation which alleviates or reverts the phenotypic effects of an already existing mutation
- **Intragenic suppression**: suppressor mutation occured in the same gene as the original mutation.
    - Crick, et al. used this to establish the fundamental nature of the genetic code.
- **Intergenic suppresion (extragenic)**: the second mutation is not on the same gene as the original mutation.
    - Useful for identifying new genetic sites which affect a biological process of interest
    - Provides evidence between functionally interacting molecules and intersecting biological pathways

## Nucleotide substitutions

- **synonymous (silent)**: no amino acid change
- **missense**: amino acid changes to some else except stop codon
- **nonsense**: amino acid changes to stop codon

All substitution on the second codon site and 96% of the substitutions on the first site are non-synonymous, while 70% of the substitutions on the third site are synonymous

## **Evolutionary dynamics**

Transitions occurs more frequently than transversions, but many transitions can be “overwritten” by one transversion. 

Mutation rate of non-synonymous substitution is usually lower than the rate of synonymous substitution

### Models of nucleotide substitution

- eg. **JC69** (one parameter, assuming equal sequence frequencies), K80, HKY85, **GTR** (most complex w/ 7 parameters) etc.
- The likelihood of a certain nucleotide in a given vertex is not based on the assumption that nucleotides appear equally, but on the frequency observed in the vertex itself (eg. different GC account in genomes from different species)

### Models of amino acid substitution

- **JTT**: based on a larger protein database
- **WAG**: avoids need to use closely-related sequence pairs by obtaining ML estimate of Q matrix
- **LG**: add rate heterogeneity to ML estimation of Q matrix
- **I**: Invariable sites model
- **G**: Discrete Gamma model
- Test for best-fitting substitution models, calculate likelihood for each model, choose model with smallest BIC or AIC(AICc) score