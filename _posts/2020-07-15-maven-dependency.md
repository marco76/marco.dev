---
title: 'Maven: find a package'
description: 'Search a dependency loaded with maven'
date: 2020-07-15T01:41:48+00:00
created: 2020-07-15T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'java'
color: '#7AAB13'
permalink: /java-maven-search
categories:
  - Java
  - Maven
tags:
  - Java
  - Maven

introduction: 'Search a dependency in a maven tree'
---

## Did you get a warning with maven, your pom.xml has problems, what to do?

When you build your maven project you could have an error or a warning like:

`[WARNING] The POM for com.sun.xml.bind:jaxb-osgi:2.2.10 is invalid, transitive dependencies (if any) will not be available, enable debug logging for more details`

How to find the dependency that include jaxb-osgi?

You can ask maven to show the chain of dependencies until this package:

`mvn dependency:tree -Dincludes=com.sun.xml.bind:jaxb-osgi:jar`

You will have a result similar to this one:
```console
[INFO]
[INFO] --- maven-dependency-plugin:3.0.2:tree (default-cli) @ your-project-name ---
[INFO] your-project:SNAPSHOT
[INFO] \- io.rest-assured:rest-assured:jar:3.0.0:test
[INFO]    \- io.rest-assured:xml-path:jar:3.3.0:test
[INFO]       \- com.sun.xml.bind:jaxb-osgi:jar:2.2.10:test
[INFO] ------------------------------------------------------------------------
[INFO] Reactor Summary for your-project-name-SNAPSHOT:
```




