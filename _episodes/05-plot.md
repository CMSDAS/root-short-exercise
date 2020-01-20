---
title: "Step 3: Make the plots"
teaching: 5
exercises: 10
questions:
- "How do we combine the histograms?"
objectives:
- "Make plots of all observables"
keypoints:
- "The plotting combines all histograms to the estimations of the physical processes to create a figure with a physical meaning."
- "The plots show the share of the contributing physical processes to the data."
- "We do not include any systematic uncertainties in this example."
---

Finally, the histograms are combined to the final plots showing the data taken with the CMS detector compared to the expectation from the background estimations. These plots allow to study the contribution of the different physics processes to the data taken with the CMS detector and represent the first step to answer the question whether we can verify the existence of the Higgs boson.

To combine the histograms produced in the previous step to meaningful plots, run the following command.

```bash
bash plot.sh /path/to/histograms.root /output/dir/with/plots
```

The Python script generates for each variable a `png` and `pdf` image file, which can be viewed with a program of your choice.

{% include links.md %}
