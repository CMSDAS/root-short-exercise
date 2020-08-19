---
title: Setup
---

> ## What do I need to participate in this lesson?
> You need very little to participate in this lesson! At a bare minimum, you require a working internet connection, a CERN account, an SSH connection to `lxplus.cern.ch` and about 2 hours of time.
>
> But if you feel confident enough, you can also run the lesson on your own system! You will find further information in the section about installing ROOT.
>
> Some reminders follow about `ssh`, X forwarding and `scp`. Also note that we always assume that you use the `bash` shell!
{: .keypoints}

### Connect to LXPLUS with X forwarding

Probably you want to see the output of graphical applications that run on LXPLUS. To do so, pass the `-Y` flag to `ssh`. However, you need a rather fast internet connection to make this work smoothly. Of course, you have to be on a machine with a running X server!

```bash
ssh -Y your_username@lxplus.cern.ch
```

### Copy files with scp

With a slow internet connection it may be better to just copy a file to your local machine and inspect it there, which can be done easily with `scp`.

```bash
scp your_username@lxplus.cern.ch:/path/to/file/on/lxplus /path/to/file/on/your/machine
```

{% include links.md %}
