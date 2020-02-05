---
title: "Step 2: Produce histograms"
teaching: 5
exercises: 10
questions:
- "Which histograms do we need?"
objectives:
- "Produce all the histograms for the plots"
- "Understand why we need so many histograms for a single plot"
keypoints:
- "We produce histograms of all physics processes and all observables."
- "All histograms are produced in a signal region with opposite-signed muon-tau pairs and in a control region with same-signed pairs for the data-driven QCD estimate"
---

The first step produces skimmed datasets from the original files but still preserves information of selected quantities for each event. In this step, we compute histograms of these quantities for all skimmed datasets. Because of the data-driven QCD estimation, similar histograms have to be produced with the selection containing same-charged tau lepton pairs. This sums up to multiple hundreds of histograms which have to be combined to the final plots such as the ones shown above.

This step is implemented in Python in the file `histograms.py`. Run the following script to process the previously produced reduced datasets.

```bash
bash histograms.sh /input/dir/with/skims /output/dir/with/histograms
```

The script produces the file `histograms.root`, which contains the histograms. You can have a look at the plain histograms using the ROOT browser, which is started up with the command `rootbrowse histograms.root`.

{% include links.md %}
