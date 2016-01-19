We thank the referee for their detailed and through feedback. In addressing their comments, we note that *Physical Review Letters* specifies the following criteria for acceptance:

> To maintain its mission of providing high-profile publication of important results in all areas of physics, PRL maintains strict acceptance criteria. In addition to being scientifically valid, published Letters must meet our criteria of impact, innovation, and interest by doing at least one of the following:
> 
> 1. Open a new area of research, or new avenues of research within an established area, and therefore significantly influence the research of others.
> 2. Solve, or make essential steps towards solving, a critical outstanding problem.
> 3. If presenting a new technique, or methodology, it should play a pivotal role in future physics research, and make apparent its immediate consequences for physicists.
> 4. In rare instances a Letter may also be of unusual intrinsic interest to our broad audience.

We maintain that our work satisfies all of the first three criteria, while our exposition in the previous version may not have adequately reflected this.  We feel that after following the referee’s comments that our work now clearly meets the requirements of a PRL. We explicitly discuss each of these three classes of contributions below.

First, our work opens up a new avenue of research within an established area by showing a new form of particle filter approximations that were previously unknown in the literature and provide a new platform for phase estimation and other tasks in quantum metrology. Our work significantly impacts the research of others, because our method does not rely on precomputed policies, but yields experiment designs on the fly for thousands of experiments, and requires such a small amount of memory that the entire inference process can be run in an FPGA. This opens up the possibility of new classes of quantum experiments that would have previously been impossible because of long latencies experienced when communicating with a control computer.

Our work also solves a critical outstanding problem, namely that of finding an iterative phase estimation algorithm that can be used to perform Shor’s algorithm in a memory limited environment without requiring exponential classical resources. This is not possible using existing optimized policies because of the exponential size of the decision tree.Furthermore, the online nature of our algorithm allows time-dependent parameters to be tracked in real time in a system while outputting an estimate of the uncertainty. This capability opens up new uses in online control of quantum systems by allowing phase estimation algorithms to identify time-dependent drift (potentially over millions of experiments). Such possibilities cannot be achieved using existing approaches.

Finally, our work will play a pivotal role in future research by revealing very simple, but highly effective methods for performing online phase estimation. As future experiments migrate to FPGAs, we are entering a new era of online experiments where the control hardware plays an active role in data acquisition. Our methods not only make this a possibility (for long experiments) but they also saturate the optimal $O(1/T)$ scaling reached by optimized methods. In addition to these capabilities, our method is *simple*; it can be programmed in under an hour by an undergraduate student, and does not require substantial study of optimization literature to apply successfully.
The simplicity of our algorithm sets it apart from particle swarm optimization or differential evolution. As such, our method will become a go to method for both for established researchers and for students entering the field. We strongly suspect that our method will help inspire future generations of particle filter methods for phase estimation that are optimized for online experiments.

Aside from the PRL criteria, we are glad that the referee agrees with the utility of our rejection filtering method to experimental practice, and in particular, to memory-limited and embedded computing platforms such as those based on FPGAs. We disagree, however, that the results presented in our manuscript overlap substantially with those already presented in literature. To this end, we have significantly clarified the presentation of our results to show how rejection filtering differs from traditional metrology applications, and offers something of value to quantum information processing. In particular, we have revised the introduction to emphasize the role of phase estimation in small quantum information processing devices, and to highlight the challenges in using traditional iterative phase estimation methods in Shor's algorithm.

In addition, we have also significantly expanded our manuscript, including the addition of new results (shown in our new Figure 3) that address the performance of our algorithm for very long experiments ($\sum M_i \approx 10^{100}$), where precomputation is simply not tenable as an experiment design strategy. In doing so, we further establish the utility of our method for QIP applications.

Below, we detail the changes we have made to the manuscript and respond to each point raised by the referee. With these revisions, we believe that our work will offer something of value to the physics community at-large, and to the readers of *Physical Review Letters* in particular.

