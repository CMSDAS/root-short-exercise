---
title: "NanoAOD analysis: Skim the initial datasets"
teaching: 5
exercises: 10
questions:
- "How can I process large amounts of data efficiently?"
- "How does an analysis with RDataFrame look like in C++?"
objectives:
- "Perform this step of the analysis by yourself"
keypoints:
- "We reduced the initial datasets by filtering suitable events and selecting interesting observables."
- "This step includes finding the interesting muon-tau pair in each selected event."
- "To perform this computationally expensive part of the analysis as efficiently as possible, we enable ROOT's implicit multi-threading and use RDataFrame in C++!"
- "`ROOT::RVec` is an extended `std::vector`, which provides features to deal easily with collections similar to NumPy arrays in Python."
---

In this step, the NanoAOD files containing data and simulated events are pre-processed. This step is called skimming since the event selection reduces the size of the datasets significantly. In addition, we perform a pair selection to find from the muon and tau collections the pair which is most likely to have originated from a Higgs boson.

This step is implemented in the file `skim.cxx` [here](../code/skim.cxx) and is written in C++ for performance reasons.

> ## Download the code and investigate the content!
> Download the file [`skim.cxx`](../code/skim.cxx) and investigate the content. You can easily follow the steps in the `main` function!
{: .challenge}

> ## Compile the C++ program!
> Compile the file [`skim.cxx`](../code/skim.cxx) to an executable!
>
> Note that you require ROOT built with C++14 or later. You can find out by looking at the output of `root-config --cflags`, which must contain `-std=c++14` or `-std=c++17`!
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

## Have you noticed the `ROOT::RVec` class?

`ROOT::RVec` is an extended `std::vector` with additional features  to deal with collections, similar to NumPy arrays. Because `RVec` has the same interface than a `std::vector` you can use them interchangeably! However, following additional features simplifies typical tasks in analysis. You can find the full documentation [here](https://root.cern/doc/master/classROOT_1_1VecOps_1_1RVec.html)!

Note that all vectors in `RDataFrame` are automatically treated as `RVec`s. You can use all features shown below in strings passed to `RDataFrame`!

### Adopting memory

You can adopt memory just by passing the pointer and the length of the vector! This may improve the runtime of you program greatly because copies are costly operations.

```cpp
int d[3] = { 1, 2, 3 };
ROOT::RVec<int> v(d, 3); // { 1, 2, 3 }
```

### Arithmetic operations and masking

You can use arithmetic operations and masking with `RVec`s, just like with NumPy arrays!

```cpp
# Arithmetic operations
ROOT::RVec<int> x = { 1, 2, 3 };
auto y = pow(x, 2); // { 1, 4, 9 }
auto z = x + y; // { 2, 6, 12 }
```

```cpp
# Masking
ROOT::RVec<int> x = { 0, 1, 2 };
ROOT::RVec<int> y = { 1, 2, 3 };
auto z = y[x > 0]; // { 2, 3 }
```

### NumPy-like helper functions

```cpp
# Sorting, index manipulation, comparison, ...
using namespace ROOT::VecOps;
RVec<int> x = { 3, 1, 2 };
auto y = Reverse(Sort(x)); // { 3, 2, 1 }
auto idx = Argsort(x); // { 1, 2, 0 } (the indices sorting the vector x)
auto z = Take(x, idx); // { 1, 2, 3 } (the sorted vector)
auto allEqual = All(Reverse(z) == y); // true (compares all elements)
```

`ROOT::VecOps` also offers helpers typical to HEP such as `DeltaPhi` and `InvariantMass`. You can find working code examples explaining these helpers in the [VecOps tutorials](https://root.cern/doc/master/group__tutorial__vecops.html)!

> ## Try it by yourself!
> Feel free to open the ROOT prompt and try `ROOT::RVec` by yourself! The prompt is well suited to try some of the features shown above because you can print the content of the vectors just by leaving out the semicolon at the end of the line.
{: .challenge}

{% include links.md %}
