# The Roadmap for Targeted Learning {#intro}

## Learning Objectives

By the end of this chapter you will be able to:

1. Translate scientific questions to statistical questions.
2. Define a statistical model based on the knowledge of the experiment that
   generated the data.
3. Identify a causal parameter as a function of the observed data distribution.
4. Explain the following causal and statistical assumptions and their
   implications: i.i.d., consistency, interference, positivity, SUTVA.

## Introduction

The roadmap of statistical learning is concerned with the translation from
real-world data applications to a mathematical and statistical formulation of
the relevant estimation problem. This involves data as a random variable having
a probability distribution, scientific knowledge represented by a statistical
model, a statistical target parameter representing an answer to the question of
interest, and the notion of an estimator and sampling distribution of the
estimator.

## The Roadmap

Following the roadmap is a process of five stages.

1. Data as a random variable with a probability distribution, $O \sim P_0$.
2. The statistical model $\mathcal{M}$ such that $P_0 \in \mathcal{M}$.
3. The statistical target parameter $\Psi$ and estimand $\Psi(P_0)$.
4. The estimator $\hat{\Psi}$ and estimate $\hat{\Psi}(P_n)$.
5. A measure of uncertainty for the estimate $\hat{\Psi}(P_n)$.

### (1) Data as a random variable with a probability distribution, $O \sim P_0$ {-}

The data set we're confronted with is the result of an experiment and we can
view the data as a random variable, $O$, because if we repeat the experiment
we would have a different realization of this experiment. In particular, if we
repeat the experiment many times we could learn the probability distribution,
$P_0$, of our data. So, the observed data $O$ with probability distribution
$P_0$ are $n$ independent identically distributed (i.i.d.) observations of the
random variable $O; O_1, \ldots, O_n$. Note that while not all data are i.i.d.,
there are ways to handle non-i.i.d. data, such as establishing conditional
independence, stratifying data to create sets of identically distributed data,
etc. It is crucial that researchers be absolutely clear about what they actually
know about the data-generating distribution for a given problem of interest.
Unfortunately, communication between statisticians and researchers is often
fraught with misinterpretation. The roadmap provides a mechanism by which to
ensure clear communication between research and statistician -- it truly helps
with this communication!

#### The empirical probability measure, $P_n$ {-}

Once we have $n$ of such i.i.d. observations we have an empirical probability
measure, $P_n$. The empirical probability measure is an approximation of the
true probability measure $P_0$, allowing us to learn from our data. For
example, we can define the empirical probability measure of a set, $A$, to be
the proportion of observations which end up in $A$. That is,
\begin{equation*}
  P_n(A) = \frac{1}{n}\sum_{i=1}^{n} \mathbb{I}(O_i \in A)
\end{equation*}

In order to start learning something, we need to ask *"What do we know about the
probability distribution of the data?"* This brings us to Step 2.

### (2) The statistical model $\mathcal{M}$ such that $P_0 \in \mathcal{M}$ {-}

The statistical model $\mathcal{M}$ is defined by the question we asked at the
end of \ref{step1}. It is defined as the set of possible probability
distributions for our observed data. Often $\mathcal{M}$ is very large (possibly
infinite-dimensional), to reflect the fact that statistical knowledge is
limited. In the case that $\mathcal{M}$ is infinite-dimensional, we deem this a
nonparametric statistical model.

Alternatively, if the probability distribution of the data at hand is described
by a finite number of parameters, then the statistical model is parametric. In
this case, we prescribe to the belief that the random variable $O$ being
observed has, e.g., a normal distribution with mean $\mu$ and variance
$\sigma^2$. More formally, a parametric model may be defined
\begin{equation*}
  \mathcal{M} = \{P_{\theta} : \theta \in \mathcal{R}^d \}
\end{equation*}

Sadly, the assumption that the data-generating distribution has a specific,
parametric forms is all-too-common, even when such is a leap of faith. This
practice of oversimplification in the current culture of data analysis typically
derails any attempt at trying to answer the scientific question at hand; alas,
such statements as the ever-popular quip of Box that "All models are wrong but
some are useful," encourage the data analyst to make arbitrary choices even when
that often force significant differences in answers to the same estimation
problem. The Targeted Learning paradigm does not suffer from this bias since it
defines the statistical model through a representation of the true
data-generating distribution corresponding to the observed data.