> The authors present a new phase estimation algorithm based on Bayesian inference. Their work contributes both to the numerical implementation of Bayesian inference and, what has traditionally been in the focus of research, how the control parameters should be chosen in phase measurements.
> 
> One can distinguish three different components in the manuscript. First, the rules, i.e., the policy, through which to update the control parameters during the experiment. Second, a rejection filtering scheme that makes numerical implementation of Bayesian inference less memory intensive than the version of sequential Monte Carlo described, e.g., in [11]. A third component is a novel procedure to detect and correct faults in the estimation. Furthermore, the authors demonstrate the robustness of the algorithm in the presence of decoherence and in the presence of noise, even when the level of noise is unknown to the experimenter. It is also shown that the algorithm is suitable in estimating phase in real time when the phase may drift in time.
> 
> It is interesting that the rejection filtering scheme appears to also yield very accurate estimates since it can make Bayesian inference better compatible with memory-limited computing environments such as FPGAs. However, the algorithm to update measurement settings may have a limited impact on phase estimation over time since there exists relevant work on phase estimation beyond what is cited in the manuscript, and to a large degree similar results have been achieved earlier by other means. In my view the manuscript would therefore be better suited in Physical Review A.
> 
> I present detailed criticism, comments, and questions below.
> 
> 1) One of the main results of the manuscript is the policy for the presence of decoherence in Eq. (5). The achieved median error is plotted in Fig. 3. However, phase measurements in the presence of decoherence have also been studied, e.g., in R. S. Said, D. W. Berry, and J. Twamley, PRB B 83, 125410 (2011); P. Cappellaro, PRA 85, 030301 (2012) as well as in A. J. F. Hayes and D. W. Berry, PRA 89, 013838 (2014). The last paper also takes into account possible low visibility in the measurements which is not considered in the manuscript under review.

The results of Ferrie *et al.* 2012 (doi:10/tfx) characterize the effects on phase estimation (there discussed as estimating Larmor precession) of known but limited visibility. RFPE inherits this, such that we have focused on the perfect-visibility case for clarity, and have done so without loss of generality. Moreover, the particle guess heuristic (PGH) that we employ in this work has been shown to work well for visibilities as low as 10% (Wiebe *et al.* 2014 doi:10/tdk), such that there is no reason to expect that visibility presents a difficulty for rejection-filtering PE. We have revised our manuscript accordingly, and have emphasized the citation to Ferrie *et al.* 2012, as well as noted the independent result of Cappellaro 2012.

> With perfect visibility, the likelihood function of Eq. (6) in PRA 89, 013838 is equivalent to Eq. (5) of the manuscript. Comparing the results is not straightforward since PRA 89, 013838 considers mean squared error whereas the current manuscript presents median error and because of the differences in counting the resources.

We agree that the phase estimation likelihood function is well-motivated and well-studied, both by us and more broadly in literature. Indeed, we believe that this strengthens the case for our present work, as this body of work shows that the phase estimation likelihood is relevant to a wide range of applications. Our result extends this literature to consider phase estimation using an approximation of Bayesian inference that is easy to implement in memory-constrained experimental control platforms and that uses few measurements to accurately estimate the phase-estimation model.

As discussed in the revisions to our introduction, the difference in resource counting between much of the prior literature and our own manuscript stems from a difference in application; whereas Hayes and Berry 2014 consider cost models best-suited to metrology applications, we have evaluated RFPE in terms of cost models motivated by applications to quantum algorithms.

> But in principle one could either (i) combine the policy of Eq. (5) with the error correction procedure of p. 4 and evaluate the mean error or (ii) simply apply the policy of PRA 89, 013838 with perfect visibility and calculate the median error. Either way, it seems unlikely the new policy could significantly improve the old results. The green curve in the upper panel of Fig. 5 in PRA 89, 013838 already exhibits a Heisenberg-like scaling $V_H \sim N^{−2}$ (notation of that paper). At least, the authors have not quantified how much they could improve the precision of the estimates compared to existing results in the presence of decoherence, and in this case the burden of proof is on the authors.
> One of the merits of policy of Eq. (5) is that the updates of the measurement settings are faster to evaluate than with locally optimized settings. But the measurement settings of PRA 89, 013838 are also fast to evaluate once the policy is known. It is only finding an efficient policy where substantial computation time is required. 

