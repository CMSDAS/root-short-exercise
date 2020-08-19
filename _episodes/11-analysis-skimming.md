---
title: "NanoAOD analysis: Skim the initial datasets"
teaching: 5
exercises: 5
questions:
- "How can I process large amounts of data efficiently?"
- "How does an analysis with RDataFrame looks like in C++?"
objectives:
- "Perform this step of the analysis by yourself"
keypoints:
- "We reduce the inital datasets by filtering suitable events and the selection of the interesting observables."
- "This step includes finding the interesting muon-tau pair in each selected event."
- "We use RDataFrame in C++ to perform the computational expensive part of the analysis as efficient as possible and enable the implicit multi-threading!"
---

In this step, the NanoAOD files containing data and simulated events are pre-processed. This step is called skimming since the event selection reduces the size of the datasets significantly. In addition, we perform a pair selection to find from the muon and tau collections the pair which is most likely to have originated from a Higgs boson.

This step is implemented in the file `skim.cxx` [here](../code/skim.cxx) and is written in C++ for performance reasons.

> ## Download the code and investigate the content!
> Download the file [`skim.cxx`](../code/skim.cxx) and investigate the content. You can easily follow the steps in the `main` function!
{: .challenge}

> ## Compile the C++ program!
> Compile the file [`skim.cxx`](../code/skim.cxx) to an executable!
{: .challenge}

> ## Compile the C++ program!
> Use the following command and replace `g++` with the C++ compiler of your choice.
> ```bash
> g++ -O3 -o skim skim.cxx $(root-config --cflags --libs)
> ```
{: .solution}

> ## Run the C++ program and investigate the output!
> Run it! Note that the program picks up the files from the same directory in which you run it. Also the results of this step are files in the same directory in which you have run the executable and have the filenames `*Skim.root`.
{: .challenge}

{% include links.md %}
