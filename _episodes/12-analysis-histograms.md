---
title: "NanoAOD analysis: Produce histograms"
teaching: 5
exercises: 5
questions:
- "How to produce many histograms efficiently?"
- "How does an analysis with `RDataFrame` look like in Python?"
objectives:
- "Produce all histograms required for the final plots"
- "Understand why we need so many histograms for a single plot"
keypoints:
- "We produce histograms of all physics processes and all observables."
- "All histograms are produced in a signal region with opposite-signed muon-tau pairs and in a control region with same-signed pairs for the data-driven QCD estimate"
- "This step shows the usage of RDataFrame in Python producing a large number of histograms in a single event loop and in parallel!"
---

> In the previous section, we produced skimmed datasets from the original files but still preserved information of selected quantities for each event. In this step, we compute histograms of these quantities for all skimmed datasets. Because of the data-driven QCD estimation, similar histograms have to be produced with the selection containing same-charged tau lepton pairs. This sums up to multiple hundreds of histograms which have to be combined into the final plots such as the ones shown in the next section.
{: .testimonial}

For convenience, this step is implemented in Python in the file `histograms.py`, which you can download [here](../code/histograms.py).

> ## Investigate and run the Python script!
> Have a look at [the code](../code/histograms.py) and run it! Note that the program picks up the files from the same directory in which you run it.
{: .challenge}

> ## Investigate the output!
> The script produces the file `histograms.root`, which contains the histograms. You can have a look at the plain histograms using for example the ROOT browser!
{: .challenge}

{% include links.md %}
