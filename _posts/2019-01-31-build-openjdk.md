---
title: 'Build the OpenJDK'
description: 'Tutorial'
date: 2019-01-31T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'java'
color: '#7AAB13'
permalink: /build-openjdk
categories:
  - Java
tags:
  - Java
 
image: '/assets/img/'

introduction: 'Build the OpenJDK, step by step'
---

## Build the OpenJDK from the sources

In this tutorial we build OpenJDK version 12 for MacOSX.

## Install Mercurial

[https://www.mercurial-scm.org/wiki/Download]()

Install brew : [https://brew.sh]()

```
brew install mercurial
```

You can test that everything is working with

```
hg --version
```

## Clone the repository

Example for Java 12:

```
hg clone https://hg.openjdk.java.net/jdk/jdk12
```

... it will take a while ...

Here you can find the list of the available repositories:

[https://hg.openjdk.java.net/jdk]()

When cloned, enter in the directory with the sources

```
cd jdk12
```

Verify that all the requirements are satisfied:

```
bash configure
```

Build the OpenJDK with
 
```
make images
```

At the end your image should be ready in the build folder, you can verify the version with:

```
./build/*/images/jdk/bin/java -version
```

e.g.

```
openjdk version "12-internal" 2019-03-19
OpenJDK Runtime Environment (build 12-internal+0-adhoc.marco.jdk12)
OpenJDK 64-Bit Server VM (build 12-internal+0-adhoc.marco.jdk12, mixed mode, sharing)
```

Enjoy it and contribute! ;-)

## Links

[Bug Dashboard](https://bugs.openjdk.java.net/secure/Dashboard.jspa)

[How to contribute](https://openjdk.java.net/contribute/)

[Build, detailed instructions](https://cr.openjdk.java.net/~ihse/demo-new-build-readme/common/doc/building.html#tldr-instructions-for-the-impatient)

[Unofficial GitHub Repo](Very useful to navigate the sources)

[JDK 12 Tags](https://hg.openjdk.java.net/jdk/jdk12/tags)

[JDK 12 Log](https://hg.openjdk.java.net/jdk/jdk12/shortlog/)

