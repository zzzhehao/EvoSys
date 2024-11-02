> The emphasis in coalescent thinking is to view populations backwards in time, using the **divergence observable in a population to estimate the time to a most recent common ancestor (MRCA)**; this ancestor is the point where gene genealogies come together, or ‘coalesce’, in a single biological organism. Coalescent theory is dependent on tree-based (genealogical) thinking familiar to systematists (Harding 1996). Unlike phylogenetic methods, coalescent theory assumes that **genealogies are random variables**. This follows from an **assumption of mutational neutrality**; in the basic model no particular ancestor is either more or less fit or likely to produce descendants within the genealogy. Also, phylogenetic trees are measured in terms of substitutions or state changes, without an intrinsic time constraint. In contrast, **coalescent trees are calculated in terms of time, set by a fixed mutation rate, and coalescent analyses therefore assume a molecular clock**.
>
>- [Wakeley, 2009]([https://doi.org/10.1093/schbul/syp004](https://doi.org/10.1093/schbul/syp004)) 

## Multispecies coalescent process

Represents the application of coalescent theory to the case of multiple species, results in cases where the relationships among species for an individual gene (the _gene tree_) can differ from the broader history of the species (the _species tree_).

Incongruence between gene tree and taxa tree can be caused by …

### Incomplete lineage sorting process (ILS)

**Lineage sorting process:** lost of the genetic lineage by random process

- leads polyphyletic lineage into para- and eventuell monophyletic lineage (reciprocal Monophyly)
- Speciation has nothing to do with genetic distances, genetic tree only reflect the phylogeny of one gene
- after 4 Ne (effective population size) most species will be reciprocal monophyletic

### Rapidly successive speciation (short branches) 

Can lead to lasting differences in gene and taxa trees

![](https://www.biorxiv.org/content/biorxiv/early/2018/09/11/413427/F1.large.jpg) 

### Hybridization

> **Hybridization**, the crossbreeding between individuals of different species, and **introgression**, the transfer of genes between species mediated primarily by back crossing, have been the focus of evolutionary studies over many decades (see [Anderson, 1949](<https://www.nature.com/articles/hdy201168#ref-CR2>); [Arnold, 1992](<https://www.nature.com/articles/hdy201168#ref-CR5>); [Rieseberg and Carney, 1998](<https://www.nature.com/articles/hdy201168#ref-CR67>)).
>
>- [Twyford and Ennos, 2012]([https://doi.org/10.1038/hdy.2011.68](https://doi.org/10.1038/hdy.2011.68))

- Gene duplication and loss
- Recombination
- Horizontal gene transfer

## Concatenation

Concatenation method concatenates multiple gene sequences of each species and treats them as one alignment to generate a phylogenetic tree ⇒ **Supermatrix**

**Nonparametric methods by summarizing the gene trees**:

> _3.2.1. Nonparametric methods_
>
Nonparametric methods include the consensus (Margush and McMorris, 1981; Degnan et al., 2008; Ewing et al., 2008), reconciliation (Page and Charleston, 1997; Slowinski et al., 1997; Page, 1998; Avise, 2000; Page, 2000; V’Yugin et al., 2002; Bonizzoni et al., 2003; Gorbunov and Lyubetsky, 2005; Berglund-Sonnhammer et al., 2006), and supertree (Wilkinson et al., 2005; Cotton and Wilkinson, 2007; Steel and Rodrigo, 2008) methods. Consensus methods use various techniques to construct a single summary tree from the estimated gene trees that is then taken to be the estimated phylogeny of the species. Consensus methods are nonparametric in the sense that they do not assume a specific underlying distribution for the gene trees. The reconciliation method summarizes gene trees by a single tree (or several trees with the same score) that minimizes the number of coalescence, horizontal, and gene duplication/gene loss events required to reconcile gene trees and the query tree (Berglund-Sonnhammer et al., 2006). **The supertree method is a family of approaches that merge (or summarize) multiple gene trees into a single tree called the ‘‘supertree”** (Bininda-Emonds and Bryant, 1998; Bininda-Emonds and Sanderson, 2001; Day et al., 2008).
>
>- [Liu _et al.,_ 2009]([https://doi.org/10.1016/j.ympev.2009.05.033](https://doi.org/10.1016/j.ympev.2009.05.033)) 