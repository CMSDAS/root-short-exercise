---
title: "Final preparations"
teaching: 5
exercises: 10
questions:
- "What do I have to prepare for the workshop?"
objectives:
- "Run the analysis once by yourself"
- "Make two git repositories on CERN GitLab"
- "Add files to the repositories"
keypoints:
- "Run the analysis by yourself to understand the different steps."
- "Set up `git` and visit CERN GitLab."
- "Make two git repositories and add files to them."
---

### Final preparations

We assume that you have run the analysis once by yourself and you are familiar with the different analysis steps. Follow the instructions below as final preparations for a successful workshop.

### Visit CERN GitLab and initialize the repositories

First, go to [gitlab.cern.ch](https://gitlab.cern.ch) and create two new repositories using the `New project` button. The names of the repositories should be:

 - `awesome-analysis-eventselection`
 - `awesome-analysis-statistics`

### Check out the repositories

Next, check out the repositories. You can do this with the following command.

```bash
git clone https://gitlab.cern.ch/<your username>/<repository name>
```

### Add files to the repositories

Now add the files of the analysis you got from the zip archive to the repositories following the structure below. Don't add the outputs of the analysis such as the plots and the ROOT files!

 - `awesome-analysis-eventselection`: Files for step 1 to 3 (skimming, histograms and plots)
 - `awesome-analysis-statistics`: Files for step 4 (fitting)

 If you have never used `git` before, remember to set your name and email address.

 ```bash
git config --global user.name "<your name>"
git config --global user.email "<your email>"
```


Then, add the files with a meaningful commit message using the commands below.

 ```bash
 git add <files>
 git commit -m <commit message>
 ```

{% include links.md %}
