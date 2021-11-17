Sorry about the late response, but hopefully this will be helpful in the future.

I think the optimal approach varies a descent amount by discipline, so I'll
target my advice for applied machine learning/alignment research, though I
think the ideas are somewhat similar for more theoretical CS research in general.

Overall, the goal is to optimize for extracting maximum value of information
per unit time (as with all epistemic activities, see also [this approach to
research/high uncertainty activities](rsdp)). 

Next, it's worth noting that academic papers aren't typically well optimized
for maximizing value for information per unit time (compare to distill for
example).

(Aside: This is actually a really hard task in general because of differing
reader backgrounds, though it is possible to do better by having multiple paths
like [this explanation of Bayes Theorem](a_bayes). Even given the difficulty,
academic papers still kinda suck.)

Given how poorly optimized they are, the optimal approach isn't just to read
start to end and is probably very non-linear in general. The biggest gains in
time can often come from quickly determining you shouldn't read a
paper/section/paragraph/proof.

I typically use a (reasonably standard) multi pass approach which looks
something like this:
- 0th pass: try to understand what paper accomplishes and figure out how much
  I should care.  

  This is often best done by reading the abstract and looking at graphs and/or
  samples.  If there is a blog post or other summary, that's often better than
  the abstract.  I also try to figure out what my key uncertainties about the
  paper are and how much I should care.  At this point, you need to figure out
  how much if you should read more and if so, how much detailed your reading
  should be.  Additionally, its good to think a bit about how to quickly
  address your uncertainties and which sections are likely to be important.

  It might be helpful to write down your key uncertainties.

  Check if there are any uncertainties for which resolving them could reduce
  how much you care or change which sections seem important to read. If there
  are any, it can be a good idea to focus on these first so that you can quit
  earlier or be more optimal in general.

- 1st pass: skim intro, look at figures, look at headings, skim/read methods,
  skim results, glance at equations (mostly checking for recognition), skim
  results/conclusion.

  I find most value typically is in the methods and trying to assess the
  results. So I often read the methods in more detail and spend some amount of
  time looking through graphs and figures in the results.

- 2nd pass: read important sections, possibly in detail and potentially skim
  other less important sections.
- 3nd pass: reread sections at necessary in as much detail as necessary.
  Potentially start reading through proof/algorithms in some detail (if
  applicable). Repeat as needed.
- א pass: reimplement and potentially extend the paper.
 

 [rsdp]: https://cs.stanford.edu/~jsteinhardt/ResearchasaStochasticDecisionProcess.html
 [a_bayes]: https://arbital.com/p/bayes_rule