In principle, one could indeed apply the policy of Hayes and Berry with perfect visibility, as suggested. This is neither necessary (our policy handles limited visibility well, as noted above), and does not solve the problem under study, however. Thus, we have refrained from doing so. In particular, by using the particle guess heuristic (PGH), we have avoided both an expensive precomputation, and the need to store large policy vectors on experimental control hardware. Moreover, because the PGH depends only on the current state of the algorithm, we do not need to know *a priori* how many samples we wish to collect, but can make this decision adaptively as well.
For instance, in our new Figure 3, we illustrate this by running our algorithm for $N = 2000$ experimental samples, beyond what is generally considered to be feasible with precomputed policies.

We have revised our manuscript to illustrate the advantages of our PGH heuristic (as adapted to RFPE) with respect to the precomputed decision trees of Hayes and Berry.

> 2)  In the absence of decoherence the authors propose the policy of Eq. (4). In Figs. 1 and 2 median error is compared to Kitaev’s work from the year 1996 and to information-theory phase estimation (ITPE). For ITPE reference is not given and its working has not been fully explained. But more importantly, there already exists methods to achieve Heisenberg scaling for the mean squared error. A review can be found in Berry et al., PRA 80, 052114 (2009) where this is shown in Fig. 2. More recent work were policies where found through machine learning is published in A. Hentschel and B. C. Sanders, PRL 104, 063603 (2010) as well as in A. Hentschel and B. C. Sanders, PRL 107, 233601 (2011). This also yields policies that are fast to execute. These results are only applicable with $N$ up to ~50 (notation of those papers), though.

As above, our result is significant not in that it approximately reaches the Cramér-Rao bound (more commonly known in physics as Heisenberg scaling), but that it does so without requiring large policy vectors such as those explored by the algorithm of Hentschel and Sanders 2010. Indeed, the difficulty of precomputation and the size of the resulting policies explain much of the $N \approx 50$ limit encountered by the works mentioned by the referee--- again referring to our new Figure 3, RFPE suffers no such immediate limitation.

> 3) On page 4, the step 3 of the reset rule states “After restart, continue as normal until $\sigma \le \Delta$ then set $\sigma$ and $\mu$ to those of the closest eigenvalue”. I did not understand this. If “eigenvalue” means the eigenvalue of $U$, it should be unknown. The definition of $\Delta$ is that “spectral gaps are promised to be at least $\Delta$”. But if spectral gaps are differences between (energy) eigenvalues and eigenvalues are unknown, $\Delta$ is also unknown. Also, it was not clear to me what lines in Algorithm 3 (Supplemental Material) would correspond to the step 3. In algorithm 3, $\Delta$ is not mentioned. Also, the text could present a motivation for why the number 5 is chosen in the condition CNT < 5.

Since our algorithm is an online inference method, we always have a model for the posterior distribution stored.  This means that as we track eigenphases through hundreds, or thousands of measurements, we retain the previous estimates of the eigenvalues that we've learned even if decoherence thermalizes the state.  Thus if the current model of a state ever is unambiguously one of the eigenstates that the algorithm has observed in a previous step then the posterior model that we should use is the best one ever found for that corresponding eigenstate.  Step 3 reflects this observation.

After modifying the paper, we felt that this aspect of the restart rule was of secondary importance so we relegated the description of that part of the algorithm to the supplemental material.  

Finally, we have added extra text explaining algorithm 3 and have replaced the hardcoded value of 5 with a user-specifiable variable as input.

> 4)  Page 1 of the main text states “Bayesian phase estimation, as introduced by Svore et al. [9], involves performing a set of experiments and then updating the prior distribution using Bayes’ rule.” But already much earlier papers involve performing a set of experiments and then updating the prior using Bayes’ rule. For instance D.W. Berry and H. M. Wiseman, PRL 85, 5098 (2000) and D. W. Berry, H. M. Wiseman, and J. K. Breslin, PRA 63, 053804 (2001). Many other papers also do this. A review from the year 2009 can be found in PRA 80, 052114. The authors must mean something more specific but it was not clear to me what do they mean.

We have added the suggested citations.

