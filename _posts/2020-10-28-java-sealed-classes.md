---
published: true
title: 'Java sealed classes - Quick intro'
description: 'Java 15 new features. Java sealed classes tutorial'
date: 2020-10-28T01:41:48+00:00
author: Marco Molteni
layout: post
main-class: 'java'
color: '#7AAB13'
permalink: /java-sealed-classes
categories:
  - Java
tags:
  - Java

introduction: 'Sealed classes - Java 15 new feature'
---

Java 15 introduce the _sealed classes_ as Preview feature.
_Preview_ means that the feature is still in evaluation and development and is not ready for production.

Sealed classes allow you to limit the extensibility of one class to a predefined set of subclasses.

Before the _sealed classes_ it was possible to limit the extensibility of a class to the package level, this had the drawback of limiting the accessibility and use of this class from outside the package.

### Why sealed classes?
According to the official [JEP 360](https://openjdk.java.net/jeps/360): 

> Sealed classes and interfaces restrict which other classes or interfaces may extend or implement them.

> ... it should be possible for a superclass to be widely accessible (since it represents an important abstraction for users) but not widely extensible (since its subclasses should be restricted to those known to the author).

The documentation of Oracle is pretty good, you can find it here:
[Java SE Language Updates - Sealed classes](https://docs.oracle.com/en/java/javase/15/language/sealed-classes-and-interfaces.html)

For a deep dive you can read this document of Brian Goetz:
[Data Classes and Sealed Types for Java](https://cr.openjdk.java.net/~briangoetz/amber/datum.html)

Because of the extensive documentation we will limit this post to a basic example that can give an idea of the new feature.

## Example

```java
sealed class Person permits Man, Woman, Child {
    public String name;
}
non-sealed class Man extends Person {}
final class Woman extends Person {};
sealed class Child extends Person permits Boy, Girl {}
final class Boy extends Child {}
final class Girl extends Child {}
class Superman extends Man {};
// final class Sun extends Person {}; // =>  Alient is not allowed in the sealed hierarchy;
```

This code is can be represented by the following schema:

<img src="/assets/img/uploads/2020/sealed-classes.gif" alt=""/>

The `sealed class Person` can define which other classes are authorized to extend it.
`Person permits Man, Woman, Child` means that the class Person can be extended only by the classes `Man`, `Woman` and `Child`.

The extended classes need to have one of the following modifiers: 

<span style='color: blue'>_sealed_</span> :  the class can be extended by the defined classes using `permits`

<span style='color: green'>_non-sealed_ </span>: any class can extend this class

<span style='color: red'>_final_ </span>: the class cannot be extended
