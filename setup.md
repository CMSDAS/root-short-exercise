---
title: Setup
---

## Download the files

First, download the required files using the following link and unpack the archive:

[https://github.com/awesome-workshop/payload/archive/master.zip](https://github.com/awesome-workshop/payload/archive/master.zip)

For download to LXPLUS, you can use the following command:

~~~
curl -OL https://github.com/awesome-workshop/payload/archive/master.zip
~~~
{: .language-shell}

Next, please select one of the following solutions to get the required software.

## Set up the software

The analysis needs ROOT above release 6.16, a recent C++ compiler supporting at least C++14 and Python. To set up the software, choose one of the following options.

### Docker

On a machine running docker (see docker setup instructions for [MacOS](https://docs.docker.com/docker-for-mac/install/), [CentOS](https://docs.docker.com/install/linux/docker-ce/centos/) and [Ubuntu](https://docs.docker.com/install/linux/docker-ce/ubuntu/)), cd into the top level of your analysis repo:

```bash
cd /path/to/analysis/repo
```

start up a container from the `rootproject/root-conda` docker image as follows:

```bash
docker run -it --rm -v $PWD:/analysis -w /analysis rootproject/root-conda /bin/bash
# If you run into a premission error, use "sudo docker run ..." as a quick fix.
# To fix this for the future, see https://docs.docker.com/install/linux/linux-postinstall/
```

Thanks the volume mount set up with the `-v` command, any output saved under your working directory (`/analysis`) will automatically appear on your local machine in the location from which you started the container.

When you're finished working in the container type `exit` to get out of it. 

**Note:** The `--rm` option causes the container to be deleted once you're finished working with it. If you want the container to persist on your machine after you exit, remove the `--rm` option from the startup command.

### conda

If you are running on a Linux distribution or MacOS, you can use the conda package manager to install ROOT in under five minutes. Follow the steps shown in the first slides in [this presentation](https://indico.cern.ch/event/759388/contributions/3306849/attachments/1816254/2968550/root_conda_forge.pdf) to set up your system.

### lxplus/CVMFS

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

### SWAN

You can run the analysis in the browser using the [SWAN service at CERN](http://swan.web.cern.ch/). Go to [swan.cern.ch](https://swan.cern.ch) and select the software stack 96 to start your session. Please note that you have to visit CERNBox once before you can use SWAN (go once to [cernbox.cern.ch](https://cernbox.cern.ch)).



Download the files, upload them and in the top menu you can open a terminal. To view any output, either you can download the result again or view them directly in the browser.

{% include links.md %}
