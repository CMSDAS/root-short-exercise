---
title: "Efficient analysis with RDataFrame"
teaching: 10
exercises: 0
questions:
- "How can I perform efficient analysis with ROOT?"
objectives:
- "Understand the concept of declarative programming"
- "Learn about the basics of `RDataFrame`"
- "Find out how to run your analysis on multiple threads"
keypoints:
- "`RDataFrame` is the recommended entry point for efficient analysis"
- "`RDataFrame` follows a declarative workflow: Declare first what you want to do and let ROOT run all of your tasks as efficiently as possible in one go, in parallel!"
- "Parallelization on multiple threads requires only the `ROOT.EnableImplicitMT()` statement"
---

> ## Introduction to RDataFrame
> In this section, you will learn about the recommended tool to perform efficient analysis with ROOT called `RDataFrame`! `RDataFrame` enables you to run all your tasks efficiently in one go and on multiple threads.
{: .testimonial}

```python
import ROOT

# Enable multi-threading
ROOT.EnableImplicitMT(2)
```

```python
# Create dataframe from a (reduced) NanoAOD file
df = ROOT.RDataFrame("Events", "Run2012BC_DoubleMuParked_Muons.root")

# For simplicity, select only events with exactly two muons and require opposite charge
df_2mu = df.Filter("nMuon == 2", "Events with exactly two muons")
df_os = df_2mu.Filter("Muon_charge[0] != Muon_charge[1]", "Muons with opposite charge")
```

```python
# Compute invariant mass of the dimuon system

# Perform the computation of the invariant mass in C++
ROOT.gInterpreter.Declare('''
using Vec_t = const ROOT::RVec<float>&;
float ComputeInvariantMass(Vec_t pt, Vec_t eta, Vec_t phi, Vec_t mass) {
    const ROOT::Math::PtEtaPhiMVector p1(pt[0], eta[0], phi[0], mass[0]);
    const ROOT::Math::PtEtaPhiMVector p2(pt[1], eta[1], phi[1], mass[1]);
    return (p1 + p2).M();
}
''')

# Add the result of the computation to the dataframe
df_mass = df_os.Define("Dimuon_mass", "ComputeInvariantMass(Muon_pt, Muon_eta, Muon_phi, Muon_mass)")

# Make histogram of the dimuon mass spectrum
h = df_mass.Histo1D(("Dimuon_mass", ";m_{#mu#mu} (GeV);N_{Events}", 30000, 0.25, 300), "Dimuon_mass")
```

```python
# Request a cut-flow report
report = df_mass.Report()
```

```python
# Produce plot
ROOT.gStyle.SetOptStat(0)
ROOT.gStyle.SetTextFont(42)
c = ROOT.TCanvas("c", "", 800, 700)
h.GetXaxis().SetTitleSize(0.04); h.GetYaxis().SetTitleSize(0.04)
c.SetLogx(); c.SetLogy()
h.Draw()

label = ROOT.TLatex()
label.SetNDC(True)
label.SetTextSize(0.040)
label.DrawLatex(0.100, 0.920, "#bf{CMS Open Data}")
label.DrawLatex(0.550, 0.920, "#sqrt{s} = 8 TeV, L_{int} = 11.6 fb^{-1}")

# Save as png file
c.SaveAs("dimuon_spectrum.png")

# Print cut-flow report
report.Print()
```

```
Events with exactly two muons: pass=31104343   all=61540413   -- eff=50.54 % cumulative eff=50.54 %
Muons with opposite charge: pass=24067843   all=31104343   -- eff=77.38 % cumulative eff=39.11 %
```

![](../fig/dimuon_spectrum.png)

> ## Try it by yourself!
> - Assemble the code pieces and compute a high-resolution dimuon spectrum in under one minute!
> - Does the computation time decrease with an increasing number of threads `N` in `ROOT.EnableImplicitMT(N)`?
> - Could you name the resonances?
{: .challenge}


{% include links.md %}

