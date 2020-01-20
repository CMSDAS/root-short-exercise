---
title: "Physics background"
teaching: 15
exercises: 0
questions:
- "What is the physics behind the data?"
objectives:
- "Learn the basics of the physics processes present in the data"
keypoints:
- "Analysis studies Higgs boson decays to two tau leptons with a muon and a hadronic tau in the final state"
- "The analysis estimates all processes but QCD directly from simulation"
---

The following sections describe the relevant physics processes of the analysis.

## Signal process

The physical process of interest, also often called signal, is the production of the Higgs boson in the decay to two tau leptons. The main production modes of the Higgs boson are the gluon fusion and the vector boson fusion production indicated in the plots with the labels gg→H and qq→H, respectively. See below the two Feynman diagrams that describe the processes in leading order.

<div class="row">
  <div class="col-md-6">

    <img src="http://cms-results.web.cern.ch/cms-results/public-results/publications/HIG-13-004/CMS-HIG-13-004_Figure_001-a.png">

  </div>
  <div class="col-md-6">

    <img src="http://cms-results.web.cern.ch/cms-results/public-results/publications/HIG-13-004/CMS-HIG-13-004_Figure_001-b.png">

  </div>
</div>

## Tau decay modes

The tau lepton has a very short lifetime of about 290 femtoseconds after which it decays into other particles. With a probability of about 20% each, the tau lepton decays into a muon or an electron and two neutrinos. All other decay modes consist of a combination of hadrons such as pions and kaons and a single neutrino. You can find [here](http://pdg.lbl.gov/2019/tables/rpp2019-sum-leptons.pdf) a full overview and the exact numbers. This analysis considers only tau lepton pairs of which one tau lepton decays into a muon and two neutrinos and the other tau lepton hadronically, whereas [the official CMS analysis](http://cms-results.web.cern.ch/cms-results/public-results/publications/HIG-13-004/index.html) considered additional decay channels.

## Background processes

Besides the Higgs boson decaying into two tau leptons, many other processes can produce very similar signatures in the detector, which have to be taken into account to draw any conclusions from the data. In the following, the most prominent processes with a similar signature as the signal are presented. Besides the QCD multijet process, the analysis estimates the contribution of the background processes using simulated events.

### Z→ττ

The most prominent background process is the Z boson decaying into two tau leptons. The leading order production is called the Drell-Yan process in which a quark anti-quark pair annihilates. Because the Z boson decays such as the Higgs boson directly into two tau leptons, this process is very hard to distinguish from the signal.

### Z→ll

Besides the decay of the Z boson into two tau leptons, the Z boson decays with the same probability to electrons and muons. Although this process does not contain any genuine tau lepton, a tau can be reconstructed by mistake. Objects that are likely to be misidentified as a hadronic decay of a tau lepton are electrons or jets.

### W+jets

W bosons are frequently produced at the LHC and can decay into any lepton. If a muon from a W boson is selected together with a misidentified tau from a jet, a similar event signature as the signal can occur. However, this process can be strongly suppressed by a cut in the event selection on the transverse mass of the muon and the missing energy such as done in the published CMS analysis.

### tt¯

Top anti-top pairs are produced at the LHC by quark anti-quark annihilation or gluon fusion. Because a top quark decays immediately and almost exclusively via a W boson and a bottom quark, additional misidentifications result in signal-like signatures in the detector similar to the $W+\mathrm{jets}$ process explained above. However, the identification of jets originating from bottom quarks, and the subsequent removel of such events, is capable to reduce this background effectively.

### QCD

The QCD multijet background describes decays with a large number of jets, which occurs very often at the LHC. Such events can be falsely selected for the analysis due to misidentifications. Because a proper simulation of this process is complex and computational expensive, the contribution is not estimated from simulation but from data itself. Therefore, we select tau pairs with the same selection than the signal but with the changed requirement that both tau leptons have the same charge. Then, all known processes from simulation are subtracted from the histogram. Using the resulting histogram as estimation for the QCD multijet process is possible because the production of misidentified tau lepton candidates is independent from the charge.

{% include links.md %}
