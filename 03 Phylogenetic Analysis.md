## **Character types (in Data Science)**

- **Quantitative**: measurements, continuous or discrete (can be made from continuous by binning)
- **Qualitative**: binary or multistate, counts are special case called meristic

## Sequence Alignment

**Pairwise sequence alignment**
- Maximal unique match
- Dot-matrix methods
- Dynamic programming

**Multiple sequence alignment**
- Dynamic programming
- Progressive methods
- Iterative methods
- Motif finding

### **Partitions**

- Multilocus data sets, different genes / gene regions have evolved differently
- Independent application of substitution model allows better fit, but increased model parameters and calculation intensity
- Require predefinition e.g. in NEXUS format

### **Mixture models**

- Accounts for heterogeneity site-by-site, thus better for application when partitions still have heterogeneity
- Commonly uses site-frequency profiles
- Protein functionality information can further limit which amino acids are possible at a given site

> Standard protein substitution models use a single amino acid replacement rate matrix that summarizes the biological, chemical and physical properties of amino acids. However, site evolution is highly heterogeneous and depends on many factors: genetic code; solvent exposure; secondary and tertiary structure; protein function; etc. These impact the substitution pattern and, in most cases, a single replacement matrix is not enough to represent all the complexity of the evolutionary processes.
>
>- [Le _et al_., 2008](https://doi.org/10.1098/rstb.2008.0180)

## Phylogenetic Tree Reconstruction: Algorithms

| Tree Building Method \ Data Type | Distances                 | Nucleotides Sites (discrete)                           |
| -------------------------------- | ------------------------- | ------------------------------------------------------ |
| Clustering Algorithm             | Neighbor-Joining<br>UPGMA |                                                        |
| Optimality Criterion             | Minimum Evolution         | Parsimony<br>Maximum Likelihood\*<br>Bayesian Analys\* |

\*: Probabilistic method

### **Clustering Algorithm**

Trees are constructed by adding taxa to a more similar region of the existing tree, until all taxa are added.

- Easy and fast computing
- Depends on the order in which we add the taxa
- Impossible to evaluate competing hypothesis

### **Optimizing Algorithm**

Assign each possible tree a “score” and choose the best tree we can propose

### **Distance methods**

Produce single tree, fast, BUT …

- Deterministic, does not account for uncertainty
- Loose information (by translating into genetic distances)
- Genetic distances usually inappropriately approximate real divergence (lack of molecular clock)
- Sensitive to genetic saturation and LBA

### **Character-based methods**

- Uses information more efficiently, accounts for every change in the alignment.
- Uses objective criterion among possible trees.
- Ideal: rank all possible trees and choose the best; but practice: heuristic searching algorithms
- Heuristic search
	1. Stepwise addition
		1. connects one taxon at a time, only the optimal tree at each step will be saved
	2. Branch swapping
		1. Nearest-neighbor interchange (NNI): Trees divided into four subtrees which are interchanged
		2. Subtree-pruning-regrafting (SPR): All subtrees pruned from tree, regrafted at all reattachment points
		3. Tree bisection-reconnection (TBR): Tree is cut along a branch to form two subtrees and all possible reconnections are evaluated
	3. Optimize tree score (Parsimony, Likelihood, Posterior probabilitiy) till maximum

## Maximum Parsimony

**Parsimony**: Optimal phylogenetic tree minimizes the total number of character state changes in the tree.
- Principles: as-is, closest, simple, random
- Ordered characters never goes backwards
- Autapomorphies are unique to one taxon, so not informative for parsimony

**Incongruent** ⇒ **Consensus tree**

Tree measurement: **Consistency Index (CI)** = minimum required steps / actual steps
- the higher the CI the better the parsimony

### Search Methods

**Exhaustive search**

- Evaluate all possible trees
- Computational cost makes it unsuitable for more than 10 or 11 taxa

**Branch-and-bound algorithm**

- Finds all shortest trees (brute force), unsuitable for more than 16 taxa.

## Maximum Likelihood

- **Likelihood**: “probability” of a model (distribution) given a data
- **Probability**: “probability” of a data given a model (distribution)

- Test for best-fitting substitution models, calculate likelihood for each model, choose model with smallest BIC or AIC(AICc) score
    - **Akaike information criterion (AIC), BIC (Bayesian information criterion)** is a method evaluating how well a model fits the data

> All models suck at their job. AIC tells you how much they suck.

- **Pros**: strong statistical foundations, model assumptions are explicit (testable), statistical framework for hypothesis testing, less sensitive to homoplasy than distance methods
- **Cons**: poor performance with morphological data, frequentist method

### Branch support

#### Bremer (Decay) Index

- indicates how much longer would a tree be if it did not have certain node under consideration
- the higher the index the better the node is supported

#### Non-parametric bootstrapping

Resampling technique **with** replacement

- Node value gives the frequency of a given clade’s appearance in the pseudoreplicates
- \> 75% is considered high support
- More conservative than posterior probabilities, but still inflated in phylogenomics

Faster alternatives

- UFBoot (Ultrafast bootstrap), high support > 95%
- aLRT, aBayes, SH-aLRT > 85% considered as high support

#### **Jackknifing**

Same as **bootstrapp**, but **without** replacement

## Bayesian Inference

See [04 Bayesian Inference](04%20Bayesian%20Inference.md)

## Consensus Tree

### **Strict rule**
- retains only the groups appearing in all input trees, conflicts become polytomies

### **Majority rule**
- retains groups supported by the majority of input, can include groups not supported by parsimony

### **Semi-strict**
- retains groups that do not conflict, conflicts become polytomies

## Phylogenetic Errors

### Genetic saturation (kind of “homoplasy”)

![](https://www.researchgate.net/publication/235767064/figure/fig2/AS:299640479076356@1448451265485/Effect-of-saturation-on-estimating-divergence-times-For-genetically-divergent-taxa.png)

> When sequences in a multiple alignment have undergone so many multiple substitutions that apparent distances largely underestimate the real genetic distances, the alignment is said to be saturated. Phylogenetic inference works best with datasets that are only slightly saturated. Owing to their reduced state space (four possible bases), nucleotide sequences saturate more rapidly than protein sequences (20 possible amino acids).
>
>- [Philippe _et al._, 2011]([https://doi.org/10.1371/journal.pbio.1000602](https://doi.org/10.1371/journal.pbio.1000602)) 

### **Long branch attraction (LBA)**

A form of systematic error, whereby distantly related lineages are incorrectly inferred to be closely related

- Genetic saturation will result in long branch attraction