Now, on to Step 3: *``What are we trying to learn from the data?"*

### (3) The statistical target parameter $\Psi$ and estimand $\Psi(P_0)$ {-}

The statistical target parameter, $\Psi$, is defined as a mapping from the
statistical model, $\mathcal{M}$, to the parameter space (i.e., a real number)
$\mathcal{R}$. That is, $\Psi: \mathcal{M}\rightarrow\mathbb{R}$. The target
parameter may be seen as a representation of the
quantity that we wish to learn from the data, the answer to a well-specified
(often causal) question of interest. In contrast to purely statistical target
parameters, causal target parameters require _identification from the observed
data_, based on causal models that include several untestable assumptions,
described in more detail in the section on [causal target parameters](#causal).

For a simple example, consider a data set which contains observations of a
survival time on every subject, for which our question of interest is "What's
the probability that someone lives longer than five years?" We have,
\begin{equation*}
  \Psi(P_0) = \mathbb{P}(O > 5)
\end{equation*}

This answer to this question is the **estimand, $\Psi(P_0)$**, which is the
quantity we're trying to learn from the data. Once we have defined $O$,
$\mathcal{M}$ and $\Psi(P_0)$ we have formally defined the statistical
estimation problem.

### (4) The estimator $\hat{\Psi}$ and estimate $\hat{\Psi}(P_n)$ {-}

To obtain a good approximation of the estimand, we need an estimator, an _a
priori_-specified algorithm defined as a mapping from the set of possible
empirical distributions, $P_n$, which live in a non-parametric statistical
model, $\mathcal{M}_{NP}$ ($P_n \in \mathcal{M}_{NP}$), to the parameter space
of the parameter of interest. That is, $\hat{\Psi} : \mathcal{M}_{NP} \rightarrow
\mathbb{R}^d$. The estimator is a function that takes as input
the observed data, a realization of $P_n$, and gives as output a value in the
parameter space, which is the **estimate, $\hat{\Psi}(P_n)$**.

Where the estimator may be seen as an operator that maps the observed data and
corresponding empirical distribution to a value in the parameter space, the
numerical output that produced such a function is the estimate. Thus, it is an
element of the parameter space based on the empirical probability distribution
of the observed data. If we plug in a realization of $P_n$ (based on a sample
size $n$ of the random variable $O$), we get back an estimate $\hat{\Psi}(P_n)$
of the true parameter value $\Psi(P_0)$.

In order to quantify the uncertainty in our estimate of the target parameter
(i.e., to construct statistical inference), an understanding of the sampling
distribution of our estimator will be necessary. This brings us to Step 5.

### (5) A measure of uncertainty for the estimate $\hat{\Psi}(P_n)$ {-}

Since the estimator $\hat{\Psi}$ is a function of the empirical
distribution $P_n$, the estimator itself is a random variable with a sampling
distribution. So, if we repeat the experiment of drawing $n$ observations we
would every time end up with a different realization of our estimate and our
estimator has a sampling distribution. The sampling distribution of an estimator
can be theoretically validated to be approximately normally distributed by a
Central Limit Theorem (CLT).

A class of __Central Limit Theorems__ (CLTs) are statements regarding the
convergence of the __sampling distribution of an estimator__ to a normal
distribution. In general, we will construct estimators whose limit sampling
distributions may be shown to be approximately normal distributed as sample size
increases. For large enough $n$ we have,
\begin{equation*}
  \hat{\Psi}(P_n) \sim N \left(\Psi(P_0), \frac{\sigma^2}{n}\right),
\end{equation*}
permitting statistical inference. Now, we can proceed to quantify the
uncertainty of our chosen estimator by construction of hypothesis tests and
confidence intervals. For example, we may construct a confidence interval at
level $(1 - \alpha)$ for our estimand, $\Psi(P_0)$:
\begin{equation*}
  \hat{\Psi}(P_n) \pm z_{1 - \frac{\alpha}{2}}
    \left(\frac{\sigma}{\sqrt{n}}\right),
\end{equation*}
where $z_{1 - \frac{\alpha}{2}}$ is the $(1 - \frac{\alpha}{2})^\text{th}$
quantile of the standard normal distribution. Often, we will be interested in
constructing 95% confidence intervals, corresponding to mass $\alpha = 0.05$ in
either tail of the limit distribution; thus, we will typically take
$z_{1 - \frac{\alpha}{2}} \approx 1.96$.

_Note:_ we will typically have to estimate the standard error,
$\frac{\sigma}{\sqrt{n}}$.

A 95\% confidence interval means that if we were to take 100 different samples
of size $n$ and compute a 95% confidence interval for each sample then
approximately 95 of the 100 confidence intervals would contain the estimand,
$\Psi(P_0)$. More practically, this means that there is a 95% probability
(or 95% confidence) that the confidence interval procedure will contain the
true estimand. However, any single estimated confidence interval either will
contain the true estimand or will not.

## Summary of the Roadmap

Data, $O$, is viewed as a random variable that has a probability distribution.
We often have $n$ units of independent identically distributed units with
probability distribution $P_0$ ($O_1, \ldots, O_n \sim P_0$). We have
statistical knowledge about the experiment that generated this data. In other
words, we make a statement that the true data distribution $P_0$ falls in a
certain set called a statistical model, $\mathcal{M}$. Often these sets are very
large because statistical knowledge is very limited so these statistical models
are often infinite dimensional models. Our statistical query is, "What are we
trying to learn from the data?" denoted by the statistical target parameter,
$\Psi$, which maps the $P_0$ into the estimand, $\Psi(P_0)$. At this point the
statistical estimation problem is formally defined and now we will need
statistical theory to guide us in the construction of estimators. There's a lot
of statistical theory we will review in this course that, in particular, relies
on the Central Limit Theorem, allowing us to come up with estimators that are
approximately normally distributed and also allowing us to come with statistical
inference (i.e., confidence intervals and hypothesis tests).

## Causal Target Parameters {#causal}

### The Causal Model

After formalizing the data and the statistical model, we can define a causal 
model to express causal parameters of interest. Directed acyclic graphs (DAGs) 
are one useful tool to express what we know about the causal relations among 
variables. Ignoring exogenous $U$ terms (explained below), we assume the 
following ordering of the variables in the observed data $O$.


```{=html}
<div id="htmlwidget-f24f61b14a52b30b1486" style="width:200px;height:300px;" class="visNetwork html-widget"></div>
<script type="application/json" data-for="htmlwidget-f24f61b14a52b30b1486">{"x":{"nodes":{"id":["W","A","Y"],"label":["W","A","Y"]},"edges":{"from":["W","W","A"],"to":["A","Y","Y"]},"nodesToDataframe":true,"edgesToDataframe":true,"options":{"width":"100%","height":"100%","nodes":{"shape":"dot"},"manipulation":{"enabled":false},"edges":{"arrows":{"to":true}},"layout":{"randomSeed":25}},"groups":null,"width":"200px","height":"300px","idselection":{"enabled":false},"byselection":{"enabled":false},"main":null,"submain":null,"footer":null,"background":"rgba(0, 0, 0, 0)"},"evals":[],"jsHooks":[]}</script>
```

While directed acyclic graphs (DAGs) like above provide a convenient means by 
which to visualize causal relations between variables, the same causal 
relations among variables can be represented via a set of structural equations, 
which define the non-parametric structural equation model (NPSEM):
\begin{align*}
  W &= f_W(U_W) \\
  A &= f_A(W, U_A) \\
  Y &= f_Y(W, A, U_Y),
\end{align*}
where $U_W$, $U_A$, and $U_Y$ represent the unmeasured exogenous background
characteristics that influence the value of each variable. In the NPSEM, $f_W$,
$f_A$ and $f_Y$ denote that each variable (for $W$, $A$ and $Y$, respectively)
is a function of its parents and unmeasured background characteristics, but note
that there is no imposition of any particular functional constraints(e.g.,
linear, logit-linear, only one interaction, etc.). For this reason, they are 
called non-parametric structural equation models (NPSEMs). The
DAG and set of nonparametric structural equations represent exactly the same
information and so may be used interchangeably.

The first hypothetical experiment we will consider is assigning exposure to the
whole population and observing the outcome, and then assigning no exposure to
the whole population and observing the outcome. On the nonparametric structural
equations, this corresponds to a comparison of the outcome distribution in the
population under two interventions:

1. $A$ is set to $1$ for all individuals, and
2. $A$ is set to $0$ for all individuals.

These interventions imply two new nonparametric structural equation models. For
the case $A = 1$, we have
\begin{align*}
  W &= f_W(U_W) \\
  A &= 1 \\
  Y(1) &= f_Y(W, 1, U_Y),
\end{align*}
and for the case $A=0$,
\begin{align*}
  W &= f_W(U_W) \\
  A &= 0 \\
  Y(0) &= f_Y(W, 0, U_Y).
\end{align*}

In these equations, $A$ is no longer a function of $W$ because we have
intervened on the system, setting $A$ deterministically to either of the values
$1$ or $0$. The new symbols $Y(1)$ and $Y(0)$ indicate the outcome variable in
our population if it were generated by the respective NPSEMs above; these are
often called _counterfactuals_ (since they run contrary-to-fact). The difference
between the means of the outcome under these two interventions defines a
parameter that is often called the "average treatment effect" (ATE), denoted
\begin{equation}\label{eqn:ate}
  ATE = \mathbb{E}_X(Y(1)-Y(0)),
\end{equation}
where $\mathbb{E}_X$ is the mean under the theoretical (unobserved) full data
$X = (W, Y(1), Y(0))$.

Note, we can define much more complicated interventions on NPSEM's, such as
interventions based upon rules (themselves based upon covariates), stochastic
rules, etc. and each results in a different targeted parameter and entails
different identifiability assumptions discussed below.

### Identifiability

Because we can never observe both $Y(0)$ (the counterfactual outcome when $A=0$)
and $Y(1)$ (similarly, the counterfactual outcome when $A=1$), we cannot
estimate \ref{eqn:ate} directly. Instead, we have to make assumptions under
which this quantity may be estimated from the observed data $O \sim P_0$ under
the data-generating distribution $P_0$. Fortunately, given the causal model
specified in the NPSEM above, we can, with a handful of untestable assumptions,
estimate the ATE, even from observational data. These assumptions may be
summarized as follows

1. The causal graph implies $Y(a) \perp A$ for all $a \in \mathcal{A}$, which
   is the _randomization_ assumption. In the case of observational data, the
   analogous assumption is _strong ignorability_ or _no unmeasured confounding_
   $Y(a) \perp A \mid W$ for all $a \in \mathcal{A}$;
2. Although not represented in the causal graph, also required is the assumption
   of no interference between units, that is, the outcome for unit $i$ $Y_i$ is
   not affected by exposure for unit $j$ $A_j$ unless $i=j$;
3. _Consistency_ of the treatment mechanism is also required, i.e., the outcome
   for unit $i$ is $Y_i(a)$ whenever $A_i = a$, an assumption also known as "no
   other versions of treatment";
4. It is also necessary that all observed units, across strata defined by $W$,
   have a bounded (non-deterministic) probability of receiving treatment --
   that is, $0 < \mathbb{P}(A = a \mid W) < 1$ for all $a$ and $W$). This assumption
   is referred to as _positivity_ or _overlap_.

