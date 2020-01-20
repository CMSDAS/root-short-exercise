---
title: "Introduction"
teaching: 10
exercises: 0
questions:
- "What is the purpose if this analysis?"
objectives:
- "Understand why we prepared for you this example analysis"
- "Understand what the analysis is doing"
keypoints:
- "Example analysis used as common baseline for learning the technologies discussed at the workshop"
- "This analysis studies decays of a Higgs boson into two tau leptons in the final state of a muon lepton and a hadronically decayed tau lepton"
---

## Why have we prepared this analysis?

We have prepared for you this example analysis as common baseline for learning the technolgoies discussed in this workshop. The goal is to have a working example that is simple yet complex enough to demonstrate common problems and their solutions in physics analysis.

## The analysis

This analysis uses data and simulation of events at the CMS experiment from 2012 with the goal to study decays of a Higgs boson into two tau leptons in the final state of a muon lepton and a hadronically decayed tau lepton. The analysis follows loosely the setup [of the official CMS analysis published in 2014](http://cms-results.web.cern.ch/cms-results/public-results/publications/HIG-13-004/index.html).

The purpose of the original CMS analysis was to establish the existence of the Higgs boson decaying into two tau leptons. Since performing this analysis properly with full consideration of all systematic uncertainties is an enormously complex task, we reduce this analysis to the qualitative study of the kinematics and properties of such events without a statistical analysis. However, as you can explore in this record, already such a reduced analysis is complex and requires extensive physics knowledge, which makes this a perfect first look into the procedures required to claim the evidence or existence of a new particle.

Two example results produced by this analysis can be seen below. The plots show the data recorded by the detector compared to the estimation of the contributing processes, which are explained in the following. The analysis has implemented the visualization of 34 such observables.

<div class="row">
  <div class="col-md-6">

    <img src="https://raw.githubusercontent.com/cms-opendata-analyses/HiggsTauTauNanoAODOutreachAnalysis/2012/plots/m_vis.png">

  </div>
  <div class="col-md-6">

    <img src="https://raw.githubusercontent.com/cms-opendata-analyses/HiggsTauTauNanoAODOutreachAnalysis/2012/plots/eta_2.png">

  </div>
</div>

## Analysis steps

The analysis steps follow the typical workflow of such an analysis at CMS. An overview of these steps is given in the following and the full details can be found in the analysis code and the description of the single sections of the lesson. The detailed technical description how to run the analysis is put separately in the respective section of the lesson.

1. First, the NanoAOD files containing data and simulated events are pre-processed. This step is here called skimming since the event selection reduces the size of the datasets significantly. In addition, we perform a pair selection to find from the muon and tau collections the pair which originates most likely from a Higgs boson.
2. The first step produces skimmed datasets from the original files but still preserves information of selected quantities for each event. In this step, we compute histograms of these quantities for all skimmed datasets. Because of the data-driven QCD estimation, similar histograms have to be produced with the selection containing same-charged tau lepton pairs. This sums up to multiple hundreds of histograms which have to be combined to the final plots such as the ones shown above.
3. Finally, the histograms are combined to the final plots showing the data taken with the CMS detector compared to the expectation from the background estimations. These plots allow to study the contribution of the different physics processes to the data taken with the CMS detector and represent the first step to answer the question whether we can verify the existence of the Higgs boson.
4. To perform a measurement, we have to fit the expected contributions of physics processes to the data of the experiment. This step follows a similar procedure than measuring the signal strength to claim the existence of the Higgs boson.

## Disclaimer: How to interpret the results

Please note that a proper analysis of data always requires a thorough study of all uncertainties. Since this analysis does not include any systematic uncertainties, the resulting plots should be interpreted only qualitatively. For a valid physics measurement, the differences between the data and the sum of all processes would have to be explained within the uncertainties. Also note that the counts for the simulated Higgs boson events are scaled up to make the expected signal contribution visible by eye.

## Reminder: Have you set up your environment?

Please go [here](../setup.html), select one of the options to set up your environment with the required software and download the required files.

{% include links.md %}

