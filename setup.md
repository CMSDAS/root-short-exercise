---
title: Setup
---

First, download the required files using the following link and unpack the archive:

[https://github.com/stwunsch/awesome-workshop-analysis/archive/master.zip FIXME: Update this link!](https://github.com/stwunsch/awesome-workshop-analysis/archive/master.zip)

Next, please select one of the following solutions to get the required software:

1. TODO: Docker?
2. TODO: conda
3. lxplus/CVMFS

You can use the [CERN lxplus service](http://information-technology.web.cern.ch/services/lxplus-service) to log into a machine at CERN with [CVMFS](https://cernvm.cern.ch/portal/filesystem). Alternatively, you can use any system with a CVMFS installation. Use the following command to connect to lxplus [with X forwarding](https://unix.stackexchange.com/questions/12755/how-to-forward-x-over-ssh-to-run-graphics-applications-remotely).

```bash
ssh -Y your_username@lxplus.cern.ch
```

When logged in, just source the software stack with the following command.

```bash
source /cvmfs/sft.cern.ch/lcg/views/LCG_95/x86_64-centos7-gcc8-opt/setup.sh
```

Note that you may have to replace `x86_64-centos7-gcc8-opt` with a platform matching your system.

Now, you should have all required software available. You can check with `which root`, e.g., which ROOT executable you have sourced.

4. TODO: SWAN?

{% include links.md %}
