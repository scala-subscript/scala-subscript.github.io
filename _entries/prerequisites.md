---
sectionid: prerequisites
sectionclass: h2
title: Prerequisites
parent-id: subscript
number: 1100
---
In order to get started using SubScript, one should have an [SBT](http://www.scala-sbt.org/) build tool installed (use the official [installation guide](http://www.scala-sbt.org/download.html)) and know the basics of working with the command line.

**Note for Mac OS users:** if you try to install SBT with [homebrew](http://brew.sh/), you may encounter the following error:
```
Cowardly refusing to `sudo brew install'
```
This is due to [this](https://github.com/Homebrew/homebrew/issues/9953) issue, you can solve this by running the following command:
```
sudo chown root /usr/bin/brew
``` 
