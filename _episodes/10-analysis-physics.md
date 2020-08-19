---
title: "NanoAOD analysis: Introduction"
teaching: 10
exercises: 10
questions:
- "What am I supposed to learn from this analysis?"
- "What is the physics behind the data?"
objectives:
- "Learn the basics of the physics processes present in the data"
- "Learn about the content of the (reduced) NanoAOD files"
keypoints:
- "Analysis studies Higgs boson decays to two tau leptons with a muon and a hadronic tau in the final state"
- "The input files are (reduced) CMS NanoAOD, being very close to actual analysis in CMS"
- "The following steps will show in a hands-on the use of RDataFrame in an actual analysis"
---

> This section shows you how an analysis with CMS NanoAOD files and RDataFrame can be performed, from the inital files to the result plots.
{: .testimonial}

## Signal process

The physical process of interest, also often called signal, is the production of the Higgs boson in the decay to two tau leptons. The main production modes of the Higgs boson are the gluon fusion and the vector boson fusion production indicated in the plots with the labels gg→H and qq→H, respectively. See below the two Feynman diagrams that describe the processes at leading order.

<div class="row">
  <div class="col-md-6">

    <img src="http://cms-results.web.cern.ch/cms-results/public-results/publications/HIG-13-004/CMS-HIG-13-004_Figure_001-a.png" height="70%" width="70%">

  </div>
  <div class="col-md-6">

    <img src="http://cms-results.web.cern.ch/cms-results/public-results/publications/HIG-13-004/CMS-HIG-13-004_Figure_001-b.png" height="70%" width="70%">

  </div>
</div>

## Tau decay modes

The tau lepton has a very short lifetime of about 290 femtoseconds after which it decays into other particles. With a probability of about 20% each, the tau lepton decays into a muon or an electron and two neutrinos. All other decay modes consist of a combination of hadrons such as pions and kaons and a single neutrino. You can find [here](http://pdg.lbl.gov/2019/tables/rpp2019-sum-leptons.pdf) a full overview and the exact numbers. This analysis considers only tau lepton pairs of which one tau lepton decays into a muon and two neutrinos and the other tau lepton hadronically, whereas [the official CMS analysis](http://cms-results.web.cern.ch/cms-results/public-results/publications/HIG-13-004/index.html) considered additional decay channels.

## Background processes

Besides the Higgs boson decaying into two tau leptons, many other processes can produce very similar signatures in the detector, which have to be taken into account to draw any conclusions from the data. In the following, the most prominent processes with a similar signature as the signal are presented. Besides the QCD multijet process, the analysis estimates the contribution of the background processes using simulated events.

### Z→ττ

The most prominent background process is the Z boson decaying into two tau leptons. The leading order production is called the Drell-Yan process in which a quark anti-quark pair annihilates. Because the Z boson decays directly into two tau leptons, same as the Higgs boson, this process is very hard to distinguish from the signal.

### Z→ll

Besides the decay of the Z boson into two tau leptons, the Z boson decays with the same probability to electrons and muons. Although this process does not contain any genuine tau leptons, a tau can be reconstructed by mistake. Objects that are likely to be misidentified as a hadronic decay of a tau lepton are electrons or jets.

### W+jets

W bosons are frequently produced at the LHC and can decay into any lepton. If a muon from a W boson is selected together with a misidentified tau from a jet, a similar event signature as the signal can occur. However, this process can be strongly suppressed by a cut in the event selection on the transverse mass of the muon and the missing energy, as done in the published CMS analysis.

### tt¯

Top anti-top pairs are produced at the LHC by quark anti-quark annihilation or gluon fusion. Because a top quark decays immediately and almost exclusively via a W boson and a bottom quark, additional misidentifications result in signal-like signatures in the detector similar to the $W+\mathrm{jets}$ process explained above. However, the identification of jets originating from bottom quarks, and the subsequent removal of such events, is capable of reducing this background effectively.

### QCD

The QCD multijet background describes decays with a large number of jets, which occurs very often at the LHC. Such events can be falsely selected for the analysis due to misidentifications. Because a proper simulation of this process is complex and computational expensive, the contribution is not estimated from simulation but from data itself. Therefore, we select tau pairs with the same selection as the signal, but with the modified requirement that both tau leptons have the same charge. Then, all known processes from simulation are subtracted from the histogram. Using the resulting histogram as estimation for the QCD multijet process is possible because the production of misidentified tau lepton candidates is independent of the charge.

## Files and dataset content

The used files and the content of the datasets, for example [the simulated Standard Model Higgs boson produced by Gluon fusion](http://opendata.web.cern.ch/record/12351), can be found on [the CERN Open Data portal](http://opendata.web.cern.ch/record/12350).

> ## Have a look at the content of the (reduced) CMS NanoAOD files!
> You can just look at the content on the CERN Open Data portal (follow for example [this link](http://opendata.web.cern.ch/record/12351)) or take one of the files you will download below and investigate the content with ROOT, such as shown in the previous sections!
{: .challenge}

> ## Why NanoAOD?
> The NanoAOD format is a small version of the MiniAOD format (which is a small version of the AOD format) with a size of about 2 kB/Event. Going towards Run 3 and 4 of the LHC, this format will be very likely the default for most CMS analyses to be able to process an unprecedented amount of data!
{: .keypoints}

> ## Why *reduced* NanoAOD?
> Note that the used NanoAOD files are reduced versions recreated with open CMS data and simulation from 2012, but you will most likely not see any difference!
{: .checklist}

## Download the required datasets

Because very likely you will run the code multiple times, we want to speed up the analysis so that you can focus on the software. To do so, download with `xrdcp` the files on your computer or any other system with ROOT (v6.18 or later) available. The size of downloaded files sum up to about 6.5 GB and represent only 10% of the original files you can find on the Open Data portal, which enables you to run the full analysis in under five minutes.

Alternatively, you can download the files manually via HTTP from [https://root.cern/files/HiggsTauTauReduced/](https://root.cern/files/HiggsTauTauReduced/).

```bash
SAMPLES=(
    GluGluToHToTauTau
    VBF_HToTauTau
    DYJetsToLL
    TTbar
    W1JetsToLNu
    W2JetsToLNu
    W3JetsToLNu
    Run2012B_TauPlusX
    Run2012C_TauPlusX
    )

for SAMPLE in ${SAMPLES[@]}
do
    # Via XRootD:
    xrdcp root://eospublic.cern.ch//eos/root-eos/HiggsTauTauReduced/${SAMPLE}.root .
    # Via HTTP:
    # curl -O https://root.cern/files/HiggsTauTauReduced/${SAMPLE}.root
done
```

> ## Download the files!
> Choose one of the options shown above and download the files!
{: .challenge}

{% include links.md %}
