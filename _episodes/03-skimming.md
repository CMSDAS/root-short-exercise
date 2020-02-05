---
title: "Step 1: Skim the initial datasets"
teaching: 5
exercises: 10
questions:
- "What happens in the skimming step?"
objectives:
- "Perform this step of the analysis by yourself"
keypoints:
- "We reduce the inital datasets by filtering suitable events and the selection of the interesting observables."
- "This step includes finding the interesting muon-tau pair in each selected event."
---

In this step, the NanoAOD files containing data and simulated events are pre-processed. This step is called skimming since the event selection reduces the size of the datasets significantly. In addition, we perform a pair selection to find from the muon and tau collections the pair which is most likely to have originated from a Higgs boson.

This step is implemented in the file `skim.cxx` and is written in C++ for performance reasons. To compile and run the program, use the script `skim.sh`. Note that you may need to change the compiler in the script based on your system.

If needed, initialize your CERN kerberos credentials to enable eos access:

```bash
kinit [your_CERN_username]@CERN.CH
```

Execute the following command to run the skimming:

```bash
bash skim.sh root://eospublic.cern.ch//eos/root-eos/HiggsTauTauReduced/ /output/dir/with/skims
```

In case you want to download the files first, for example if you want to run many times, execute the following two commands.

```bash
bash download.sh /input/dir/with/samples
bash skim.sh /input/dir/with/samples /output/dir/with/skims
```

The results of this step are files in `/output/dir/with/skims` with the suffix `*Skim.root`.

{% include links.md %}
