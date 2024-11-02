## Bayesian Mathematics

Joint probability > $Pr(B, D)$

Conditional probability > $Pr(B |D)$

Marginal probability > $Pr(D)=Pr(B,D)+Pr(W,D)$

### **Bayes’ theorem**

$$ Pr(B|D)=\frac{Pr(D|B)Pr(B)}{Pr(D)} $$

**In statistics:**

$$ Pr(\theta|D)=\frac{Pr(D|\theta)Pr(\theta)}{\Sigma_{\theta }Pr(D|\theta)Pr(\theta)} $$

$Pr(\theta)$: Prior probability of hypothesis $\theta$

$Pr(D|\theta)$: Likelihood of hypothesis $\theta$ (Probability that the data is true given hypothesis $\theta$)

$\Sigma_{\theta }Pr(D|\theta)Pr(\theta)$: Marginal probability of the data (marginalizing over hypothesis)

$Pr(\theta|D)$: Posterior probability of the hypothesis $\theta$

**For continuous data:**

$$ p(\theta|D)=\frac{p(D|\theta)p(\theta)}{\int p(D|\theta)p(\theta)d \theta} $$

$p(\theta)$: Prior probability density

$p(D|\theta)$: Likelihood

${\int p(D|\theta)p(\theta)d \theta}$: Marginal probability of the data (marginalizing over hypothesis)

$p(\theta|D)$: Posterior probability density

- Probabilities are attached to intervals, not individual values
    - area of an interval underneath the **probability density function** is the **probability**, i.e. integrating a density yields a probability
- Density curves are all variation of a gamma probability distribution, prior with different variance and means shapes different curve, the higher the variance, the less informative it is

## Markov Chain Monte Carlo (MCMC)

- Exact marginal probability of data become extremely impractical to calculating while analyzing multiparametric data
    
    e.g., a 2-parameter analysis (the integrals are folded!):
    
    $$ p(\theta , \phi|D)=\frac{p(D|\theta, \phi)p(\theta)p(\phi)}{\int_\theta \int_\phi p(D|\theta, \phi)p(\theta)p(\phi)d \theta d\phi} $$
    
- an approximation of the posterior probability, i.e. a histogram
    

### Metropolis algorithm (MCMC robot)

- calculating score ratio (R = Proposed / Current), if a uniform(0,1) random deviate > R, reject propose
    - Uphills are always be accepted
    - Slight downhills are usually accepted, drastic “off the cliff” are almost never accepted
- if proposal distributions are …
    - too narrow, steps are small (”baby steps”), big waves in trace plot
    - too wide, steps are huge, proposes are often declined, robot stuck in one place
    - appropriate, white noise in trace plot can be observed, indicates “good mixing”

### Metropolis-coupled MCMC (MCMCMC)

helps robot explore tree topology to prevent stucking in local maxima

- **Cold chain** is normal chain and follows the Metropolis algorithm
- **Heated chain ****has modified posterior probability which is flattened out, allow them taking more “risky” steps and explore the topology as scouts
- Swaps between cold and heated chain allows cold chain to reach the global maxima

### Hasting ratio

rebalace propose bias caused by assymetric distribution

## Bayesian phylogenetic inference

### MCMC analysis steps

1. Choose starting states
2. Update one or more parameters
    1. Choose parameter(s)
    2. Propose new state(s)
    3. Calculate ratio R
    4. Draw _u_ from Uniform(0,1)
    5. if _u_ < R, accept; otherwise, reject
3. Save tree and parameters
4. go back to step 2, loop till defined sample amount has been saved
5. Summarize and sample the posteriors

### MCMC Convergence

- Posterior probability is approximated ⇒ a collection of trees from posterior distribution
- **Burnin**: initial states with low posterior probability need to be discarded
- **Convergence**: multiple runs need to reach similar results, assesed _a posteriori_

**Diagnostics** (Program: [TRACER](https://beast.community/tracer_convergence))

- **ESS (Effective sample size)** > 200
- **Traces** (e.g. lnL (log-Likelihood) across iterations) should have reached stationarity for enough generations

### Prior distributions

- Prior probabilities are assigned to all parameters, usually the distribution of the parameter _a prioir_ is unknown ⇒ uninformative (flat) priors (**Uniform**) are used
- **Gamma(a,b)** distributions are appropriate for parameters range from 0 to infinity (e.g., branch lengths)
    - **Lognormal($\mu$,$\sigma$)** distribution
- **Beta(a,b)** distribution are appropriate for proportions which lie in [0,1]
- **Dirichlet(a,b,c,d)** distribution, ideal for nucleotide relative frequencies

### Posterior probabilities

Support values, indicating the confidency on the topology

> The accuracy of Bayesian clade support has recently been called into question in a number of studies (dis cussed in more detail below). In our opinion, this repre sents the most troubling property of the Bayesian method. While the issue is unresolved and complex, nearly all comparisons of resampling support (i.e., jack knife and bootstrap) and Bayesian clade support indicate that Bayesian support is generally higher. Some of these studies interpret this as underestimation of support by resampling methods. In other words, this is equivalent to an **increased probability of assigning low support to correct nodes, a type-II error** (Wilcox & al., 2002; Alfaro & al., 2003). Others interpret the trend as **inflation of Bayesian support values, or an increased probability of Bayesian methods to support incorrect nodes, a type I error** (Suzuki & al., 2002; Cummings & al., 2003; Douady & al., 2003; Erixon & al., 2003; Simmons & al., 2004).

- Randle _et al_., 2005

> 0.95 considered as highly supported

## References

Randle, C.P., Mort, M.E. and Crawford, D.J. (2005) ‘Bayesian Inference of Phylogenetics Revisited: Developments and Concerns’, _Taxon_, 54(1), pp. 9–15.

[Phyloseminar #78: Paul Lewis (UConn) Primer part 3a](https://www.youtube.com/watch?v=4PWlnNsfz90)

[Phyloseminar #79: Paul Lewis (UConn) Primer part 3b](https://www.youtube.com/watch?v=TLtOS--YwkU)