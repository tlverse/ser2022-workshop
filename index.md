---
knit: "bookdown::render_book"
title: "[SER 2022 Workshops] Targeted Learning I and II"
subtitle: "Causal Inference Meets Machine Learning and Advanced Applications of Causal Inference"
author: "Mark van der Laan, Alan Hubbard, Jeremy Coyle, Nima Hejazi, Ivana
  Malenica, Rachael Phillips"
date: "updated: June 13, 2022"
documentclass: book
site: bookdown::bookdown_site
bibliography: [book.bib, packages.bib]
biblio-style: apalike
fontsize: '12pt, krantz2'
monofontoptions: "Scale=0.7"
link-citations: yes
colorlinks: yes
lot: yes
lof: yes
always_allow_html: yes
url: 'https\://tlverse.org/ser2022-workshop/'
github-repo: tlverse/ser2022-workshop
graphics: yes
description: "Open source, reproducible teaching materials accompanying two 
  half-day workshops on Targeted Learning with the 
  [`tlverse`](https://github.com/tlverse)."
---

# Welcome! {-}

This open source, reproducible vignette is for two half-day workshops at the 
Society for Epidemiologic Research Meeting on June 14, 2022. Beyond introducing 
Targeted Learning (TL), these workshops focus on applying the methodology in 
practice using the [`tlverse` software ecosystem](https://github.com/tlverse). 
These materials are based on a working draft of the book [*Targeted 
Learning in `R`: Causal Data Science with the `tlverse` Software 
Ecosystem*](https://tlverse.org/tlverse-handbook/), which includes in-depth 
discussion of these topics and much more, and may serve as a useful reference 
to accompany these workshop materials.

<img style="float: center; margin-right: 1%; margin-bottom: 0.01em"
     src="img/logos/tlverse-logo.svg" width="30%" height="30%">
<img style="float: center; margin-right: 1%; margin-bottom: 0.01em"
     src="img/logos/Rlogo.svg" width="35%" height="35%">
<img style="float: center; margin-right: 1%; margin-bottom: 0.01em"
     src="img/logos/vdl-logo-transparent.svg" width="30%" height="30%">
<p style="clear: both;">
<br>

## Important links {-}

* **`R` version 4.2.0+**: Install `R` or update to the most recent major version 
  of `R` (which is 4.2.0+): https://cloud.r-project.org. For more operating 
  system-specific instructions, please see the [setup 
  instructions](https://tlverse.org/ser2022-workshop/tlverse.html#setup) below.
* **`R` packages**: Please try to set up the `R` virtual environment 
  before the day of the workshop by following these 
  [instructions](https://github.com/tlverse/ser2022-workshop/blob/master/install.md).
  If you are experiencing issues or if this is your first time using `renv`, 
  this introduction to the package might be 
  helpful: https://rstudio.github.io/renv/articles/renv.html. As an alternative
  to the virtual environment, you can install the relevant software packages 
  instead using this [install `R` 
  script](https://github.com/tlverse/ser2022-workshop/blob/master/install.R).
* __Installation errors__: You will probably exceed the GitHub API rate limit 
  during the installation, which will throw an error. This issue and a solution 
  are addressed 
  here: https://tlverse.org/ser2022-workshop/tlverse.html#installtlverse. 
* __Code__: `R` script files for each section of the workshop are available in
  the "R_code" folder in the GitHub repository for the workshop:
  https://github.com/tlverse/ser2022-workshops/tree/master/R_code. 
* __Slides__: Any slide decks are available in the "slides" folder in the 
  GitHub repository for the workshop: 
  https://github.com/tlverse/ser2022-workshops/tree/master/slides.
## About {-}

### Targeted Learning I: Causal Inference Meets Machine Learning (8:30A--12:00P) {-}
This workshop will provide an introduction to the field of targeted learning for 
causal inference, and the corresponding [`tlverse` software 
ecosystem](https://github.com/tlverse). Emphasis will be placed on targeted 
minimum loss-based estimation (TMLE) of causal effects under single time point 
interventions, including extensions for missing covariates and outcomes. These 
multiply robust, efficient plug-in estimators use state-of-the-art machine 
learning tools to flexibly adjust for confounding while yielding valid 
statistical inference. In addition to discussion, this workshop will incorporate 
both interactive activities and hands-on, guided `R` programming exercises, to 
allow participants the opportunity to familiarize themselves with methodology 
and tools that translate to real-world data analysis. It is highly recommended 
for participants to have an understanding of basic statistical concepts such as 
confounding, probability distributions, confidence intervals, hypothesis 
testing, and regression. Advanced knowledge of mathematical statistics is 
useful but not necessary. Familiarity with the `R` programming language will be 
essential.

### Targeted Learning II: Advanced Applications of Causal Inference (1:00--4:00P) {-}
Building on an introduction to targeted learning and its software ecosystem, 
the [`tlverse`](https://github.com/tlverse), this workshop serves as a 
walkthrough of its use for estimation of advanced parameters motivated by 
causal inference. In particular, we will discuss targeted estimators of the 
causal effects of dynamic, optimal dynamic, and stochastic interventions; time 
permitting, estimation of the effects of interventions in settings with 
time-to-event (survival) outcomes may also be discussed. Throughout, we will 
draw on advanced uses of machine learning, including conditional density 
estimation and categorical outcome prediction, highlighting the extensibility 
of the `tlverse`. In addition to discussion, this workshop will incorporate both 
interactive activities and hands-on, guided `R` programming exercises, to allow 
participants the opportunity to familiarize themselves with methodology and 
tools that translate to real-world data analysis. It is highly recommended for 
participants to have an understanding of basic statistical concepts such as 
confounding, probability distributions, confidence intervals, hypothesis 
testing, and regression. Advanced knowledge of mathematical statistics is 
useful but not necessary. Familiarity with the `R` programming language will be 
essential. Prior experience with the `tlverse` (as covered in the SER workshop 
"Targeted Learning I") is highly recommended.

## Schedule {-}

* 08:30--9:40A: Introduction to Targeted Learning by Alan (slide deck 
  here: https://github.com/tlverse/ser2022-workshop/tree/master/slides/intro.pdf) 
* 09:40--10:00A: Introduction to the [`tlverse`](#tlverse) and [`R6`](#r6) by 
  Rachael
* 10:00--10:40A: Super learning in the `tlverse` with the [`sl3` `R`
  package](https://github.com/tlverse/sl3) by Rachael
* 10:40--11:00A: Programming exercises with `sl3`
* 11:00--11:40A: Targeted minimum loss-based estimation in the `tlverse` with 
  the [`tmle3` `R` package](https://github.com/tlverse/tmle3) by Alan and Ivana
* 11:40A--12:00P: Programming exercises with `tmle3`
* 12:00--01:00P: Lunch Break
* 01:00--02:00P: Optimal treatment regimes with the [`tmle3mopttx` `R`
  package](https://github.com/tlverse/tmle3mopttx) by Ivana
* 02:00-02:30P: Programming exercises with `tmle3mopttx`
* 02:30-03:30P: Stochastic treatment regimes with the [`tmle3shift` `R`
  package](https://github.com/tlverse/tmle3shift) by Nima
* 03:30-04:00P: Programming exercises with `tmle3shift`

NOTE: All listings are in Central Time.

## About the instructors {-}

### Alan Hubbard {-}

Alan Hubbard is Professor of Biostatistics, former head of the Division of
Biostatistics at UC Berkeley, and head of data analytics core at UC Berkeley's
SuperFund research program. His current research interests include causal
inference, variable importance analysis, statistical machine learning,
estimation of and inference for data-adaptive statistical target parameters, and
targeted minimum loss-based estimation. Research in his group is generally
motivated by applications to problems in computational biology, epidemiology,
and precision medicine.

### Nima Hejazi {-}

[Nima Hejazi](https://nimahejazi.org), PhD, is an incoming Assistant Professor
of Biostatistics at the [Harvard T.H. Chan School of Public
Health](https://www.hsph.harvard.edu/biostatistics/). He received his PhD in
biostatistics at UC Berkeley, working under the supervision of Mark van der Laan
and Alan Hubbard, and afterwards held an NSF postdoctoral research fellowship.
Nima's research interests blend causal inference, machine learning,
semiparametric estimation, and computational statistics -- areas of recent
emphasis include causal mediation analysis, efficiency under biased sampling
designs, non/semi-parametric sieve estimation with machine learning, and
targeted loss-based estimation. His work is primarily driven by applications in
clinical trials (esp. vaccine efficacy trials), infectious disease epidemiology,
and computational biology. Nima is passionate about statistical computing
and open source software design standards for statistical data science, and he
has co-led or contributed significantly to many `tlverse` packages (`hal9001`,
`sl3`, `tmle3`, `origami`, `tmle3shift`, `tmle3mediate`).

### Ivana Malenica {-}

Ivana Malenica is a PhD student in biostatistics advised by Mark van der Laan.
Ivana is currently a fellow at the Berkeley Institute for Data Science, after
serving as a NIH Biomedical Big Data and Freeport-McMoRan Genomic Engine fellow.
She earned her Master's in Biostatistics and Bachelor's in Mathematics, and
spent some time at the Translational Genomics Research Institute. Very broadly,
her research interests span non/semi-parametric theory, probability theory,
machine learning, causal inference and high-dimensional statistics. Most of her
current work involves complex dependent settings (dependence through time and
network) and adaptive sequential designs.

### Rachael Phillips {-}

Rachael Phillips is a PhD student in biostatistics, advised by Alan Hubbard and
Mark van der Laan. She has an MA in Biostatistics, BS in Biology, and BA in
Mathematics. As a student of targeted learning, Rachael integrates causal 
inference, machine learning, and statistical theory to answer causal questions 
with statistical confidence. She is motivated by issues arising in healthcare, 
and is especially interested in clinical algorithm frameworks and guidelines. 

### Mark van der Laan {-}

Mark van der Laan, PhD, is Professor of Biostatistics and Statistics at UC
Berkeley. His research interests include statistical methods in computational
biology, survival analysis, censored data, adaptive designs, targeted maximum
likelihood estimation, causal inference, data-adaptive loss-based learning, and
multiple testing. His research group developed loss-based super learning in
semiparametric models, based on cross-validation, as a generic optimal tool for
the estimation of infinite-dimensional parameters, such as nonparametric density
estimation and prediction with both censored and uncensored data. Building on
this work, his research group developed targeted maximum likelihood estimation
for a target parameter of the data-generating distribution in arbitrary
semiparametric and nonparametric models, as a generic optimal methodology for
statistical and causal inference. Most recently, Mark's group has focused in
part on the development of a centralized, principled set of software tools for
targeted learning, the `tlverse`. Unfortunately, Mark is not able to attend 
SER 2022 in person. 

### Jeremy Coyle {-}

Jeremy Coyle, PhD, is a consulting data scientist and statistical programmer,
currently leading the software development effort that has produced the
`tlverse` ecosystem of `R` packages and related software tools. Jeremy earned his
PhD in Biostatistics from UC Berkeley in 2016, primarily under the supervision
of Alan Hubbard. Unfortunately, Jeremy is not able to attend SER 2022 in person. 


## Reproduciblity with the `tlverse` {#repro} {-}

The `tlverse` software ecosystem is a growing collection of packages, several of
which are quite early on in the software lifecycle. The team does its best to
maintain backwards compatibility. Once this work reaches completion, the
specific versions of the `tlverse` packages used will be archived and tagged to
produce it.

This book was written using [bookdown](http://bookdown.org/), and the complete
source is available on [GitHub](https://github.com/tlverse/tlverse-handbook).
This version of the book was built with R version 4.2.0 (2022-04-22),
[pandoc](https://pandoc.org/) version 2.7.3, and the
following packages:


|package      |version    |source                                                                  |
|:------------|:----------|:-----------------------------------------------------------------------|
|bookdown     |0.26.3     |Github (rstudio/bookdown\@169c43b6bb95213f2af63a95acd4e977a58a3e1f)     |
|bslib        |0.3.1.9000 |Github (rstudio/bslib\@a4946a49499438e71dce29c810a41e2d05170376)        |
|data.table   |1.14.2     |CRAN (R 4.2.0)                                                          |
|delayed      |0.3.0      |CRAN (R 4.2.0)                                                          |
|devtools     |2.4.3      |CRAN (R 4.2.0)                                                          |
|downlit      |0.4.0      |CRAN (R 4.2.0)                                                          |
|dplyr        |1.0.9      |CRAN (R 4.2.0)                                                          |
|ggplot2      |3.3.6      |CRAN (R 4.2.0)                                                          |
|here         |1.0.1      |CRAN (R 4.2.0)                                                          |
|kableExtra   |1.3.4      |CRAN (R 4.2.0)                                                          |
|knitr        |1.39       |CRAN (R 4.2.0)                                                          |
|mvtnorm      |1.1-3      |CRAN (R 4.2.0)                                                          |
|origami      |1.0.5      |Github (tlverse/origami\@e1b8fe6f5e75fff1d48eed115bb81475c9bd506e)      |
|readr        |2.1.2      |CRAN (R 4.2.0)                                                          |
|rmarkdown    |2.14       |CRAN (R 4.2.0)                                                          |
|skimr        |2.1.4      |CRAN (R 4.2.0)                                                          |
|sl3          |1.4.5      |Github (tlverse/sl3\@de445c210eefa5aa9dd4c0d1fab8126f0d7c5eeb)          |
|stringr      |1.4.0      |CRAN (R 4.2.0)                                                          |
|tibble       |3.1.7      |CRAN (R 4.2.0)                                                          |
|tidyr        |1.2.0      |CRAN (R 4.2.0)                                                          |
|tidyverse    |1.3.1      |CRAN (R 4.2.0)                                                          |
|tmle3        |0.2.0      |Github (tlverse/tmle3\@ed72f8a20e64c914ab25ffe015d865f7a9963d27)        |
|tmle3mediate |0.0.3      |Github (tlverse/tmle3mediate\@70d1151c4adb54d044f355d06d07bcaeb7f8ae07) |
|tmle3mopttx  |1.0.0      |Github (tlverse/tmle3mopttx\@c8c675f051bc5ee6d51fa535fe6dc80791d4d1b7)  |
|tmle3shift   |0.2.0      |Github (tlverse/tmle3shift\@4ed52b50af501a5fa2e6257b568d17fd485d3f42)   |

## `R` and RStudio setup instructions {#setup} {-}

`R` and RStudio are separate downloads and installations. `R` is the
underlying statistical computing environment. RStudio is a graphical integrated
development environment (IDE) that makes using `R` much easier and more
interactive. You need to install `R` before you install RStudio.

### Windows {-}

#### If you already have `R` and RStudio installed

* Open RStudio, and click on "Help" > "Check for updates". If a new version is
  available, quit RStudio, and download the latest version for RStudio.
* To check which version of `R` you are using, start RStudio and the first thing
  that appears in the console indicates the version of `R` you are
  running. Alternatively, you can type `sessionInfo()`, which will also display
  which version of `R` you are running. Go on the [CRAN
  website](https://cran.r-project.org/bin/windows/base/) and check whether a
  more recent version is available. If so, please download and install it. You
  can [check 
  here](https://cran.r-project.org/bin/windows/base/rw-FAQ.html#How-do-I-UNinstall-R_003f)
  for more information on how to remove old versions from your system if you
  wish to do so.

#### If you don't have `R` and RStudio installed

* Download `R` from
  the [CRAN website](http://cran.r-project.org/bin/windows/base/release.htm).
* Run the `.exe` file that was just downloaded.
* Go to the [RStudio download 
  page](https://www.rstudio.com/products/rstudio/download/#download).
* Under *Installers* select **RStudio x.yy.zzz - Windows XP/Vista/7/8** (where 
  x, y, and z represent version numbers).
* Double click the file to install it.
* Once it's installed, open RStudio to make sure it works and you don't get any
  error messages.

### macOS / Mac OS X {-}

#### If you already have `R` and RStudio installed

* Open RStudio, and click on "Help" > "Check for updates". If a new version is
  available, quit RStudio, and download the latest version for RStudio.
* To check the version of `R` you are using, start RStudio and the first thing
  that appears on the terminal indicates the version of `R` you are running.
  Alternatively, you can type `sessionInfo()`, which will also display which
  version of `R` you are running. Go on the [CRAN
  website](https://cran.r-project.org/bin/macosx/) and check whether a more
  recent version is available. If so, please download and install it.

#### If you don't have `R` and RStudio installed

* Download `R` from
  the [CRAN website](http://cran.r-project.org/bin/macosx).
* Select the `.pkg` file for the latest `R` version.
* Double click on the downloaded file to install `R`.
* It is also a good idea to install [XQuartz](https://www.xquartz.org/) (needed
  by some packages).
* Go to the [RStudio download
  page](https://www.rstudio.com/products/rstudio/download/#download).
* Under *Installers* select **RStudio x.yy.zzz - Mac OS X 10.6+ (64-bit)**
  (where x, y, and z represent version numbers).
* Double click the file to install RStudio.
* Once it's installed, open RStudio to make sure it works and you don't get any
  error messages.

### Linux {-}

* Follow the instructions for your distribution from 
  [CRAN](https://cloud.r-project.org/bin/linux); they provide information
  to get the most recent version of `R` for common distributions. For most
  distributions, you could use your package manager (e.g., for Debian/Ubuntu run 
  `sudo apt-get install r-base`, and for Fedora `sudo yum install R`), but we
  don't recommend this approach as the versions provided by this are
  usually out of date. In any case, make sure you have at least `R` 4.2.0.
* Go to the [RStudio download
  page](https://www.rstudio.com/products/rstudio/download/#download).
* Under *Installers* select the version that matches your distribution, and
  install it with your preferred method (e.g., with Debian/Ubuntu `sudo dpkg -i
  rstudio-x.yy.zzz-amd64.deb` at the terminal).
* Once it's installed, open RStudio to make sure it works and you don't get any
  error messages.

These setup instructions are adapted from those written for [Data Carpentry: `R`
for Data Analysis and Visualization of Ecological
Data](http://www.datacarpentry.org/R-ecology-lesson/).