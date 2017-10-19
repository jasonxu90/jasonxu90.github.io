
---
# [](#header-1)Research

My research lies at the interface of methodology for statistical learning/inference and optimization. I am particularly interested in inference under partially observed data arising from continuous-time Markov processes, an exciting problem that combines spectral methods and stochastic process theory. The computational aspects of this challenge demand the development of efficient and robust optimization or sampling techniques. 
These considerations lead to new directions toward scalable algorithms for large-scale and high-dimensional estimation under a wide range of constraints including sparsity, rank, smoothness, and shape restrictions. A recurring theme in this recent line of work entails converting difficult (nonsmooth, nonconvex) problems into feasible subproblems via operator splitting or iterative schemes.

On the applications side, much of my work has focused on stochastic modeling and inference for hematopoiesis, the process of blood cell production. I enjoy collaborating closely with scientists and learning about new domains; recent areas of interest include infectious disease modeling, statistical problems in medical imaging, and analyzing environmental data.

A list of publications along with software is available [here](https://jasonxu90.github.io/publications.html).


Selected Current Projects
-------
Some of the things I'm thinking about:

__Fast + positive definite sparse covariance estimation__ (_with Ken Lange_)

<img src="https://jasonxu90.github.io/files/cov.png " width="58%">

Seeking a sparse estimate of a covariance matrix reduces the number of effective parameters in a problem whose dimension grows quadratically in the number of covariates. Zero entries have an important interpretation as marginal independencies, in contrast with zeros in the inverse covariance (_precision_) matrix which encode conditional independence. The latter problem is well-studied; l<sub>1</sub> shrinkage methods such as graphical lasso offer a nice solution. Sparse covariance estimation is more difficult: the likelihood is not convex, and existing penalized likelihood approaches quickly become limited by the size of the data. Even on moderately sized problems, they may approach the solution slowly in practice. 

We develop a proximal distance algorithm based on majorization-minimization (MM), a principle that generalizes the expectation-maximization (EM) framework better known to statisticians. Both transfer optimization onto a sequence of nicer _surrogate functions_. We produce a tighter surrogate than existing MM approaches, important toward achieving faster convergence empirically.  As an alternative to l<sub>1</sub> shrinkage, we penalize the distance from each estimate to its projection onto a symmetric sparsity set. Doing so yields nice properties: while most MM algorithms rely on gradient or Newton steps, these sequential minimizations admit direct solutions that can be efficiently computed by exploiting a surprising connection to dynamical systems and control theory. Positive definiteness is often a cumbersome constraint, but is guaranteed at each iterate via simple backtracking using our approach. These merits go a long way in practice, as demonstrated in an analysis of international migration data with tens of thousands of parameters to be estimated. 

* * *
__Large-scale multivariate convex regression__ (_with Hua Zhou, Wotao Yin, Rahul Mazumder, Lori Hu, Eric Chi_)

<img src="https://jasonxu90.github.io/files/convex.png " width="70%">

Shape-constrained regression and density estimation are classical statistical problems, but algorithms in the multivariate setting lag behind recent theoretical contributions. Convexity is the simplest shape restriction that enjoys a natural generalization to higher dimensions, but regression subject to convexity restrictions presents computational challenges, as the set of constraints to be enforced increases rapidly with the number of observations. 

Building on [recent](https://arxiv.org/abs/1509.08165) work, we present an alternating directions (ADMM) algorithm to solve this problem that can handle datasets with hundreds of thousands of observations, with dimensionality in the thousands. 
Our formulation includes l<sub>2</sub> regularization of the subgradients to reduce generalization error by combating erratic fluctuations near the boundary. Such behavior is a well-known phenomenon in nonparametric regression that effects large biases when unaccounted for. The resulting objective function decomposes into three blocks, and we provide a direct proof that our three-operator splitting algorithm enjoys primal + dual convergence via a variational inequality characterization. This is a departure from the many studies applying ADMM to objectives with more than two blocks, which works well in some cases but is not guaranteed to be convergent. We apply our method to econometric and environmental data. 

* * *
__Bayesian inference for fitting SIR models to massive, partially observed outbreaks__ (_with Jon Wakefield, Vladimir Minin_)

<img src="https://jasonxu90.github.io/files/sir.png " width="64%">

Continuous-time stochastic processes subject to nonlinear mechanistic dynamics are notoriously difficult to study mathematically. This is true of the stochastic Susceptible-Infected-Removed (SIR) process, a relatively simple model of infection that has become seminal in epidemiology. The majority of statistical studies resort to methods based on forward simulation from the model. As these are largely limited to systems comprised of thousands of individuals, statistical studies of larger outbreaks resort to model simplifications such as piecewise constant or diffusion approximations.

Our approach relies on a branching process that closely approximates the SIR model. This process enjoys many nice properties, including closed form expressions for transition probabilities, and one could efficiently perform approximate inference under the SIR model based on the likelihood or posterior of the branching process. Among these nice properties is a simple distribution of infection times over any finite interval, given the populations at the endpoints. We show that this property enables efficient complete data augmentation by treating the branching approximation as a proposal density. This yields Metropolis-Hastings methods that target the _exact_ SIR posterior even when only one of the three populations is observed, i.e. we only observe new disease cases. Currently, the resulting Markov chain Monte Carlo algorithm is feasible for outbreaks with hundreds of thousands of infection and removal events on a standard laptop. We apply the approach to incidence data from the Ebola outbreak in West Africa, where the susceptible population count is in the millions.

* * *
__Coupling + simulation for spatial birth-death-shift processes__ (_with Alfonso Landeros, Tim Stutz, Janet Sinsheimer, Ken Lange, Mary Sehl_)

<img src="https://jasonxu90.github.io/files/lattice.png " width="60%">


Motivated by the need for realistic stochastic modeling of tumor progression, we study the transient behavior of birth-death-shift processes on a lattice. Interacting particle systems with spatial dependence are extremely complex, but celebrated mathematical results concerning asymptotic behavior and phase transitions in such systems have limited use toward inference. We present new data structures that, together with tau-leaping algorithms, allow for efficient simulation of these lattice processes. We relate these methods to the more analytically tractable well-mixed case (no area interaction) via coupling arguments. These contributions together allow for numerical estimation of critical quantities such as first passage times and extinction probabilities.

[Back to homepage](./)