_Remark_: Together, (2) and (3), the assumptions of no interference and
consistency, respectively, are jointly referred to as the *stable unit
treatment value assumption* (SUTVA).

Given these assumptions, the ATE may be re-written as a function of $P_0$,
specifically
\begin{equation}\label{eqn:estimand}
  ATE = \mathbb{E}_0(Y(1) - Y(0)) = \mathbb{E}_0
    \left(\mathbb{E}_0[Y \mid A = 1, W] - \mathbb{E}_0[Y \mid A = 0, W]\right),
\end{equation}
or the difference in the predicted outcome values for each subject, under the
contrast of treatment conditions ($A = 0$ vs. $A = 1$), in the population,
averaged over all observations. Thus, a parameter of a theoretical "full" data
distribution can be represented as an estimand of the observed data
distribution. Significantly, there is nothing about the representation in
\ref{eqn:estimand} that requires parameteric assumptions; thus, the regressions
on the right hand side may be estimated freely with machine learning. With
different parameters, there will be potentially different identifiability
assumptions and the resulting estimands can be functions of different components
of $P_0$. 

## The WASH Benefits Example Dataset

The data come from a study of the effect of water quality, sanitation, hand
washing, and nutritional interventions on child development in rural Bangladesh
(WASH Benefits Bangladesh): a cluster-randomised controlled trial
[@luby2018effects]. The study enrolled pregnant women in their first or second
trimester from the rural villages of Gazipur, Kishoreganj, Mymensingh, and
Tangail districts of central Bangladesh, with an average of eight women per
cluster. Groups of eight geographically adjacent clusters were block-randomised,
using a random number generator, into six intervention groups (all of which
received weekly visits from a community health promoter for the first 6 months
and every 2 weeks for the next 18 months) and a double-sized control group (no
intervention or health promoter visit). The six intervention groups were:

