---
title: "Step 4: Make a measurement"
teaching: 5
exercises: 10
questions:
- "How can we make a measurement?"
objectives:
- "Perform a fit representing a measurement"
keypoints:
- "The measurement fits the signal strength (multiplier of the Standard Model expectation) of the Z to two tau lepton process."
---

This step performs a fit on the histograms of the visible mass plot to perform a measurement.

![](https://raw.githubusercontent.com/cms-opendata-analyses/HiggsTauTauNanoAODOutreachAnalysis/2012/plots/m_vis.png)

Because the contribution of the Higgs signal is too tiny with the inclusive selection, we fit the "signal" strength of the Z→ττ process. You can find the implementation of the fitting in the Python script `fit.py`. Use the following command to run the fit.

```bash
bash fit.sh /path/to/histograms.root /dir/output/dir/with/plot
```

The resulting plot shows the scan of the profile likelihood from which we can extract the best fit value of the signal strength modifier for the Z→ττ process and the uncertainty on this parameter.

{% include links.md %}
