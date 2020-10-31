---
published: true
title: 'Java test preview features'
description: 'How to test preview features'
date: 2020-10-27T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'java'
color: '#7AAB13'
permalink: /java-test-preview-features
categories:
  - Java
tags:
  - Java

introduction: 'Java test preview features'
---
To know what's included in this the latest Java release: [http://java-version.com/java](http://java-version.com/java)

## In 2 minutes
Every new Java release contains few new features in _preview_. This allows the community to test / review / comment them.

These features are not 'production ready' and they could disappear or change in the following releases.

Here you can find a nice explanation from Oracle: [The role of preview features in Java 14, Java 15, Java 16, and beyond](https://blogs.oracle.com/javamagazine/the-role-of-previews-in-java-14-java-15-java-16-and-beyond)

## How to use the preview features

### JShell
JShell should contain all the new preview features without lag.

To test them you can simply add `--enable-preview` to the `jshell` command.

Here a quick tutorial:

<iframe width="560" height="315" src="https://www.youtube.com/embed/dfBRP6YWXyc" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>

### Command line
To run code that includes preview features you should compile your source using the flags `javac --enable-preview --release [release nr.] [source].java`
 and execute it using `java --enable-preview [mainclass]`.

### IntelliJ

In IntelliJ you can configure the JDK used for the project:

_Project Structure ..._

Be sure that _Project language level_ is set on _[version] (Preview)_
<img src="/assets/img/uploads/2020/intellij-preview.gif" alt=""/>

You cannot use the preview features in the _JShell Console ..._ included in IntelliJ. This console is very limited.

