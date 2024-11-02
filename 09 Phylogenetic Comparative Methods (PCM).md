Used to infer evolutionary process and history through comparing species character data in a phylogenetic context. Many standard statistical methods assume that data are independent, BUT, phylogenetic tree terminals cannot be treated as independent data.

Therefore **Phylogenetic Independent Contrasts (PIC)**: a statistical transformation that creates independent data points from trees, can be used to test for evolutionary correlations between characters.

## Models for Character Evolution

### Continuous traits

#### Brownian Motion

"Evolution proceeds with random changes."

- A “random walk” model of evolution of continuous characters, describes motion that results from a large number of weak, independent forces
- Genetic drift, random change, weak selection (especially given timeframe)
$$ \sigma ^2=\frac{\Sigma S_i}{n-1} $$
- $\sigma ^2$ is related to standarized contrasts from PIC, affects the range of the motion.

#### Brownian Motion with a Trend (Trend)

BM with a directional trend.

#### Ornstein-Uhlenbeck Process

"Evolution bounded around median value - equilibrium"

#### Early Burst (EB)

"Rate of evolution decreases through time."

#### Late Burst (LB)

"Rate of evolution increases through time."

### Discrete traits

#### MK model

- Most widely used.
- Uses “Q” matrix of instantaneous transition rates between states:
	- **Equal rates (ER)**
	- **Symmetric rates (SYM)** - forward and reverse are equal
	- **All rates different (ARD)**

## *A note on working with continuous characters*

### **Log transformation**

When working with continuous characters, we should always consider **log-transforming** our data before conducting analysis.

- Log-transformation result in a ratio scale between data points
- In biology, percentage change rather than absolute change is often what matters
- Log-transformation often result in distribution closer to normal
