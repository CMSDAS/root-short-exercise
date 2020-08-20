---
title: "NanoAOD analysis: Make the plots"
teaching: 5
exercises: 5
questions:
- "How can I make high quality plots with ROOT?"
objectives:
- "Make plots of all observables"
keypoints:
- "The plotting combines all histograms to produce estimates of the physical processes and create a figure with a physical meaning."
- "The plots show the share of the contributing physical processes to the data, but without systematic uncertainties."
- "The script shows how you can produce paper quality plots with ROOT!"
---

> Finally, the histograms are combined to produce the final plots showing the data taken with the CMS detector compared with the expectation from the background estimates. These plots allow one to study the contribution of the different physics processes to the data taken with the CMS detector and represent the first step towards verifying the existence of the Higgs boson.
{: .testimonial}

This step is again implemented for convenience in Python and can be found in the file `plot.py`, which you can download [here](../code/plot.py).

> ## Investigate and run the Python script!
> Have a look at [the code](../code/plot.py) and run it! Note again that the program picks up the files from the same directory in which you run it.
{: .challenge}

> ## Investigate the output!
> The Python script generates for each variable a `png` and `pdf` image file, which can be viewed with a program of your choice. Only two example outputs are shown below, the visible mass of the di-tau system and the pseudorapidity distribution of the tau, but you can investigate 34 of such plots after you have run the script!
{: .challenge}

<div class="row">
  <div class="col-md-6">

    <img src="../fig/m_vis.png" align="middle">

  </div>
  <div class="col-md-6">

    <img src="../fig/eta_2.png" align="middle">

  </div>
</div>

{% include links.md %}
