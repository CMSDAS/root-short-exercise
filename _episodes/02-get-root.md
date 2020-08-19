---
title: "Get ROOT"
teaching: 10
exercises: 5
questions:
- "How to install ROOT on my system or get access to systems with ROOT?"
objectives:
- "Find for you the most efficient way to get access to ROOT"
- "Install ROOT or connect to a machine with ROOT already made available"
keypoints:
- "ROOT is accessible via many sources"
- "Detailed instructions being up-to-date can be found on [https://root.cern/install](https://root.cern/install)"
---

> This section shows you multiple ways to get ROOT. Find below solutions to run ROOT locally, on LXPLUS, in batch systems and CIs!
{: .testimonial}

## Conda

[Conda](https://docs.conda.io/en/latest/) is a package management system and environment management system, which can install ROOT in a few minutes on Linux and MacOS.

The fastes way to get ROOT is [installing Miniconda](https://docs.conda.io/en/latest/miniconda.html) (a minimal Conda installer) and then run the following two commands:

```bash
conda create -c conda-forge --name <my-environment> root
conda activate <my-environment>
```

You can find detailed information about ROOT on Conda in [this blog post](https://iscinumpy.gitlab.io/post/root-conda/).

## CVMFS

[CVMFS](https://cernvm.cern.ch/portal/filesystem) is a software distribution service and in HEP on many systems already set up. CMSSW including ROOT is distributed via CVMFS, but also other software stacks are available that contain ROOT.

Most notably, the CERN service [LXPLUS](http://information-technology.web.cern.ch/services/lxplus-service) has CVMFS always installed and enables rapid access to software and computing resources.

### CMSSW

Following commands let you find out quickly which ROOT version comes with CMSSW.

```bash
# Source setup tools
source /cvmfs/cms.cern.ch/cmsset_default.sh

# Show CMSSW versions
scram list

# Setup CMSSW environment (using CMSSW_10_6_15 here)
cmsrel CMSSW_10_6_15
cd CMSSW_10_6_15/

# Show information about ROOT
scram tool list | grep root
```

### LCG

Another possibility to get ROOT via CVMFS are the LCG stacks. All information about the releases and containing packages can be found on [http://lcginfo.cern.ch/](http://lcginfo.cern.ch/). Most releases are available as a Python 2 and Python 3 version, for example [`98`](http://lcginfo.cern.ch/release/98/) and [`98python3`](http://lcginfo.cern.ch/release/98python3/). There are also development releases every night, which contain the latest ROOT release in [`dev4`](http://lcginfo.cern.ch/release/dev3/) and the very latest developments from ROOT master in [`dev3`](http://lcginfo.cern.ch/release/dev3/).

The following example shows you how to source LCG 98 based on Python 3 on a CentOS 7 machine such as LXPLUS. Note the platform and compiler dependent information in the path, which have to be adjusted based on your system. The available combinations are shown on the website.

```bash
source /cvmfs/sft.cern.ch/lcg/views/LCG_98python3/x86_64-centos7-gcc10-opt/setup.sh
```

## Docker

If you want to use ROOT in a CI, most likely the software will be made available via Docker. The official ROOT docker contain can be found on [https://hub.docker.com/r/rootproject/root](https://hub.docker.com/r/rootproject/root). The different base images and ROOT versions are encoded in the tags, for example `6.22.00-fedora32`, and `latest` will get you the latest ROOT release based on Ubuntu 20.04. If you want to try it, [get Docker](https://docs.docker.com/get-docker/) and run the following command to start the container with a bash shell.

```bash
run --rm -it rootproject/root /bin/bash
```

## Binary releases and packages

The classic way to distribute software, besides the source code, are plain binary releases. You can download these from the release pages on [https://root.cern/install/all_releases/](https://root.cern/install/all_releases/) for all major MacOS and Linux versions.

In addition, the ROOT community maintains for some Linux distributions, e.g., Arch Linux, packages in the respective package managers. You can find a list of maintained packages on [https://root.cern/install/#linux-package-managers](https://root.cern/install/#linux-package-managers).

## Verify the ROOT version

Since ROOT has a long history and numerous releases, you may find on old systems such Scientific Linux 6 also old ROOT versions. However, you can easily verify with following commands the version of ROOT and also find expert details about the ROOT configuration!

```bash
# ROOT version and build tag
root --version

# Again the ROOT version
root-config --version

# Expert details about the ROOT configuration
root-config --help
```

> ## Find your way to access ROOT!
> For the exercises later you need at least ROOT 6.18. Feel free to set up for yourself your preferred environment satisfying this requirement!
{: .challenge}


> ## Fallback solution
> As a fallback solution you can always connect via `ssh -Y your_username@lxplus.cern.ch` to LXPLUS. The `-Y` flag enables X forwarding, which allows you to forward the output of graphics application in case you run a system with an X server such as almost all Linux distributions.
{: .solution}

{% include links.md %}
