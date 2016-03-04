

# Second Report of Referee A -- LK14833/Wiebe #

> By emphasizing the simplicity of their method and its compatibility
> with memory limited environments, the authors have made their case for
> publication stronger and the revised manuscript could be suitable for
> Physical Review Letters. However, some issues still remain in the
> current version and those should be addressed before publication.
> 
> Below, the comment numbering follows that in my original report, so
> that the comments 15-20 point out new issues in the revised
> manuscript.
> 
> 4) In my first report, in comment 4, the reference Berry et al. PRA
> 80, 052114 was mentioned, and the authors replied “We have added the
> suggested citations.” However, the revised manuscript does not contain
> a citation to PRA 80, 052114.

We apologize for this oversight, and have addressed the issue.

> 6) In response to my comment 6 in my first report, the authors state
> “…robustness to uncharacterized sources of error is also a feature of
> our earlier works Ferrie and Granade 2014 (doi:10/tdj) and Wiebe *et
> al.* 2014 (doi:10/tdk) using the sequential Monte Carlo algorithm.”
> 
> In Supplemental material, the following sentence has been added “Our
> algorithm is not only robust against well-known depolarizing noise but
> is robust against uncharacterized noise sources as well. That is, by
> using rejection filtering, we retain the robustness previously shown
> for particle filtering in quantum information applications [4,6,7].”
> This sentence gives an impression that in [4], estimation in the
> presence of uncharacterized noise would have been studied. However, in
> [4] it was assumed that the strength of the noise is known. In [4],
> this is stated on page 7:
> 
> “The robustness of the learning algorithm to depolarizing noise arises
> similarly from the fact that a large number of particles are used in
> the SMC approximation, but also because of the fact that we assume
> that the strength of the depolarizing noise is known.”

The referee is correct that in the particular example that they quoted, the strength of the depolarizing noise was taken to be known, and moreover, that this provided the SMC approximation a large degree of robustness. In particular, we agree with the referee that we did not make clear the insight we drew from these citations, namely that SMC exhibits a large degree of robustness to violations of assumptions made at the level of models. In light of the referee's comments, we have clarified our wording here to emphasize that the robustness is intended to be against errors in the underlying likelihood function.

> 11) It appears the authors did not notice comment 11 of my first
> report “In Fig. 3 the curves continue up to the experiment number 10^3
> but the axes extend to 10^4.” The empty space in the current figure 4
> (on the right-hand side) should be cutted out.

We have made this change.

> 15) In the introduction, it is stated that “Our approach has several
> advantages compared to traditional methods: it is classically
> efficient, achieves Heisenberg limited scaling, resists depolarizing
> noise, tracks time dependent eigenstates, recovers from failures and
> can be run on a FPGA.” It is not clear what is meant by “traditional
> methods” and therefore the sentence can be misleading. For instance,
> is the method implemented in [2] traditional or not? At least it
> demonstrates Heisenberg-limited scaling and was simple enough to be
> experimentally realized in 2007. It would be more sensible to compare
> RFPE to *existing* rather than “traditional” methods.

We have changed the wording here, in accordance with the referee's suggestions.

> 16) In Reference [14], the PRA version is probably sufficient so that
> the arXiv version can be left out.

Though we tend to err on the side of providing more accessible citations rather than less, we have followed the referee's suggestion in this case.

> 17) In the reference list of the main text, there are references
> [30-35], but these have not been cited in the main text. Are these
> meant to be in the reference list of Supplemental material only or
> should there be citations to these in the main text?

All references in the main text of our revised manuscript are cited within the main text. We thank the referee for pointing out this issue.

> 18) In Supplemental material, on page 1, in the sentence “ This
> protocol is taken in Figure ?? wherein…” the correct figure number is
> missing (it has been replaced by question marks).

The reference to the figure has been corrected.

> 19) For reference [29], rather than the arXiv version, it would be
> better to cite the version published in PRA 92, 042303 (2015).
> 
> 20) For reference [33] in the main text and [7] in Supplemental
> material, rather than the arXiv version, it would be better to cite
> the version published in PRL 113, 210404 (2014).

We have updated these references.

# Report of Referee B -- LK14833/Wiebe #

> Bayesian methods for, estimation and discrimination, have a long
> history in quantum theory going back (at least) to the 1970s. In the
> 1990s and early 2000s there was a flurry of work on parameter
> estimation, tomography etc that used Bayesian methods.
> 
> Defining features of those works were: applicable to small scale
> systems (of order one spin, or one optical phase); "the algorithms" /
> "policies" developed were not scalable to larger systems or large data
> sets (# of experimental trials) say greater than a hundred data
> points; usually ignored imperfections (imperfect state preparation,
> decoherence, measurement imperfections); and assuming that the
> parameters to be estimated were static or quasi static.
> 
> Wiebe, Granade and collaborators have, over the last few years,
> embarked on a program to make Bayesian estimation practical for
> quantum systems. In particular they have focused on implementing and
> proposing methods which are scalable to moderate sized quantum systems
> and to large data sets without the restrictions above.
> 
> I read the paper twice and the supplemental material once. Then I read
> the previous referees report and the authors response. I agree with
> many of the previous referees points. But contrary to the previous
> referee, I think the paper is suitable for PRL for the reasons given
> above. I believe that three of PRL criteria are met by this article to
> a greater or lesser extent depending on the specific criteria.
> 
> However I think the authors need to make the case, in their
> manuscript, so that non expert readers can understand the advance. I
> suggest the authors read carefully the first referee's second
> paragraph, ie.
> 
> "One can distinguish three different components in the manuscript.
> First, the rules, i.e., the policy, through which to update the
> control parameters during the experiment. Second, a rejection
> filtering scheme that makes numerical implementation of Bayesian
> inference less memory intensive than the version of sequential Monte
> Carlo described, e.g., in [11]. A third component is a novel procedure
> to detect and correct faults in the estimation. Furthermore, the
> authors demonstrate the robustness of the algorithm in the presence of
> decoherence and in the presence of noise, even when the level of noise
> is unknown to the experimenter. It is also shown that the algorithm is
> suitable in estimating phase in real time when the phase may drift in
> time.";
> 
> the points I raised above; and the authors own response to the first
> referee (arguing that their work meets the PRL criteria). Then modify
> the introduction and abstract to clearly explain the advances their
> work makes.

We thank the referee for their assessment, and have taken efforts to make our case more clearly in our current revisons. In particular, we have implemented the referee's suggestions (below), and have reworded much of our introduction to more clearly identify the contributions made by our manuscript. We believe that by mentioning all three of our contributions explicitly in our new introduction, our work should be significantly more accessible to expert and non-expert readers alike, and should elucidate the advantages of rejection filtering phase estimation.

> Small suggestions: * Below the circuit diagram the controlled unitary
> is not explained neither is the "/" . Remember PRL will have non
> expert readers, so these should probably be explained.
> 
> * Be kind to the reader and reduce the number of acronyms. Perhaps the
> authors could consider keeping ITPE, RFPE, and FPGA but removing PE,
> IPE, RF, and PGH. The latter acronyms are rarely used and thus would
> not lengthen the manuscript too much.
> 
> *Consider appropriately citing the relevant work by Giedke et al
> "Quantum measurement of a mesoscopic spin ensemble" Phys. Rev. A 74,
> 032316 (2006)

We have cited this work and also clarified the circuit diagram along with providing a reference to Nielsen and Chuang for the non-expert.