> 5) On page 1 of Supplemental Material it is stated that “We see in Figure 2 that this strategy of restarting substantially reduces the weights of the tails. In fact, the mean error in the inference falls from 0.0513 radians to $1.08×10^{-6}$ radians. This shows that this resetting strategy substantially reduce the probability of a large error occuring in the estimate of the eigenphase. To our knowledge, this data represents the first time that a heuristic method has been successful in reducing the mean error in frequency estimation to an acceptable level of uncertainty.” However, in M. P. V. Stenberg, Y. R. Sanders, and F. K. Wilhelm, PRL 113, 210404 (2014) the mean error of a heuristic method is reduced through an “outlier correction scheme”. Figure 4 exhibits the results for g that is equivalent to frequency when ωr is known (notation of that paper). Also in M. P. V. Stenberg, K. Pack, and F. K. Wilhelm, arXiv:1508.04412 it is shown how to reduce the mean error of the coherent state phase and amplitude through a similar outlier correction scheme.

We agree that other heuristics have been used to reduce mean errors in frequency estimation, and have changed the wording here to reflect that agreement. We disagree, however, that the results of Stenberg *et al.* 2014 and 2015 are similar heuristics. In particular, in Appendix D, we show that our reset rule can be derived from an external agent's first-principles reasoning about the state of a rejection filtering instance.

> 6) In Supplemental Material, Fig. 3 demonstrates robustness against uncharacterised noise. Robustness against uncharacterised noise was also demonstrated in PRL 113, 210404 (2014) in Fig. 3.

We acknowledge that the effect of $\gamma$ in this figure is similar to that studied by Stenberg *et al.* in PRL 113, 210404. As Stenberg *et al.* note in their introduction, however, robustness to uncharacterized sources of error is also a feature of our earlier works Ferrie and Granade 2014 (doi:10/tdj) and Wiebe *et al.* 2014 (doi:10/tdk) using the sequential Monte Carlo algorithm.
In particular, Ferrie and Granade considered errors in evaluating the likelihood function, Wiebe *et al.* show robustness to model errors, and Stenberg *et al.* show robustness to readout error and decoherence.

The role of Supplemental Figure 3 in our original manuscript was thus to indicate that in replacing sequential Monte Carlo by rejection filtering, the desirable feature of robustness to readout errors has not been lost. We have emphasized this in our revisions, and have added citations to these earlier works.

> 7) The circuit on page 1 could have a figure number and a caption. It could be stated explicitly that $H$ is the Hadamard operator and $Z$ a Pauli matrix. The formula $Z(M \theta) = e^{iM\theta Z}$ has been given but it has not been explained what $Z$ is on the right-hand side of the equality.

We have explicitly defined $H$, $M$ and $Z$ in our revisions.

> 8)  Page 4 states “This model is appropriate when the time required to implement the controlled operation $\Lambda(U)$ is long...” But the operation $\Lambda$ has not been defined. Is $\Lambda(U)$ the same as $U^M$ on page 1?

Though $\Lambda(U)$ is somewhat commonly used to denote the controlled application of $U$, we have revised our manuscript to be more explicit.
 
> 9) On page 4 it is stated “In fact, it has already been observed that Bayesian inference to can be used to learn to an arbitrary number of digits using M ≈ T2 for certain noise models [11] (at the price of degrading the algorithm’s performance).” As far as I can see, in [11] it was not observed how to find the frequency beyond what is plotted in the figures. Numerical issues (impoverishment etc.) might complicate the attempts to learn an arbitrary number of digits. Of course there is probably a workaround to overcome such issues but I do not think it was shown in [11] how to do it.

We agree that this language was unclear, and have removed it in revisions.

> 10) Page 2 states “The factor of 1.25 comes from optimizing the cost of RFPE.” How did the authors confirm the factor of 1.25 optimizes the cost of RFPE?

We did not intend to imply that 1.25 is optimal, and have changed the language in revisions to indicate that the value of 1.25 is one that works well for the experiments under consideration.

> 11) In Fig. 3 the curves continue up to the experiment number 10^3 but the axes extend to 10^4.
> 
> 12) In Supplemental Material, in Eq. (4) $j$ is used both as a subindex for the free variable $x_j$ on the left-hand side of the equality as well as as the dummy index in the sums on the right-hand side. It would be better to use different indices. 

We have made the suggested revision.

> 13) In Supplemental Material, Eq. (9) uses the concept of “prior correct” whereas in Eq. (10) it reads “prior right”. The same terminology could be used in both equations.

We have made the suggested revision.

> 14) In my opinion the authors would better put their work in context if they would add citations at least to the papers mentioned above.

We have added the majority of the suggested citations, as well as a few additional citations. As a result, we believe that our work is more correctly established in its context.