1. chlorinated drinking water;
2. improved sanitation;
3. hand-washing with soap;
4. combined water, sanitation, and hand washing;
5. improved nutrition through counseling and provision of lipid-based nutrient
   supplements; and
6. combined water, sanitation, handwashing, and nutrition.

In the workshop, we concentrate on child growth (size for age) as the outcome of
interest. For reference, this trial was registered with ClinicalTrials.gov as
NCT01590095.


```r
library(tidyverse)

# read in data
dat <- read_csv("https://raw.githubusercontent.com/tlverse/tlverse-data/master/wash-benefits/washb_data.csv")
dat
# A tibble: 4,695 × 28
    whz tr      fracode month  aged sex    momage momedu momheight hfiacat Nlt18
  <dbl> <chr>   <chr>   <dbl> <dbl> <chr>   <dbl> <chr>      <dbl> <chr>   <dbl>
1  0    Control N05265      9   268 male       30 Prima…      146. Food S…     3
2 -1.16 Control N05265      9   286 male       25 Prima…      149. Modera…     2
3 -1.05 Control N08002      9   264 male       25 Prima…      152. Food S…     1
4 -1.26 Control N08002      9   252 female     28 Prima…      140. Food S…     3
5 -0.59 Control N06531      9   336 female     19 Secon…      151. Food S…     2
# … with 4,690 more rows, and 17 more variables: Ncomp <dbl>, watmin <dbl>,
#   elec <dbl>, floor <dbl>, walls <dbl>, roof <dbl>, asset_wardrobe <dbl>,
#   asset_table <dbl>, asset_chair <dbl>, asset_khat <dbl>, asset_chouki <dbl>,
#   asset_tv <dbl>, asset_refrig <dbl>, asset_bike <dbl>, asset_moto <dbl>,
#   asset_sewmach <dbl>, asset_mobile <dbl>
```

For the purposes of this workshop, we we start by treating the data as independent
and identically distributed (i.i.d.) random draws from a very large target
population. We could, with available options, account for the clustering of the
data (within sampled geographic units), but, for simplification, we avoid these
details in these workshop presentations, although modifications of our
methodology for biased samples, repeated measures, etc., are available.

We have 28 variables measured, of which 1 variable is set to be the outcome of
interest. This outcome, $Y$, is the weight-for-height Z-score (`whz` in `dat`);
the treatment of interest, $A$, is the randomized treatment group (`tr` in
`dat`); and the adjustment set, $W$, consists simply of *everything else*. This
results in our observed data structure being $n$ i.i.d. copies of $O_i = (W_i,
A_i, Y_i)$, for $i = 1, \ldots, n$.

Using the [`skimr` package](https://CRAN.R-project.org/package=skimr), we can
quickly summarize the variables measured in the WASH Benefits data set:


Table: (\#tab:skim_washb_data)Data summary

|                         |     |
|:------------------------|:----|
|Name                     |dat  |
|Number of rows           |4695 |
|Number of columns        |28   |
|_______________________  |     |
|Column type frequency:   |     |
|character                |5    |
|numeric                  |23   |
|________________________ |     |
|Group variables          |None |


**Variable type: character**

|skim_variable | n_missing| complete_rate| min| max| empty| n_unique| whitespace|
|:-------------|---------:|-------------:|---:|---:|-----:|--------:|----------:|
|tr            |         0|             1|   3|  15|     0|        7|          0|
|fracode       |         0|             1|   2|   6|     0|       20|          0|
|sex           |         0|             1|   4|   6|     0|        2|          0|
|momedu        |         0|             1|  12|  15|     0|        3|          0|
|hfiacat       |         0|             1|  11|  24|     0|        4|          0|


**Variable type: numeric**

|skim_variable  | n_missing| complete_rate|   mean|    sd|     p0|    p25|   p50|    p75|   p100|hist  |
|:--------------|---------:|-------------:|------:|-----:|------:|------:|-----:|------:|------:|:-----|
|whz            |         0|          1.00|  -0.59|  1.03|  -4.67|  -1.28|  -0.6|   0.08|   4.97|▁▆▇▁▁ |
|month          |         0|          1.00|   6.45|  3.33|   1.00|   4.00|   6.0|   9.00|  12.00|▇▇▅▇▇ |
|aged           |         0|          1.00| 266.32| 52.17|  42.00| 230.00| 266.0| 303.00| 460.00|▁▂▇▅▁ |
|momage         |        18|          1.00|  23.91|  5.24|  14.00|  20.00|  23.0|  27.00|  60.00|▇▇▁▁▁ |
|momheight      |        31|          0.99| 150.50|  5.23| 120.65| 147.05| 150.6| 154.06| 168.00|▁▁▆▇▁ |
|Nlt18          |         0|          1.00|   1.60|  1.25|   0.00|   1.00|   1.0|   2.00|  10.00|▇▂▁▁▁ |
|Ncomp          |         0|          1.00|  11.04|  6.35|   2.00|   6.00|  10.0|  14.00|  52.00|▇▃▁▁▁ |
|watmin         |         0|          1.00|   0.95|  9.48|   0.00|   0.00|   0.0|   1.00| 600.00|▇▁▁▁▁ |
|elec           |         0|          1.00|   0.60|  0.49|   0.00|   0.00|   1.0|   1.00|   1.00|▆▁▁▁▇ |
|floor          |         0|          1.00|   0.11|  0.31|   0.00|   0.00|   0.0|   0.00|   1.00|▇▁▁▁▁ |
|walls          |         0|          1.00|   0.72|  0.45|   0.00|   0.00|   1.0|   1.00|   1.00|▃▁▁▁▇ |
|roof           |         0|          1.00|   0.99|  0.12|   0.00|   1.00|   1.0|   1.00|   1.00|▁▁▁▁▇ |
|asset_wardrobe |         0|          1.00|   0.17|  0.37|   0.00|   0.00|   0.0|   0.00|   1.00|▇▁▁▁▂ |
|asset_table    |         0|          1.00|   0.73|  0.44|   0.00|   0.00|   1.0|   1.00|   1.00|▃▁▁▁▇ |
|asset_chair    |         0|          1.00|   0.73|  0.44|   0.00|   0.00|   1.0|   1.00|   1.00|▃▁▁▁▇ |
|asset_khat     |         0|          1.00|   0.61|  0.49|   0.00|   0.00|   1.0|   1.00|   1.00|▅▁▁▁▇ |
|asset_chouki   |         0|          1.00|   0.78|  0.41|   0.00|   1.00|   1.0|   1.00|   1.00|▂▁▁▁▇ |
|asset_tv       |         0|          1.00|   0.30|  0.46|   0.00|   0.00|   0.0|   1.00|   1.00|▇▁▁▁▃ |
|asset_refrig   |         0|          1.00|   0.08|  0.27|   0.00|   0.00|   0.0|   0.00|   1.00|▇▁▁▁▁ |
|asset_bike     |         0|          1.00|   0.32|  0.47|   0.00|   0.00|   0.0|   1.00|   1.00|▇▁▁▁▃ |
|asset_moto     |         0|          1.00|   0.07|  0.25|   0.00|   0.00|   0.0|   0.00|   1.00|▇▁▁▁▁ |
|asset_sewmach  |         0|          1.00|   0.06|  0.25|   0.00|   0.00|   0.0|   0.00|   1.00|▇▁▁▁▁ |
|asset_mobile   |         0|          1.00|   0.86|  0.35|   0.00|   1.00|   1.0|   1.00|   1.00|▁▁▁▁▇ |

A convenient summary of the relevant variables is given just above, complete
with a small visualization describing the marginal characteristics of each
covariate. Note that the *asset* variables reflect socioeconomic status of the
study participants. Notice also the uniform distribution of the treatment groups
(with twice as many controls); this is, of course, by design.
